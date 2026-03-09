# Fase 1: Construir el frontend
FROM node:24-alpine as build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build  # ✅ Construye el frontend para producción

# Fase 2: Servir con Nginx
FROM nginx:alpine
COPY --from=build /app/dist /usr/share/nginx/html
COPY nginx/nginx.conf /etc/nginx/nginx.conf
RUN chmod -R 755 /usr/share/nginx/html  # ✅ Asegura permisos de lectura
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]