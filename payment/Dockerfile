# FROM is used to mention the base OS of the image. It should be the first instruction in Dockerfile.
# Here also we can give environment but if we make any changes we have to rebuild it.
FROM python:3.9
EXPOSE 8080
# This creates /app folder and move the files there.
WORKDIR /app
COPY payment.ini .
COPY *.py .
COPY requirements.txt .
RUN pip3 install -r requirements.txt
# ENV CART_HOST="cart" \
#     CART_PORT="8080" \
#     USER_HOST="user" \
#     USER_PORT="8080" \
#     AMQP_HOST="rabbitmq" \
#     AMQP_USER="roboshop" \
#     AMQP_PASS="roboshop123"
CMD ["uwsgi", "--ini", "payment.ini"]