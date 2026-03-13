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

# Install backend dependencies
COPY todo_backend/package*.json ./
RUN npm install

# Copy backend code
COPY todo_backend/ .

# Copy React build into backend static folder
COPY --from=frontend-build /app/frontend/build ./static/build

# Environment variable
ENV MONGODB_URI="mongodb+srv://vmes-ead:WQW4TVXAAvgoQoYb@cluster0.xzkm7.mongodb.net/?appName=Cluster0"

EXPOSE 5000

CMD ["node","server.js"]