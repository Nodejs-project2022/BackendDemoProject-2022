# Name: Avinash Yelpula
# Project: BackendDemoProject-2022
# Project Description:
This project is used host nodejs based application on decker container platform.

# Create Dockerfile:
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



