# Use the official Joomla image
FROM joomla:5.0.2-php8.1-apache

# Set environment variables for the database connection
ENV JOOMLA_DB_HOST=${JOOMLA_DB_HOST}
ENV JOOMLA_DB_PASSWORD=${JOOMLA_DB_PASSWORD}

# Copy local Joomla site files (if needed)
COPY site_joomla /var/www/html

# Set correct permissions
RUN chown -R www-data:www-data /var/www/html

# Expose Joomla on port 80
EXPOSE 80

# Start Apache server
CMD ["apache2-foreground"]
