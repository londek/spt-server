FROM node:16-buster as builder

WORKDIR /app

COPY package.json .
RUN yarn

COPY .parcelrc tsconfig.json base_tsconfig.json ./
COPY src ./src
RUN yarn test:comp-linux


##############################################

FROM debian:buster

COPY --from=builder /app/bundle /bin/Aki-server

EXPOSE 6969

CMD ["/bin/Aki-server"]