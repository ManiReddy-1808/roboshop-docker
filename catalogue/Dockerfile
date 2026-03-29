FROM node:20
# This create the dir and move into this
WORKDIR /app
COPY package.json .
COPY *.js .
RUN npm install
RUN apk --update add curl
ENV MONGO="true"\
    MONGO_URL="mongodb:://mongodb:27017/catalogue"
CMD ["node", "server.js"]