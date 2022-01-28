# syntax=docker/dockerfile:1.2
#output : static files
FROM node:16-alpine as build
WORKDIR /code
COPY  ./jira_clone/client/package-lock.json ./jira_clone/client/package.json ./
RUN --mount=type=cache,target=/code/node_modules npm install
COPY ./jira_clone/client/ .
RUN --mount=type=cache,target=/code/node_modules npm run build


FROM nginx:alpine as runner
WORKDIR /code
COPY nginx/nginx.conf /etc/nginx/conf.d/default.conf
COPY --from=build /code/build /usr/share/nginx/html
