# Use the official MySQL 8.0 image
FROM mysql:8.0.13

# Set environment variables for MySQL
ENV MYSQL_ROOT_PASSWORD=letmein
ENV MYSQL_DATABASE=joomla

# Expose MySQL port
EXPOSE 3306

# Healthcheck for MySQL readiness
HEALTHCHECK --interval=30s --timeout=10s --retries=5 \
  CMD mysqladmin ping -h localhost || exit 1
