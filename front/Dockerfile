FROM node:lts-alpine as build-stage
RUN npm install -g http-server
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

FROM nginx:stable-alpine as production-stage
COPY --from=build-stage /dist /usr/share/nginx/html
EXPOSE 8080
CMD [ "nginx", "-g", "daemon off;" ]