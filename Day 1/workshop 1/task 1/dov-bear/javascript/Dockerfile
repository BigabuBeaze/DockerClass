ARG NODE_VER=17

FROM node:${NODE_VER}

# build strage
ARG APP_DIR=/app

# cd in APP_DIR
WORKDIR ${APP_DIR}

ADD . .

RUN npm i

# run stage
HEALTHCHECK --interval=30s --timeout=5s --start-period=5s --retries=3 \
    CMD curl -s -f http://localhost:${PORT}/healthz || exit 1

ENV PORT=5000
ENV INSTANCE_HASH=123123123
ENV INSTANCE_NAME=munpan

# not necessary, just for documentation purposes
EXPOSE ${PORT}

ENTRYPOINT ["node", "main.js"]