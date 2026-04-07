FROM maven:3.9.14 AS builder
# This creates /app folder and move the files there.
WORKDIR /app
COPY pom.xml .
COPY src ./src
RUN mvn clean package && \
    mv target/shipping-1.0.jar shipping.jar

FROM eclipse-temurin:17-jre-alpine
EXPOSE 8080
WORKDIR /app
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop && \
    chown -R roboshop:roboshop /app
COPY --from=builder /app/shipping.jar .
# This ENV is going to be handled by configmap in Kubernetes.
# ENV CART_ENDPOINT="cart:8080" \
#     DB_HOST="mysql"
# CMD ["java", "-jar", "shipping.jar"]
USER roboshop
ENTRYPOINT ["java", "-jar", "shipping.jar"]

# # FROM is used to mention the base OS of the image. It should be the first instruction in Dockerfile.
# FROM maven:3.9.14
# EXPOSE 8080
# # This creates /app folder and move the files there.
# WORKDIR /app
# COPY pom.xml .
# COPY src ./src
# RUN mvn clean package
# RUN mv target/shipping-1.0.jar shipping.jar
# ENV CART_ENDPOINT="cart:8080" \
#     DB_HOST="mysql"
# CMD ["java", "-jar", "shipping.jar"]