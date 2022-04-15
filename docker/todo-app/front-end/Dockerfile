FROM node:14-alpine AS todofrontend
WORKDIR /app
COPY package*.json ./
ADD ./node_modules.tar.gz ./
EXPOSE  3000
COPY . .
RUN npm install
CMD ["npm", "start"]
