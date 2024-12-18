# Use an official Node.js runtime as a parent image
FROM node:18

# Set the working directory inside the container
WORKDIR /app

# Copy package.json and package-lock.json (or yarn.lock if using Yarn)
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of your application code
COPY . .

# Build the Nuxt app (this runs 'nuxt build' to prepare the app for production)
RUN npm run build

# Expose the port the app will run on
EXPOSE 3000

# Command to run your app (this uses 'npm run serve' to start the production server)
CMD ["npm", "run", "serve"]
