<p align="center"><a href="https://laravel.com" target="_blank"><img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400" alt="Laravel Logo"></a></p>


## Laravel Docker Application

This is a **Laravel application** set up with **Docker**, **Nginx**, and **MySQL**.  

## Requirements

- Docker
- Docker Compose

---

## Project Structure

```
.
├── app
├── artisan
├── bootstrap
├── composer.json
├── composer.lock
├── database
├── docker
├── docker-compose.yml
├── nginx
├── node_modules
├── package.json
├── package-lock.json
├── phpunit.xml
├── public
├── README.md
├── resources
├── routes
├── storage
├── tests
├── vendor
└── vite.config.js
```

---

## Setup Instructions

1. **Clone the repository**

```bash
git clone https://github.com/pranavrjb/laravel-my-app.git
cd laravel-my-app
```
2. **Copy environment file**

``` bash
cp .env.example .env
```

3. **Start Docker containers**

``` bash
docker-compose up -d --build
```

4. **Install PHP dependencies**

``` bash
docker-compose exec app composer install
```

5. **Set Laravel APP_KEY**

``` bash
docker-compose exec app php artisan key:generate
```

6. **Fix permissions**

``` bash
docker-compose exec app chmod -R 775 storage bootstrap/cache
docker-compose exec app chown -R www-data:www-data storage bootstrap/cache
```

7. **Setup Database**

``` bash
docker-compose exec app php artisan migrate
```

8. **Access the Application**

http://localhost:8080

### Notes

- Nginx config is in `nginx/default.conf`
- PHP Dockerfile is in `docker/Dockerfile`
- MySQL container credentials:
  - DB_HOST=db
  - DB_DATABASE=laravel
  - DB_USERNAME=laravel
  - DB_PASSWORD=secret
- Volumes ensure your local changes reflect inside containers automatically
