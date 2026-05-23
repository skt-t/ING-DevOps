# ==========================================
# Etapa 1: Construcción (Build)
# ==========================================
FROM node:18-alpine AS builder
WORKDIR /app

# Copiamos el gestor de dependencias e instalamos
COPY package*.json ./
RUN npm install

# Copiamos el resto del código y compilamos
COPY . .
RUN npm run build

# ==========================================
# Etapa 2: Servidor Web (Producción)
# ==========================================
FROM nginx:alpine

# Copiamos los archivos estáticos compilados al directorio de Nginx
COPY --from=builder /app/dist /usr/share/nginx/html

# Exponemos el puerto web
EXPOSE 80

# Iniciamos Nginx
CMD ["nginx", "-g", "daemon off;"]
