FROM node:18-alpine AS build
WORKDIR /app
COPY package*.json .
RUN npm install
COPY . .
RUN npm run build
 
# Production Stage
FROM nginx:stable-alpine AS production
COPY --from=build /app/dist /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]


# Use a lightweight Node.js image as the base
#FROM node:14-alpine as builder
#FROM node:14-alpine

# Set the working directory inside the container
#WORKDIR /app/frontend

# Copy package.json and package-lock.json (or yarn.lock)
# to leverage Docker's layer caching
#COPY package*.json ./

# Install dependencies
#RUN npm install

# Copy the rest of the application code
#COPY . .

# Build the React application (assuming Create React App or similar build setup)
#RUN npm run build

# --- Production stage ---
#FROM node:14-alpine

# Set the working directory
#WORKDIR /app/frontend

# Copy the built application from the builder stage
# COPY --from=builder /app/frontend/build ./build

# Install a simple static file server (e.g., serve)
# RUN npm install -g serve

# Expose the port your application will run on
# EXPOSE 3000

# Command to start the static file server and serve the built application
# CMD ["serve", "-s", "build", "-l", "3000"]