FROM node:18-alpine AS build
WORKDIR /app
COPY package*.json ./
RUN npm install && npm install -g @angular/cli
COPY . .
RUN npm run build 

FROM nginx:alpine
COPY nginx.conf /etc/nginx/conf.d/nginx.conf
COPY --from=build /app/dist/user-interface  /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
