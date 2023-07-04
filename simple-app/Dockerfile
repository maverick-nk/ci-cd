# Use an official Node.js 
FROM node:14 as build

# Set the working directory 
WORKDIR /app

# Copy package*.json
COPY package*.json ./

# Install project dependencies
# RUN npm ci --production --> Requires package-lock.json from same node version.
RUN npm install --only=production

# Copy the project
COPY . .

# Build the React application 
RUN npm run build

# Nginx server
FROM nginx:alpine

# Copy the build files
COPY --from=build /app/build /usr/share/nginx/html

# Expose port 80 for the container
EXPOSE 80

# Start NGINX server
CMD ["nginx", "-g", "daemon off;"]