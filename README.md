<p align="center"><a href="#" target="_blank"><img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400"></a></p>

<p align="center">Products Microservices | Event Driven Architecture with RabbitMQ</p>
<p align="center">
<img src="https://img.shields.io/static/v1?label=&message=Laravel&color=red" alt="Laravel">
<img src="https://img.shields.io/static/v1?label=&message=Docker&color=blue" alt="Docker">
<img src="https://img.shields.io/static/v1?label=&message=Docker+Compose&color=orange" alt="Docker Compose">
<img src="https://img.shields.io/static/v1?label=&message=MySQL&color=yellowgreen" alt="MySQL">
<img src="https://img.shields.io/static/v1?label=&message=phpMyAdmin&color=yellow" alt="phpMyAdmin">
</p>

## About

There are two Laravel applications:

- Admin Application `micro_admin`
- Main Application `micro_main`

Admin Application creates, updates or deletes the product, which fires an event to do the same action in Main Application as well.

Like<3 the product through Main Application, which fires an event to update the Admin Application as well.


## Run The Applications

Clone the repository.

### Admin Application:

Goto `micro_admin` directory. Create .env file using .env.example file. Setup RabbitMQ credentials in .env file.

    RABBITMQ_HOST=
    RABBITMQ_USER=
    RABBITMQ_PASSWORD=-
    RABBITMQ_VHOST=

Open the terminal inside the directory and run the below Docker command:
```sh
docker-compose up
```
Application is up and running now.

URL: `http://localhost:8000/`

phpMyAdmin URL: `http://localhost:8080/`


### Main Application:

Goto `micro_main` directory. Create .env file using .env.example file. Setup RabbitMQ credentials in .env file.

    RABBITMQ_HOST=
    RABBITMQ_USER=
    RABBITMQ_PASSWORD=-
    RABBITMQ_VHOST=

Open the terminal inside the directory and run the below Docker command:
```sh
docker-compose up
```
Application is up and running now.

URL: `http://localhost:8001/`

phpMyAdmin URL: `http://localhost:8081/`


## API Resources

### Admin Application:

- Show All Products of Admin App:

  GET `http://localhost:8000/api/products`


- Create Product:
  
    POST `http://localhost:8000/api/products`

    Request body:

        {
            "title": "Product 1",
            "image": "https://www.product1-image.xyz"
        }


- Find Product:

  GET `http://localhost:8000/api/products/{id}`


- Update Product:

  PUT `http://localhost:8000/api/products`

  Request body:

        {
            "title": "Product 2",
            "image": "https://www.product2-image.xyz"
        }


- Delete Product:

  DELETE `http://localhost:8000/api/products/{id}`


### Main Application:

- Like<3 the Product:

  POST `http://localhost:8001/api/products/{id}/like`


- Show All Products of Main App:

  GET `http://localhost:8001/api/products`