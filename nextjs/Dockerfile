# Base image
FROM node:lts-alpine

# Set the working directory
WORKDIR /app

# Install dependencies
COPY package*.json ./
RUN npm install

# Copy application files
COPY . .

# Build the Next.js application
RUN npm run build

# Expose the necessary port
EXPOSE 3000

# Run the Next.js application
CMD ["npm", "start"]