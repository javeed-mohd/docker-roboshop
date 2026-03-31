# FROM is used to mention the base OS of the image. It should be the first instruction in Dockerfile.
FROM rabbitmq:3-management

ENV RABBITMQ_DEFAULT_USER=roboshop \
    RABBITMQ_DEFAULT_PASS=roboshop123

# Backend Services Application Communication
EXPOSE 5672

# UI Browser Management
EXPOSE 15672