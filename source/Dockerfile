# Use nginx as base image
FROM nginx:1.24

# Copy the static files to nginx's default public directory
COPY . /usr/share/nginx/html/

# Expose port 8080 (matching your docker-compose configuration)
EXPOSE 8080

# Copy custom nginx configuration to change the default port to 8080
RUN echo 'server { \
    listen 8080; \
    server_name localhost; \
    location / { \
        root /usr/share/nginx/html; \
        index index.html; \
        try_files $uri $uri/ /index.html; \
    } \
}' > /etc/nginx/conf.d/default.conf

# Start Nginx in the foreground
CMD ["nginx", "-g", "daemon off;"]