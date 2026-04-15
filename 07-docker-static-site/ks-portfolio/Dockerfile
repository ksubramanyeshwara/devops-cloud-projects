# Use official Nginx image as the base image
# Use alpine variant for a smaller image size
FROM nginx:alpine

# Copy the static website files to the Nginx HTML directory
COPY . /usr/share/nginx/html

# Expose port 80 to allow web traffic to the container
EXPOSE 80