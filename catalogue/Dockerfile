FROM node:20
# This create the dir and move into this
# "rm -rf /var/lib/apt/lists/*" cleans up the apt cache to keep the image size down
RUN apt-get update && apt-get install -y curl && rm -rf /var/lib/apt/lists/*
WORKDIR /app
COPY package.json .
COPY *.js .
RUN npm install
ENV MONGO="true"\
    MONGO_URL="mongodb:://mongodb:27017/catalogue"
CMD ["node", "server.js"]