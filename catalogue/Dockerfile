FROM node:20.20.2-alpine3.23 AS builder
WORKDIR /app
COPY package.json .
COPY *.js .
RUN npm install --legacy-peer-deps
# This version adds build tools (python3, make, g++) that some npm packages need to compile
ENV MONGO="true" \
    MONGO_URL="mongodb://mongodb:27017/catalogue"
CMD ["node", "server.js"]



# FROM node:20
# # This create the dir and move into this
# WORKDIR /app
# COPY package.json .
# COPY *.js .
# RUN npm install --legacy-peer-deps
# # This version adds build tools (python3, make, g++) that some npm packages need to compile
# ENV MONGO="true" \
#     MONGO_URL="mongodb://mongodb:27017/catalogue"
# CMD ["node", "server.js"]