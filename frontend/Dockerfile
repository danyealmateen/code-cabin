FROM node:18

# Ange arbetskatalog
WORKDIR /app

# Kopiera och installera dependencies
COPY package*.json ./
RUN npm install

# Kopiera resten av projektet
COPY . .

# Bygg React-appen
RUN npm run build

# Installera och använd serve för att köra frontend
RUN npm install -g serve
CMD ["serve", "-s", "build", "-l", "3000"]

EXPOSE 3000