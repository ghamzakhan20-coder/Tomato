# Build Stage
FROM node:20 AS build

WORKDIR /app

# Dependencies install karo
COPY package*.json ./
RUN npm install

# Source code copy karo
COPY . .

# Production build banao
RUN npm run build

# Serve Stage
FROM nginx:alpine

# Build output ko Nginx ke html directory me copy karo
COPY --from=build /app/dist /usr/share/nginx/html

# Port expose karo
EXPOSE 80

# Nginx ko run karo
CMD ["nginx", "-g", "daemon off;"]
