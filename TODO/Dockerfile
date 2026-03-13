# Stage 1: Build React frontend
FROM node:18-alpine AS frontend-build

WORKDIR /app/frontend
COPY todo_frontend/package*.json ./
RUN npm install

COPY todo_frontend/ .
RUN npm run build


# Stage 2: Backend
FROM node:18-alpine

WORKDIR /app

COPY todo_backend/package*.json ./
RUN npm install

COPY todo_backend/ .

COPY --from=frontend-build /app/frontend/build ./static/build

ENV MONGODB_URI="mongodb+srv://vmes-ead:WQW4TVXAAvgoQoYb@cluster0.xzkm7.mongodb.net/?appName=Cluster0"

EXPOSE 5000

CMD ["node","server.js"]