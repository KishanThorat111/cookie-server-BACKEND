# E-commerce Application
## Overview
This project is a full-stack e-commerce application built with Angular for the frontend and Node.js/Express for the backend. The application features cookie-based authentication and is hosted on AWS EC2, utilizing NGINX for reverse proxy and serving static files.

## Features
User registration and authentication
Cookie-based session management
Responsive design using Angular
RESTful API for backend operations
CORS-enabled for cross-origin requests
Frontend (Angular)
Backend (Nodejs)


# Backend (Node.js)

## Getting Started

## Clone the repository:

git clone https://github.com/yourusername/cookie-server-backend.git
cd cookie-server-backend



## Install dependencies:

npm install


## Create a .env file in the root directory and set your environment variables:

MONGODB_USERNAME=your_username
MONGODB_PASSWORD=your_password
SUPER_SECRET_KEY=your_secret_key
PORT=4000



## Start the backend server:

node index.js
The backend will run on http://localhost:4000.

## API Endpoints#

POST /sign-up - Register a new user
POST /sign-in - Authenticate an existing user
POST /logout - Logout the authenticated user
GET /is-authenticated - Check if the user is authenticated
Deployment
Both the frontend and backend applications are deployed on AWS EC2, using NGINX as a reverse proxy.

## NGINX Configuration

The NGINX configuration includes HTTP to HTTPS redirection and proxying requests to the appropriate services:


# Redirect HTTP (port 80) to HTTPS
server {
    listen 80;
    server_name angular.ecommerceweb.shop;

    # Redirect all traffic to HTTPS
    return 301 https://$host$request_uri;
}

# HTTPS server block for your domain
server {
    listen 443 ssl;
    server_name angular.ecommerceweb.shop;

    ssl_certificate /etc/letsencrypt/live/angular.ecommerceweb.shop/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/angular.ecommerceweb.shop/privkey.pem;

    location / {
        proxy_pass http://localhost:4200;  # Proxy requests to the Angular application
    }

    # Error handling for 404 - Not Found
    error_page 404 /index.html;
}
License
This project is licensed under the MIT License. See the LICENSE file for details.

clear
