ARG NODE_VER=17

FROM node:${NODE_VER}

# build strage
ARG APP_DIR=/app

# cd in APP_DIR
WORKDIR ${APP_DIR}

ADD main.js .
ADD package.json .
ADD package-lock.json .
ADD public public
ADD views views

RUN npm i

# run stage
HEALTHCHECK --interval=30s --timeout=5s --start-period=5s --retries=3 \
    CMD curl -s -f http://localhost:${APP_PORT} || exit 1

ENV APP_PORT=5000

# not necessary, just for documentation purposes
EXPOSE ${APP_PORT}

ENTRYPOINT ["node", "main.js"]