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

These are sufficient to deploy the stack locally. For cloud deployment, follow the instructions below.

## Containerize application

## Prerequisites

- Docker
- Docker Compose

## Instructions

1. **Build and start services**
   After cloning this repository, build the services by running:
   
      ```sh
   docker compose up -d
   ```
2. **Confirm services**
   - ```sh
     curl localhost
     ``` should produce a HTML response that Nginx proxy manager is successfully installed

