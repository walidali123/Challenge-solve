# Docker Compose Environment for Laravel API, Nuxt.js, MySQL, and Nginx

This project demonstrates how to set up a multi-container Docker environment with MySQL, a Laravel API, a Nuxt.js client, and Nginx as a reverse proxy using Docker Compose.

## Prerequisites

Before you begin, ensure you have the following installed:

- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)
- [OpenSSL](https://www.openssl.org/) (to generate SSL certificates)

## Services Overview

1. **MySQL (db):** The database service using MySQL 8.
2. **Laravel API (api):** The backend API service built with Laravel.
3. **Nuxt.js Client (client):** The frontend application built with Nuxt.js.
4. **Nginx (nginx):** Acts as a reverse proxy for the Nuxt.js frontend, handling both HTTP and HTTPS traffic.

## Project Structure
. ├── api # Laravel API codebase ├── client # Nuxt.js client codebase ├── certs # Directory to hold SSL certificates ├── nginx.conf # Nginx configuration file └── docker-compose.yml # Docker Compose configuration file

# Create a directory for certificates if it doesn't exist
mkdir -p ./certs

# Generate a private key
openssl genrsa -out ./certs/self-signed.key 2048

# Generate a self-signed certificate
openssl req -new -x509 -key ./certs/self-signed.key -out ./certs/self-signed.crt -days 365 -subj "/C=US/ST=State/L=City/O=Organization/OU=Unit/CN=localhost"




# Nuxt.js Application with Nginx Proxy

## Application Overview
This is a Nuxt.js application running behind an Nginx proxy using Docker Compose.

## Screenshots

### Application Running
![Home Page](./screenshots/homepage.png)

### Docker-compose Response
![docker-compose](./screenshots/docker-compose-running.png)

