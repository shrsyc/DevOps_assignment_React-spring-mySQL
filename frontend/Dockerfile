FROM node:22 AS builder
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

FROM nginx:alpine
COPY --from=builder /app/default.conf /etc/nginx/conf.d
COPY --from=builder /app/dist /usr/share/nginx/html
