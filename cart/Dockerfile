# FROM is used to mention the base OS of the image. It should be the first instruction in Dockerfile.
FROM node:20
# This creates /app folder and move the files there.
WORKDIR /app
COPY package.json .
COPY *.js .
RUN npm install
ENV REDIS_HOST="redis" \
    CATALOGUE_HOST="catalogue" \
    CATALOGUE_PORT="8080"
CMD ["node", "server.js"]