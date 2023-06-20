FROM node:15 as builder

WORKDIR /app

COPY package* ./

RUN npm ci --omit=dev

COPY . .

RUN npm run build

FROM node:15 as runner

WORKDIR /app

COPY --from=builder /app/build ./

RUN  npm install -g serve

ENTRYPOINT [ "serve", "-s", "./" ]
