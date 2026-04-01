FROM node:20.20.2-alpine3.23 AS builder
WORKDIR /app
COPY package.json .
COPY *.js .
RUN npm install --legacy-peer-deps
# This version adds build tools (python3, make, g++) that some npm packages need to compile




FROM node:20.20.2-alpine3.23
WORKDIR /app
EXPOSE 8080
COPY --from=builder /app /app
ENV MONGO="true" \
    MONGO_URL="mongodb://mongodb:27017/catalogue"
# Below is for Security hardening, we are creating a non root user and giving ownership to the app dir to that user and running the app with that user
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop 
RUN chown -R roboshop:roboshop /app
USER roboshop
CMD ["server.js"]
ENTRYPOINT ["node"]
# This is Command to run the app, we can also use CMD ["node", "server.js"] instead of ENTRYPOINT and CMD.

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