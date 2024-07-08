# Full-Stack FastAPI and React Template

Welcome to the Full-Stack FastAPI and React template repository. This repository serves as a demo application for interns, showcasing how to set up and run a full-stack application with a FastAPI backend and a ReactJS frontend using ChakraUI.

## Project Structure

The repository is organized into two main directories:

- **frontend**: Contains the ReactJS application.
- **backend**: Contains the FastAPI application and PostgreSQL database integration.

Each directory has its own README file with detailed instructions specific to that part of the application.

## Getting Started

To get started with this template, please follow the instructions in the respective directories:

- [Frontend README](./frontend/README.md)
- [Backend README](./backend/README.md)

These are sufficient to deploy the stack locally. For cloud deployment, using your registered domain, follow the instructions below.

## Containerize application

## Prerequisites

- Docker
- Docker Compose

Before we begin, make sure to change the API_URL in your [Frontend ,env file](./frontend/.env) to the name of your domain

## Instructions

1. **Build and start services**:
After cloning this repository, build the services by running:
```sh
docker compose up -d
```

2. **Confirm services**:
```sh
curl localhost
```
should produce a HTML response that Nginx proxy manager is successfully installed

3. **Reverse Proxying and SSL setup with Nginx proxy manager**:
- Access the Proxy manager UI by entering http://your-IP:81 in your browser, Ensure that port is open in your security group or firewall.
- Login with the default Admin credentials:
   **Email**: admin@example.com
   **Password**: changeme 
- Click on Proxy host and setup the proxy for your frontend and backend
Map your domain name to the service name of your frontend and the port the container is listening on Internally. Request a new certificate from the SSL tab
- Before saving, to configure the frontend to route api requests to the backend on the same domain, click on Advanced and paste this configuration:
```sh
location /api {
    proxy_pass http://backend:8000;
    proxy_set_header Host $host;
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_set_header X-Forwarded-Proto $scheme;
}

location /docs {
    proxy_pass http://backend:8000;
    proxy_set_header Host $host;
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_set_header X-Forwarded-Proto $scheme;
}

location /redoc {
    proxy_pass http://backend:8000;
    proxy_set_header Host $host;
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_set_header X-Forwarded-Proto $scheme;
}
```
...now save.

- Configure db.domain to route to your adminer service on port 8080, request SSL cert and save.
- Also, proxy.domain: to route to the proxy service UI on port 81; request SSL cert and save.

4. **Setup Adminer**
   - Access the adminer web interface on db.<your_domain>.com
   - Login with the db credentials in your backend .env file

5. **Setup Frontend login**
   - Access your frontend on <your_domain>
   - Provide credentials as found in [backend .env file](./backend/.env)
