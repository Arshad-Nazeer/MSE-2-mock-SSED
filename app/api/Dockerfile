FROM node:20-alpine
WORKDIR /app

RUN chown node:node /app
COPY --chown=node:node package*.json ./

USER node
RUN npm install --omit=dev && npm cache clean --force

COPY --chown=node:node . .

EXPOSE 3000
HEALTHCHECK --interval=10s --timeout=3s --retries=3 \
  CMD wget -qO- http://127.0.0.1:3000/api/health || exit 1

CMD ["npm", "start"]
