# Use the node:lts-alpine3.19 image as the base image
FROM node:lts-alpine3.19

# Install necessary dependencies for the development environment
RUN apk add --no-cache git

# Set the working directory to /workspace
WORKDIR /workspace

# Copy the application code into the container
COPY . .

# Install Node.js dependencies using npm install
RUN npm install
