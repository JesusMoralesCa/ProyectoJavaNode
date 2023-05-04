FROM node:latest

WORKDIR /app

COPY package*.json ./
COPY app.js ./

RUN npm install --only=production

EXPOSE 3000

CMD ["npm", "start"]
