FROM node:20.20.2-alpine3.23 AS builder
# This creates /app folder and move the files there.
WORKDIR /app
COPY package.json .
COPY *.js .
RUN npm install

FROM node:20.20.2-alpine3.23
# This creates /app folder and move the files there.
WORKDIR /app
EXPOSE 8080
COPY --from=builder /app /app
# This ENV is going to be handled by configMap in Kubernetes.
# ENV REDIS_HOST="redis" \
#     CATALOGUE_HOST="catalogue" \
#     CATALOGUE_PORT="8080"
# Adding the user
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
# Adding permissions
RUN chown -R roboshop:roboshop /app
USER roboshop
CMD ["server.js"]
ENTRYPOINT ["node"]

# # FROM is used to mention the base OS of the image. It should be the first instruction in Dockerfile.
# FROM node:20
# # This creates /app folder and move the files there.
# WORKDIR /app
# COPY package.json .
# COPY *.js .
# RUN npm install
# ENV REDIS_HOST="redis" \
#     CATALOGUE_HOST="catalogue" \
#     CATALOGUE_PORT="8080"
# CMD ["node", "server.js"]