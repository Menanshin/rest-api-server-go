# Используем более легкий образ для сборки
FROM golang:1.19-alpine as builder

WORKDIR /build

COPY . .

# Сборка бинарного файла main
RUN go build -o main main.go

# Новый этап для минимизации размера образа
FROM alpine:latest

WORKDIR /root/

# Копируем только скомпилированный бинарник
COPY --from=builder /build/main .

EXPOSE 8080

LABEL authors="e.maslov"

CMD ["./main"]
