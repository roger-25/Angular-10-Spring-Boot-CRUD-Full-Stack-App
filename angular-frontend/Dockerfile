FROM node:16-alpine AS build
WORKDIR /app
COPY package.json package-lock.json ./
COPY . .
RUN npm install
RUN npm run build

FROM nginx:alpine
COPY --from=build /app/dist/angular-frontend/ /usr/share/nginx/html
CMD ["nginx", "-g", "daemon off;"]