# Docker

## Build and Start

Using the repo [vinnyfs89/docker-wordpress](https://github.com/vinnyfs89/docker-wordpress) as reference. Execute the command below to get your Wordpress application working.

```bash
docker-compose up --build --force-recreate -d
docker-compose logs -f
```

{% hint style="info" %}
The application will use 2 services to handle containers. The first to turn on database and second to application.
{% endhint %}



