# ---- Stage 1: Bağımlılıkları kur ----
FROM node:18-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm ci --only=production

# ---- Stage 2: Production image ----
FROM node:18-alpine
WORKDIR /app

RUN addgroup -S nodejs && adduser -S nodejs -G nodejs

COPY --from=builder /app/node_modules ./node_modules
COPY . .

USER nodejs

ENV NODE_ENV=production

HEALTHCHECK --interval=10s --timeout=5s --retries=5 \
  CMD wget -qO- http://localhost:3500/health || exit 1

EXPOSE 3500
CMD ["node", "server.js"]
