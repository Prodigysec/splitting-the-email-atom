# Base image with Joomla
FROM joomla:5.0.2-php8.1-apache

# Install MySQL Server
RUN apt-get update && apt-get install -y mysql-server && rm -rf /var/lib/apt/lists/*

# Set up MySQL environment variables
ENV MYSQL_ROOT_PASSWORD=letmein
ENV MYSQL_DATABASE=joomla

# Create a directory for MySQL
RUN mkdir -p /var/run/mysqld && chown -R mysql:mysql /var/run/mysqld

# Copy Joomla site files (if needed)
COPY site_joomla /var/www/html

# Set permissions
RUN chown -R www-data:www-data /var/www/html

# Expose Joomla (port 80) and MySQL (port 3306)
EXPOSE 80 3306

# Copy Supervisor config
COPY supervisord.conf /etc/supervisor/conf.d/supervisord.conf

# Install Supervisor
RUN apt-get update && apt-get install -y supervisor

# Start both services
CMD ["/usr/bin/supervisord", "-c", "/etc/supervisor/conf.d/supervisord.conf"]
