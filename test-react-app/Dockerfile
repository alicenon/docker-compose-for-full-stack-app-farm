# Fase 1: Construir el frontend
FROM node:24-alpine as build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN echo "=== Directorio antes de build ===" && ls -la
RUN npm run build
RUN echo "=== Directorio después de build ===" && ls -la
RUN echo "=== Contenido de dist ===" && ls -la dist/

# Fase 2: Servir con Nginx
FROM nginx:alpine
COPY --from=build /app/dist /usr/share/nginx/html
RUN chmod -R 755 /usr/share/nginx/html
COPY nginx/nginx.conf /etc/nginx/nginx.conf
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]