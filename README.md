# Project Description

This project sets up a Dockerized environment for running a Flask web application behind an Nginx reverse proxy. The project uses Docker Compose to manage these services, aiming to follow best practices by running each service in its own container.

## Flask Application:

The Flask application is a basic "Hello World" web app. When accessed, it responds with an HTML message that says "Hello World!".

## Docker Compose Configuration:

This project employs Docker Compose to define and run the services, making it easier to manage multi-container Docker applications. The docker-compose.yaml file outlines two services: app and nginx.

- App Service: Built using the current directory as the build context, which includes the Flask application's code. This service installs Python dependencies from requirements.txt and starts the Flask app.

- Nginx Service: Utilizes the official Nginx Docker image. It maps port 8080 on the host machine to port 80 inside the container. The Nginx configuration (nginx.conf) for the reverse proxy is also mounted into the container.

## Nginx Configuration:

The nginx.conf file houses the Nginx configuration that sets up the reverse proxy. The proxy forwards requests arriving at Nginx (port 80 inside the container) to the Flask application running on port 5000 inside its respective container.

## Running the Application:

To run the application, make sure you have Docker and Docker Compose installed on your machine. Then, execute the following command in the terminal from the directory where your docker-compose.yaml file is located:

```
    docker-compose up --build
```
This command builds the Docker images if they don't exist or have been changed, starts the containers, and sets up the network between them. You can access the Flask app by navigating to http://localhost:8080 in your web browser.

To stop and remove all containers and resources created by docker-compose up, use:

```
    docker-compose down
```
