FROM nginx:1.24.0-alpine3.17-slim

# Remove default nginx configuration
RUN rm -f /etc/nginx/nginx.conf
RUN rm -f /etc/nginx/conf.d/default.conf

# Copy custom nginx configuration
COPY nginx.conf /etc/nginx/nginx.conf

# Copy frontend static files
COPY static/ /usr/share/nginx/html/

# Expose port
EXPOSE 80

# Start nginx
CMD ["nginx", "-g", "daemon off;"]


# FROM nginx:1.24.0
# RUN rm -f /usr/share/nginx/html/index.html
# RUN rm -f /etc/nginx/nginx.conf
# RUN rm -f /etc/nginx/conf.d/default.conf
# COPY nginx.conf /etc/nginx/nginx.conf
# COPY static /usr/share/nginx/html/
