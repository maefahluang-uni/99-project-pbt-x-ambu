# Stage 1: Build the Nuxt.js application
FROM node:16-alpine AS build

# Set the working directory in the container
WORKDIR /app

COPY package*.json ./
# Install dependencies
RUN npm install
COPY . .
RUN npm run build
FROM nginx:alpine

COPY --from=build /app/dist /usr/share/nginx/html

EXPOSE 80
# Command to run Nginx
CMD ["nginx", "-g", "daemon off;"]
