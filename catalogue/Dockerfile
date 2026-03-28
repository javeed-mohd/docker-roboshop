# FROM is used to mention the base OS of the image. It should be the first instruction in Dockerfile.
FROM node:20
# This creates /app folder and move the files there.
WORKDIR /app
COPY package.json .
COPY *.js .
RUN npm install
ENV MONGO="true" \
    MONGO_URL="mongodb://mongodb:27017/catalogue"
CMD ["node", "server.js"]