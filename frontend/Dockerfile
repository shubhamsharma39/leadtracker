# ---------- Stage 1: Build ----------
FROM node:20-alpine AS builder

WORKDIR /app

# Copy dependency files first (better caching)
COPY package*.json ./

RUN npm install --legacy-peer-deps

# Copy project files
COPY . .

# Build application
RUN npm run build

# ---------- Stage 2: Nginx ----------
FROM nginx:alpine

# Remove default nginx static files
RUN rm -rf /usr/share/nginx/html/*

# Copy build output
COPY --from=builder /app/dist /usr/share/nginx/html

# Copy nginx config
COPY nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
