# lint, test, transpile and build binary (as deb)
FROM node:12.4 as builder
WORKDIR /usr/app/builder
COPY ./components ./components
COPY ./*.json ./
RUN npm install
RUN npm run clean && npm run bootstrap && npm run build
RUN npm run lint && npm run test
RUN npm run dist
RUN cp ./components/stream-provider/bin/*.deb ./

RUN yarn global add http-server
CMD http-server components/stream-consumer
