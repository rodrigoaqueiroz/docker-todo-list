FROM mjgargani/puppeteer:trybe1.0 AS todotests
WORKDIR /app
COPY package*.json ./
ADD ./node_modules.tar.gz ./
COPY . .
RUN npm install
CMD ["npm", "test"]
