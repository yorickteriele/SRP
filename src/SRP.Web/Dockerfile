FROM node:25-alpine AS build
WORKDIR /app

COPY . .

RUN npm install
RUN npm run build

FROM nginx:stable-alpine

COPY config/nginx.conf /etc/nginx/conf.d/default.conf
COPY --from=build /app/dist /usr/share/nginx/html

# Expose port
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
