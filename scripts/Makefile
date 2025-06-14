.PHONY: all build test lint clean

# 定义变量，可通过命令传参
MODULE := example
VERSION := 1.0.0

# 构建Linux可执行文件
build-linux:
    go mod tidy
    GOOS=linux GOARCH=amd64 go build -ldflags "-s -w" -o bin/$(MODULE)-linux ../cmd/$(MODULE)

# 构建Windows可执行文件  
build-win:
    go mod tidy
    GOOS=windows GOARCH=amd64 go build -ldflags "-s -w" -o bin/$(MODULE)-win.exe ../cmd/$(MODULE)

# 运行单元测试
test:
    go test -v ./...

# 代码静态检查
lint:
    golangci-lint run

# 清理构建产物
clean:
    rm -rf bin/
    go clean

# Docker镜像构建
docker-build:
    docker build -t $(MODULE):$(VERSION) .

# 多阶段构建（生产环境镜像）
docker-prod:
    docker build -t $(MODULE):prod --target=prod .