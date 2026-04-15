FROM alpine:3.23 AS builder

RUN apk --no-cache add cmake clang clang-dev make gcc g++ libc-dev linux-headers

WORKDIR /app

COPY ./src ./src
COPY ./CMakeLists.txt ./CMakeLists.txt

RUN cmake -H. -B_builds
RUN cmake --build _builds


FROM alpine:3.23

WORKDIR /app
COPY --from=builder /app/_builds/app .
COPY --from=builder /usr/lib/* /usr/lib/ 

CMD ["./app"]
