# Use an official Node.js 
FROM node:14 as build

# Set the working directory 
WORKDIR /app

# Copy package*.json
COPY package*.json ./

# Defaults to production
ARG NODE_ENV=production
ENV NODE_ENV $NODE_ENV

# Install project dependencies
RUN npm install
RUN npm install -g webpack

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