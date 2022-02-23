# maintenance-mode-demo
Change to maintenance mode with nginx.

## Build

### SSL setting
```bash
mkcert -key-file docker/nginx/ssl/cert-key.pem -cert-file docker/nginx/ssl/cert.pem localhost 127.0.0.1 ::1
```

### Build
```bash
docker-compose up -d --build
docker-compose exec php composer install
```

## Maintenance mode

- Change to maintenance mode
```bash
# Maintenance mode
docker-compose exec nginx touch /var/www/html/maintenance

# Cancel maintenance mode
docker-compose exec nginx rm -rf /var/www/html/maintenance
```

