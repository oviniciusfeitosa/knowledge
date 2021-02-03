# Cache

## [Memcached vs Opcache](https://stackoverflow.com/a/24923592)

> **OPcache** is for accelerating code access. 
>
> **Memcached** is for accelerating data access. 
>
> They are **completely different**, and **completely independent**.

## [Maximizing PHP 7 Performance with NGINX, Part 1: Web Serving and Caching](https://www.nginx.com/blog/maximizing-php-7-performance-with-nginx-part-i-web-serving-and-caching/)

## Database-level Caching

* Memcached

## [Enabling FastCGI Cache in NGINX](https://www.tecmint.com/cache-content-with-nginx/)

**FastCGI** \(or **FCGI**\) is a widely-used protocol for interfacing interactive applications such as **PHP** with web servers such as **NGINX**. It is an extension of the **CGI** \(**Common Gateway Interface**\).

The main advantage of **FCGI** is that it manages multiple CGI requests in a single process. Without it, the webserver has to open a new process \(that has to be controlled, process a request, and get closed\) for every client request for a service.

To process **PHP** scripts in a [LEMP stack deployment](https://www.tecmint.com/install-lemp-on-centos-8/), **NGINX** uses **FPM** \(**FastCGI Process Manager**\) or **PHP-FPM**, a popular alternative PHP FastCGI implementation. Once the **PHP-FPM** process is running, **NGINX** is configured to proxy requests to it for processing. Thus NGINX can also be configured to cache responses from the **PHP-FPM** backend application server.

Under **NGINX**, the **FastCGI** content cache is declared using a directive called `fastcgi_cache_path` in the top-level `http{}` context, within the NGINX configuration structure. You can also add the `fastcgi_cache_key` which defines a key \(request identifier\) for caching.

Besides, to read the upstream cache status, add the **add\_header X-Cache-Status** directive within the `http{}` context – this is useful for debugging purposes.

Assuming your site’s server block configuration file is located at **/etc/nginx/conf.d/testapp.conf** or **/etc/nginx/sites-available/testapp.conf** \(under Ubuntu and its derivatives\), open the file of editing and add the following lines at the top of the file.

```text
fastcgi_cache_path /var/cache/nginx levels=1:2 keys_zone=CACHEZONE:10m; inactive=60m max_size=40m;
fastcgi_cache_key "$scheme$request_method$host$request_uri";
add_header X-Cache $upstream_cache_status;
```

[![Enable FastCGI Cache in NGINX](https://www.tecmint.com/wp-content/uploads/2020/06/add-fastcgi-cache-path-and-key.png)](https://www.tecmint.com/wp-content/uploads/2020/06/add-fastcgi-cache-path-and-key.png)Enable FastCGI Cache in NGINX

The `fastcgi_cache_path` directive specifies the number of parameters which are:

* **/var/cache/nginx** – the path to the local disk directory for the cache.
* **levels** – defines the hierarchy levels of a cache, it sets up a two-level directory hierarchy under **/var/cache/nginx**.
* **keys\_zone \(name:size\)** – enables the creation of a shared memory zone where all active keys and information about data \(meta\) are stored. Note that storing the keys in memory speeds up the checking process, by making it easier for NGINX to determine whether its a **MISS** or **HIT**, without checking the status on disk.
* **inactive** – specifies the amount of time after which cached data that are not accessed during the time specified get deleted from the cache regardless of their freshness. A value of **60m** in our example configuration means files not accessed after 60 will get removed from the cache.
* **max\_size** – specifies the maximum size of the cache. There are more parameters you can use here \(read the NGINX documentation for more information\).

The variables in the `fastcgi_cache_key` directive is described below.

NGINX uses them in calculating the key \(identifier\) of a request. Importantly, to send a cached response to the client, the request must have the same key as a cached response.

* **$scheme** – request scheme, HTTP or HTTPS.
* **$request\_method** – request method, usually “**GET**” or “**POST**”.
* **$host** – this can be hostname from the request line, or hostname from the “**Host**” request header field, or the server name matching a request, in the order of precedence.
* **$request\_uri** – means the full original request URI \(with arguments\).

Also, the `$upstream_cache_status` variable in the **add\_header X-Cache-Status** directive is calculated for each request that NGINX responds to, whether it is a **MISS** \(response not found in the cache, got from application server\) or a **HIT** \(response served from cache\) or any of the other supported values.

Next, within the `location` directive which passes PHP requests to **PHP-FPM**, uses the `fastcgi_cache` directives to activate the cache you have just defined above.

Also set caching time for different responses using the `fastcgi_cache_valid` directive as shown.

```text
fastcgi_cache CACHEZONE;
fastcgi_cache_valid  60m;
```

[![Define Caching Zone and Time](https://www.tecmint.com/wp-content/uploads/2020/06/define-caching-zone-to-use-when-processing-php-requests.png)](https://www.tecmint.com/wp-content/uploads/2020/06/define-caching-zone-to-use-when-processing-php-requests.png)Define Caching Zone and Time

If only caching time is specified as in our case, only **200**, **301**, and **302** responses are cached. But you can also specify the responses explicitly or use any \(for any response code\):

```text
fastcgi_cache CACHEZONE;
fastcgi_cache_valid 200  301 203 60m;
fastcgi_cache_valid 404 10m;
OR
fastcgi_cache CACHEZONE;
fastcgi_cache_valid  any 10m;
```

### Fine-Tuning FastCGI Caching Performance on Nginx

To set the minimum number of times a request with the same key must be made before the response is cached, include the `fastcgi_cache_min_uses` directive, either in the `http{}` or `server{}` or `location{}` context.

```text
fastcgi_cache_min_uses  3
```

[![Set Minimum Cache Usage](https://www.tecmint.com/wp-content/uploads/2020/06/set-minimum-number-of-uses-before-caching-a-response.png)](https://www.tecmint.com/wp-content/uploads/2020/06/set-minimum-number-of-uses-before-caching-a-response.png)Set Minimum Cache Usage

To enable re-validation of expired cache items using conditional requests with the “**If-Modified-Since**” and “**If-None-Match**” header fields, add the `fastcgi_cache_revalidate` directive, within the `http{}` or `server{}` or `location{}` context.

```text
fastcgi_cache_revalidate on;
```

[![Set Cache Re-validation](https://www.tecmint.com/wp-content/uploads/2020/06/set-revalidation-of-expired-cache-using-conditional-requests.png)](https://www.tecmint.com/wp-content/uploads/2020/06/set-revalidation-of-expired-cache-using-conditional-requests.png)Set Cache Re-validation

You can also instruct **NGINX** to deliver cached content when the origin server or FCGI server is down, using the `proxy_cache_use_stale` directive, within the location directive.

This sample configuration means that when **NGINX** receives an error, timeout, and any of the specified errors from the upstream server and has a stale version of the requested file in the cached content, it delivers the stale file.

```text
proxy_cache_use_stale error timeout http_500;
```

[![Enable Serving of Stale Data](https://www.tecmint.com/wp-content/uploads/2020/06/enable-serving-of-stale-data.png)](https://www.tecmint.com/wp-content/uploads/2020/06/enable-serving-of-stale-data.png)Enable Serving of Stale Data

Another useful directive to fine-tune FCGI caching performance is `fastcgi_cache_background_update` which works in conjunction with the `proxy_cache_use_stale` directive. When set to on, it instructs NGINX to serve stale content when clients request for a file that is expired or is in the process of being updated from the upstream server.

```text
fastcgi_cache_background_update on;
```

[![Enable Cache Background Update](https://www.tecmint.com/wp-content/uploads/2020/06/enable-cache-background-update.png)](https://www.tecmint.com/wp-content/uploads/2020/06/enable-cache-background-update.png)Enable Cache Background Update

The `fastcgi_cache_lock` is useful too, for cache performance fine-tuning in that if multiple clients request for the same content that is not in the cache, NGINX will forward only the first request to the upstream server, cache the response then serve the other client requests from the cache.

```text
fastcgi_cache_lock on;
```

[![Enable Cache Lock](https://www.tecmint.com/wp-content/uploads/2020/06/enable-cache-lock.png)](https://www.tecmint.com/wp-content/uploads/2020/06/enable-cache-lock.png)Enable Cache Lock

After making all the above changes in the **NGINX** configuration file, save and close it. Then check the configuration structure for any syntax errors before restarting the NGINX service.

```text
# nginx -t
# systemctl restart nginx
```

[![Check and Start Nginx Service](https://www.tecmint.com/wp-content/uploads/2020/06/check-nginx-config-for-syntax-errors-and-restart-nginx-service.png)](https://www.tecmint.com/wp-content/uploads/2020/06/check-nginx-config-for-syntax-errors-and-restart-nginx-service.png)Check and Start Nginx Service

Next, test if the cache is functioning properly, try to access your web application or site from using the following [curl command](https://www.tecmint.com/linux-curl-command-examples/) \(the first time should indicate a **MISS**, but subsequent requests should indicate a **HIT** as shown in the screenshot\).

```text
# curl -I http://testapp.tecmint.com
```

[![Test FastCGI Cache](https://www.tecmint.com/wp-content/uploads/2020/06/test-if-fastcgi-cache-is-working.png)](https://www.tecmint.com/wp-content/uploads/2020/06/test-if-fastcgi-cache-is-working.png)Test FastCGI Cache

Here is another screenshot showing NGINX serving stale data.[![Test Nginx Serving Stale Data](https://www.tecmint.com/wp-content/uploads/2020/06/nginx-serving-stale-content-from-cache.png)](https://www.tecmint.com/wp-content/uploads/2020/06/nginx-serving-stale-content-from-cache.png)

### Adding Exceptions to Bypass Cache

It is possible to set conditions under which **NGINX** should not send cached responses to clients, using the `fastcgi_cache_bypass` directive. And to instruct NGINX not to cache responses from the upstream server at all, use the `fastcgi_no_cache`.

For example, if you want **POST** requests and URLs with a query string to always go to PHP. First, declare an if statement to set the condition as follows.

```text
set $skip_cache 0; 
if ($request_method = POST) { 
	set $skip_cache 1; 
} 
```

Then activate the above exception in the `location` directive which passes PHP requests to **PHP-FPM**, using the `fastcgi_cache_bypass` and `fastcgi_no_cache` directives.

```text
 
fastcgi_cache_bypass $skip_cache; 
fastcgi_no_cache $skip_cache;
```

There are many other parts of your site for which you may not want to enable content caching. The following is an example NGINX configuration for improving the performance of a WordPress site, provided on the **nginx.com** blog.

To use it, make changes \(such as the domain, paths, filenames, etc.\) to reflect what exists in your environment.

```text
fastcgi_cache_path /var/run/NGINX-cache levels=1:2 keys_zone=WORDPRESS:100m inactive=60m; 
fastcgi_cache_key "$scheme$request_method$host$request_uri"; 
server { 
	server_name example.com www.example.com; 
	root /var/www/example.com; 
	index index.php; 
	access_log /var/log/NGINX/example.com.access.log; 
	error_log /var/log/NGINX/example.com.error.log; 
	set $skip_cache 0; 
	# POST requests and URLs with a query string should always go to PHP 	
	if ($request_method = POST) { 
		set $skip_cache 1; 
	} 
	if ($query_string != "") {
		set $skip_cache 1; 
	} 
	# Don't cache URIs containing the following segments 
	if ($request_uri ~* "/wp-admin/|/xmlrpc.php|wp-.*.php|/feed/|index.php |sitemap(_index)?.xml") { 
		set $skip_cache 1; 
	} 
	# Don't use the cache for logged-in users or recent commenters 
	if ($http_cookie ~* "comment_author|wordpress_[a-f0-9]+|wp-postpass |wordpress_no_cache|wordpress_logged_in") {
		set $skip_cache 1; 
	} 
	location / { 
		try_files $uri $uri/ /index.php?$args; 
	} 
	location ~ .php$ { 
		try_files $uri /index.php; 
		include fastcgi_params; 
		fastcgi_pass unix:/var/run/php5-fpm.sock; 
		fastcgi_cache_bypass $skip_cache; 
		fastcgi_no_cache $skip_cache; 
		fastcgi_cache WORDPRESS; 
		fastcgi_cache_valid 60m; 
	} 
	location ~ /purge(/.*) {
		fastcgi_cache_purge WORDPRESS "$scheme$request_method$host$1"; 
	} 
	location ~* ^.+.(ogg|ogv|svg|svgz|eot|otf|woff|mp4|ttf|css|rss|atom|js|jpg|jpeg |gif|png|ico|zip|tgz|gz|rar|bz2|doc|xls|exe|ppt|tar|mid|midi |wav|bmp|rtf)$ { 
		access_log off; 
		log_not_found off; 
		expires max; 
	} 
	location = /robots.txt { 
		access_log off; 
		log_not_found off; 
	}
	location ~ /. { 
		deny all; 
		access_log off; 
		log_not_found off; 
	} 
}
```

### Enabling Proxy Cache in NGINX

**NGINX** also supports the caching of responses from other proxied servers \(defined by the `proxy_pass` directive\). For this test case, we are using [NGINX as a reverse proxy for a Node.js web application](https://www.tecmint.com/nginx-as-reverse-proxy-for-nodejs-app/), so we will enable NGINX as a cache for the Node.js application. All the configuration directives used here have similar meanings as the FastCGI directives in the previous section, so we will not explain them again.

To enable caching of responses from a proxied server, include the `proxy_cache_path` directive in the top-level `http{}` context. To specify how requests are cached, you can also add the `proxy_cache_key` directive as follows.

```text
proxy_cache_path /var/cache/nginx app1 keys_zone=PROXYCACHE:100m inactive=60m max_size=500m;
proxy_cache_key  "$scheme$request_method$host$request_uri";
add_header X-Cache-Status $upstream_cache_status;
proxy_cache_min_uses 3;
```

Next, activate the cache in the location directive.

```text
location / {
	proxy_pass http://127.0.0.1:3000;
	proxy_cache        PROXYCACHE;
	proxy_cache_valid 200 302 10m;
	proxy_cache_valid 404      1m;
}
```

To define conditions under which NGINX does not send cached content and does not cache a response at all from the upstream server, include the `proxy_cache_bypass` and `proxy_no_cache`.

```text
 
proxy_cache_bypass  $cookie_nocache $arg_nocache$arg_comment;
proxy_no_cache        $http_pragma $http_authorization;
```

### Fine-Tuning Proxy Cache Performance

The following directives are useful for fine-tuning the performance of the proxy cache. They also have the same meanings as the FastCGI directives.

```text
proxy_cache_min_uses 3;
proxy_cache_revalidate on;
proxy_cache_use_stale error timeout updating http_500;
proxy_cache_background_update on;
proxy_cache_lock on;
```

