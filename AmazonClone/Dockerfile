FROM node:slim AS build
WORKDIR /apps

COPY package*.json .

RUN npm install

COPY . .

RUN npm run build 

RUN ls -l /apps
RUN ls -l /apps/dist


FROM nginx:alpine

COPY --from=build /apps/dist /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]


