# Name: Avinash Yelpula
# Project: BackendDemoProject-2022
# Project Description:
This project is used host nodejs based application on decker container platform.

# Part-1: Create Dockerfile.
# Steps:
FROM node:latest

# Create app directory
WORKDIR /usr/src/app

# Install app dependencies
COPY package*.json ./
RUN npm install

# Copy app source code
COPY . .

# Expose port and start application
EXPOSE 8080
CMD [ "npm", "start" ]

## Part-2: Create Docker-compose yaml file
I used docker compose version (3.8)
version: "3.8"

Created three containers with names like app, mongodb, mysql and with configurations. Here i given dockerfile path to build a docker image.


services:
  app:
    build: .
    ports:
    - "8080:8080"
    depends_on:
    - mongo
    - mysql
  mongo:
    image: mongo
    ports:
    - "27017:27017"
    volumes:
    - mongo-volume:/data/db
  mysql:
    image: mysql:8
    restart: always
    environment:
      MYSQL_DATABASE: DB
      MYSQL_PASSWORD: root
      MYSQL_ROOT_PASSWORD: root
    volumes:
      - mysql-volume:/var/lib/mysql
    ports:
      - 33066:3306
volumes:
  mongo-volume:
  mysql-volume






