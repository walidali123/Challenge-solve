# Use a specific version of Node.js
FROM node:20

# Set the working directory inside the container
WORKDIR /app

# Copy package.json and package-lock.json (if exists)
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code
COPY . .

# Build the Nuxt.js application
RUN npm run build

# Expose port 3000 for the Nuxt.js application
EXPOSE 3000

# Command to run the Nuxt.js application
CMD ["npm", "run", "serve"]
