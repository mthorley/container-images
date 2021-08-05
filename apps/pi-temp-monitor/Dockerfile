FROM arm64v8/node:current-alpine

WORKDIR /app

COPY package*.json ./
COPY *.js .

RUN npm install --production

EXPOSE 5000

CMD ["node", "TemperatureAgent.js"]
