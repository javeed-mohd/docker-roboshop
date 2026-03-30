# FROM is used to mention the base OS of the image. It should be the first instruction in Dockerfile.
FROM mysql:8.0

# ENV MYSQL_ROOT_PASSWORD="RoboShop@1"
COPY db/ /docker-entrypoint-initdb.d

# MySQL default port
EXPOSE 3306