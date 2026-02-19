# Stage 1: build React app (use AWS Public ECR to avoid Docker Hub limits)
FROM public.ecr.aws/docker/library/node:18-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
RUN npm run build

# Stage 2: nginx (AWS Public ECR)
FROM public.ecr.aws/nginx/nginx:alpine
COPY --from=builder /app/build /usr/share/nginx/html
EXPOSE 80