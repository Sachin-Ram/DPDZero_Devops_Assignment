FROM golang:1.24.4

WORKDIR /app

# Only copy go.mod since go.sum doesn't exist
COPY go.mod ./

# This will still try to download deps — go.sum may be created
RUN go mod tidy

# Copy rest of the source code
COPY . ./

# Build the binary
RUN go build -o service1 .

# Expose the port your service runs on
EXPOSE 8001

# Run the compiled Go binary
CMD ["./service1"]
