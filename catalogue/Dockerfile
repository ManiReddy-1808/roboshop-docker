FROM node:20
# This create the dir and move into this
# Install curl and remove the cache to keep the image size small
RUN apk --no-cache add curl
WORKDIR /app
COPY package.json .
COPY *.js .
RUN npm install
ENV MONGO="true"\
    MONGO_URL="mongodb:://mongodb:27017/catalogue"
CMD ["node", "server.js"]