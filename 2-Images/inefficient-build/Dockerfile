FROM golang:1.12.4

WORKDIR /helloworld

COPY helloworld.go .

RUN GOOS=linux go build -a -installsuffix cgo -o helloworld .

CMD ["./helloworld"]

# This image is inefficient, since we're only interested in the binary (helloworld),
# however we are packaging the whole golang .

