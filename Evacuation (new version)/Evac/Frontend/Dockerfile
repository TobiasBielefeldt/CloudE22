FROM node:current-alpine as develop-stage

ENV PORT 3333
ENV NODE_ENV development
ENV MONGO_DB_CONNECTION_STRING mongodb+srv:
ENV MONGO_DB_NAME evac
ENV REDIS_URI rediss://default:

# make the 'app' folder the current working directory
WORKDIR /app

# copy both 'package.json' and 'package-lock.json' (if available)
COPY package*.json ./

# install project dependencies
RUN npm install

# copy project files and folders to the current working directory (i.e. 'app' folder)
COPY . .

FROM develop-stage as build-stage

# build app for production with minification
RUN npm run build

FROM nginx:alpine as production-stage

COPY --from=build-stage /app/build /usr/share/nginx/html
COPY nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]

