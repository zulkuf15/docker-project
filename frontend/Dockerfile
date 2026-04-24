# # Dockerfile — Single-stage React + Node.js server (no Nginx)
# FROM node:21-alpine3.17

# WORKDIR /app

# # Copy dependencies and install
# COPY package*.json ./
# RUN npm install && npm install serve @chakra-ui/icons

# # Copy the rest of the project
# COPY . .

# # Build-time variable for backend API
# ARG REACT_APP_API_BASE_URL
# ENV REACT_APP_API_BASE_URL=$REACT_APP_API_BASE_URL

# # Build the React app
# RUN npm run build

# # Expose app port
# EXPOSE 3000

# # Serve static files using 'serve'
# CMD ["npx", "serve", "-s", "build", "-l", "3000"]

# ---- Stage 1: Build React app ----
FROM node:20-alpine AS build
WORKDIR /app

COPY package*.json ./
RUN npm ci

COPY . .

ARG REACT_APP_API_BASE_URL
ENV REACT_APP_API_BASE_URL=$REACT_APP_API_BASE_URL

RUN npm run build

# ---- Stage 2: Serve with Nginx ----
FROM nginx:1.25.3-alpine

COPY --from=build /app/build /usr/share/nginx/html
COPY nginx.conf /etc/nginx/conf.d/default.conf

RUN chown -R nginx:nginx /usr/share/nginx/html

HEALTHCHECK --interval=10s --timeout=5s --retries=3 \
  CMD wget -qO- http://localhost:80 || exit 1

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]

