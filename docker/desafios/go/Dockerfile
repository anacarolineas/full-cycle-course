FROM golang:1.20 AS build

WORKDIR /app

COPY go.mod main.go ./

# Compila o código-fonte, flags para reduzir o tamanho do binário remove símbolos
RUN CGO_ENABLED=0 GOOS=linux go build -ldflags="-s -w" -o desafio-go .

FROM scratch

WORKDIR /app

# Copie o binário compilado do estágio anterior
COPY --from=build /app/desafio-go .

CMD ["./desafio-go"]