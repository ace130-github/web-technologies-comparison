FROM node:14-alpine3.12 as build
WORKDIR app
COPY package.json yarn.lock ./
RUN yarn install
COPY . .
RUN yarn run build-self-contained

FROM nginx:1.19-alpine
COPY --from=build /app/dist /usr/share/nginx/html/
EXPOSE 80
CMD nginx -g "daemon off;"
