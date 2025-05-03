#Stage 1: Build the React app
FROM node:20-alpine AS builder

#Setting the working directory
WORKDIR /app

#Copying the depenedencies
COPY package*.json ./

#Installing the dependencies
RUN npm install

#Copying the source code
COPY . .

#Building the project
RUN npm run build

# Stage 2: Serve the app using `serve`
FROM node:20-alpine

WORKDIR /app

# Install a simple static file server
RUN npm install -g serve

# Copy built React app from builder
COPY --from=builder /app/build ./build

# Expose port
EXPOSE 3000

# Serve the app
CMD ["serve", "-s", "build", "-l", "3000"]
