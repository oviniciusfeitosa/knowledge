# Wordpress

## Docker

Using the repo [vinnyfs89/docker-wordpress](https://github.com/vinnyfs89/docker-wordpress) as reference. Execute the command below to get your wordpress application working.

```bash
docker-compose up
```

{% hint style="info" %}
The application will use 2 services to handle containers. The first to turn on database and second to application.
{% endhint %}

### WordPress: Too Many Redirects Issue when NGINX reverse proxy to Apache

Add this in your _wp-config.php:_

```bash
$_SERVER['HTTPS'] = 'On';
```

