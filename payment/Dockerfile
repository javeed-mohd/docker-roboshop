FROM python:3.9.25-alpine3.22 AS builder
# This creates /app folder and move the files there.
WORKDIR /app
RUN apk add --no-cache build-base linux-headers pcre-dev
COPY requirements.txt .
RUN pip3.9 install --prefix=/install -r requirements.txt

FROM python:3.9.25-alpine3.22
EXPOSE 8080
WORKDIR /app
RUN apk add --no-cache pcre
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
RUN chown -R roboshop:roboshop /app
COPY --from=builder /install /usr/local
COPY --chown=roboshop:roboshop payment.ini *.py requirements.txt .
# This ENV is going to be handled by configmap in Kubernetes.
# ENV CART_HOST="cart" \
#     CART_PORT="8080" \
#     USER_HOST="user" \
#     USER_PORT="8080" \
#     AMQP_HOST="rabbitmq" \
#     AMQP_USER="roboshop" \
#     AMQP_PASS="roboshop123"
USER roboshop
CMD ["uwsgi", "--ini", "payment.ini"]

# # FROM is used to mention the base OS of the image. It should be the first instruction in Dockerfile.
# # Here also we can give environment but if we make any changes we have to rebuild it.
# # Debian/Ubuntu
# FROM python:3.9
# EXPOSE 8080
# # This creates /app folder and move the files there.
# WORKDIR /app
# COPY payment.ini .
# COPY *.py .
# COPY requirements.txt .
# RUN pip3 install -r requirements.txt
# ENV CART_HOST="cart" \
#     CART_PORT="8080" \
#     USER_HOST="user" \
#     USER_PORT="8080" \
#     AMQP_HOST="rabbitmq" \
#     AMQP_USER="roboshop" \
#     AMQP_PASS="roboshop123"
# CMD ["uwsgi", "--ini", "payment.ini"]