# Use Node.js LTS image
FROM node:20

# Create app directory
WORKDIR /app

# Copy package files first
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy project files
COPY . .

# Build TypeScript project
RUN npm run build

# Expose application port
EXPOSE 3000

# Start the application
CMD ["npm", "start"]
