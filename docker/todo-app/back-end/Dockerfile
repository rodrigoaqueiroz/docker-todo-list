FROM node:14-alpine AS todobackend
WORKDIR /app
COPY package*.json ./
ADD ./node_modules.tar.gz ./
EXPOSE  3001
COPY . .
RUN npm install
CMD ["npm", "start"]
