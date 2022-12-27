FROM node:15.4.0

ENV PORT 3333
ENV NODE_ENV development
ENV MONGO_DB_CONNECTION_STRING mongodb+srv:
ENV MONGO_DB_NAME evac
ENV REDIS_URI rediss://default:

COPY . /app
WORKDIR /app

EXPOSE 3333

RUN npm install

CMD ["npm", "start"]
