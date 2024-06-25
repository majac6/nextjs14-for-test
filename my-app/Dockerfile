# Step 1: Build the application
FROM node:20 AS builder

WORKDIR /app

# SSL 인증서 검증 무시 설정
ENV NODE_TLS_REJECT_UNAUTHORIZED=0

COPY package*.json ./
RUN npm install

COPY . .
RUN npm run build

# Step 2: Run the application
FROM node:20-alpine

WORKDIR /app

COPY --from=builder /app ./
EXPOSE 3000

CMD ["npm", "run", "start"]
