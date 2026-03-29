# FROM is used to mention the base OS of the image. It should be the first instruction in Dockerfile.
FROM redis:7

# LABEL is used to add metadata
LABEL project="roboshop" \
      service="redis"

# Redis default port
EXPOSE 6379

# Default Redis server
CMD ["redis-server"]