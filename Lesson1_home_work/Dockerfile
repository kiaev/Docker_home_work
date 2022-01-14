FROM node:9
EXPOSE 3000
WORKDIR /app
COPY package*.json ./
COPY ./public ./public
COPY ./src ./src
RUN npm install
CMD ["npm", "start"]
