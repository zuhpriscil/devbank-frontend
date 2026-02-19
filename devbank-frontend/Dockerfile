# Stage 1: build React app
FROM node:18-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# Stage 2: nginx
FROM public.ecr.aws/nginx/nginx:alpine
COPY --from=builder /app/build /usr/share/nginx/html
EXPOSE 80