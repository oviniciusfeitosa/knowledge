# Known Issues

## WordPress: Too many redirects issue when NGINX reverse proxy to apache

Add this in your _wp-config.php:_

```bash
$_SERVER['HTTPS'] = 'On';
```

