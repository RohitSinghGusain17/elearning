# Use Node.js LTS image
FROM node:18

# Set working directory
WORKDIR /app

# Copy package files and install dependencies
COPY package*.json ./
RUN npm install

# Copy frontend code
COPY . .

# Expose frontend port
EXPOSE 3000

# Start frontend development server
CMD ["npm", "start"]