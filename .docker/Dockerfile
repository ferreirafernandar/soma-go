FROM golang:1.14.6-alpine3.12 as base

WORKDIR /go/src/soma
COPY . .

RUN go get -v ./...  \
    && go build -ldflags="-s -w"
RUN ls -la

CMD ["soma"]

FROM scratch as prod

COPY --from=base /go/src/soma/soma .

CMD ["/soma"]