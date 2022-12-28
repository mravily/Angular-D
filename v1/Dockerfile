FROM node:19.3.0-alpine3.16

WORKDIR /usr/app

EXPOSE 4200

COPY package*.json ./

RUN npm install -g npm

RUN npm install

COPY . .

RUN npm run build


CMD [ "npm", "run", "start" ]