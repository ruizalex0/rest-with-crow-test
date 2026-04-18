FROM alpine:3.23 AS builder

RUN apk --no-cache add cmake clang clang-dev make gcc g++ libc-dev linux-headers curl tar gzip python3

WORKDIR /app

COPY ./external ./external
COPY ./src ./src
COPY ./includes ./includes
COPY ./CMakeLists.txt .
COPY ./Makefile .

RUN make build


FROM alpine:3.23

WORKDIR /app
COPY --from=builder /usr/lib/* /usr/lib/ 
COPY --from=builder /app/bin/app .

CMD ["./app"]
