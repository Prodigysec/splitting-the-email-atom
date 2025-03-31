# Use the official Joomla image
FROM joomla:5.0.2-php8.1-apache

# Set environment variables for the database connection
ARG JOOMLA_DB_HOST
ARG JOOMLA_DB_USER
ARG JOOMLA_DB_PASSWORD
ARG JOOMLA_DB_NAME
ARG JOOMLA_DB_PORT

ENV JOOMLA_DB_HOST=${JOOMLA_DB_HOST}
ENV JOOMLA_DB_USER=${JOOMLA_DB_USER}
ENV JOOMLA_DB_PASSWORD=${JOOMLA_DB_PASSWORD}
ENV JOOMLA_DB_NAME=${JOOMLA_DB_NAME}
ENV JOOMLA_DB_PORT=${JOOMLA_DB_PORT}

# Set correct permissions
RUN chown -R www-data:www-data /var/www/html

# Install MySQL client for debugging (optional)
RUN apt-get update && apt-get install -y mysql-client && rm -rf /var/lib/apt/lists/*

# Expose Joomla on port 80
EXPOSE 80

# Start Apache server
CMD ["apache2-foreground"]
