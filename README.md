# maintenance-mode-demo
Change to maintenance mode with nginx.

## Build

### SSL setting
```bash
mkcert -key-file docker/nginx/ssl/cert-key.pem -cert-file docker/nginx/ssl/cert.pem localhost 127.0.0.1 ::1
```

### Build
```bash
cp -p .env.example .env
```

```bash
docker-compose up -d --build
```

```bash
docker-compose exec php composer install
docker-compose exec php php artisan key:generate
docker-compose exec php php artisan migrate
```

```bash
docker-compose exec php npm ci
docker-compose exec php npm run dev
```

### Access
```bash
https://localhost/register
https://localhost/login
```

## Maintenance mode

- Change to maintenance mode
```bash
# Maintenance mode
docker-compose exec nginx touch /var/www/html/maintenance

# Cancel maintenance mode
docker-compose exec nginx rm -rf /var/www/html/maintenance
```

