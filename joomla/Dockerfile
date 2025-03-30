# Use the official Joomla image
FROM joomla:5.0.2-php8.1-apache

# Install MySQL Server
RUN apt-get update && apt-get install -y mysql-server && rm -rf /var/lib/apt/lists/*

# Set MySQL environment variables
ENV MYSQL_ROOT_PASSWORD=letmein
ENV MYSQL_DATABASE=joomla

# Create required MySQL directories
RUN mkdir -p /var/run/mysqld && chown -R mysql:mysql /var/run/mysqld

# Copy Joomla site files (if needed)
COPY site_joomla /var/www/html

# Set correct permissions
RUN chown -R www-data:www-data /var/www/html

# Expose Joomla port (MySQL stays internal)
EXPOSE 80

# Copy Supervisor configuration
COPY supervisord.conf /etc/supervisor/conf.d/supervisord.conf

# Install Supervisor to manage multiple services
RUN apt-get update && apt-get install -y supervisor

# Start both Joomla and MySQL
CMD ["/usr/bin/supervisord", "-c", "/etc/supervisor/conf.d/supervisord.conf"]
