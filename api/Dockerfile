FROM node:14

# setup okteto message
COPY bashrc /root/.bashrc

WORKDIR /src

COPY package.json yarn.lock ./
RUN yarn install

ARG KEY

RUN --mount=type=cache,target=.temp_cache \
    --mount=type=secret,id=my_env,target=/etc/secrets/.env \
    export $(grep -v '^#' /etc/secrets/.env | xargs)

COPY . .
CMD ["yarn", "start"]
