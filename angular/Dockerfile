# stage 1

FROM node:14.15 AS app-project
WORKDIR /app
COPY . .
RUN npm install && npm run build --prod

# stage 2

FROM nginx:alpine
COPY --from=app-project /app/nginx/nginx.conf /etc/nginx/
COPY --from=app-project /app/nginx/security-headers.conf /etc/nginx/
COPY --from=app-project /app/dist/app /usr/share/nginx/html
EXPOSE 80
