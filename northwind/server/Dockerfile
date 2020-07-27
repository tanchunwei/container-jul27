FROM node:14

ENV APP_DIR=/app APP_PORT=3000 DB_USER=root DB_PASSWORD=changeit

ADD main.js .
ADD package.json .
ADD package-lock.json .
ADD public public
ADD views views

RUN npm install

# Add health check
HEALTHCHECK --interval=30s --timeout=3s --start-period=5s --retries=3 \
    CMD curl -s -f http://localhost:${APP_PORT}/health || exit 1

EXPOSE ${APP_PORT}

ENTRYPOINT ["node", "main.js"]
