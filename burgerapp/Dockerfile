FROM node:10-alpine

RUN apk update && apk upgrade && apk add --no-cache tini bash git openssh

ENTRYPOINT ["/sbin/tini", "--"]

WORKDIR /code

COPY package.json package-lock.json ./

RUN npm install --frozen-lockfile

COPY . .

RUN yarn run build && yarn global add serve 

EXPOSE 5000

USER node

CMD ["serve", "-s", "build"]
