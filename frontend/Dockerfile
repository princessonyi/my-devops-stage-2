# Use the official Node.js 20.x image as a base
FROM node:20-alpine

# Set the working directory in the container
WORKDIR /app

# Copy package.json and package-lock.json to the container
COPY package*.json ./

# Install dependencies
RUN npm install --production && npm install serve@14.2.3

# Copy the rest of the frontend code to the container
COPY . .

# Build the frontend application
RUN npm run build

# Expose port 80 to allow access to the React app
EXPOSE 80

# Command to start the React application
CMD ["npx", "serve", "-s", "dist", "-l", "80"]

