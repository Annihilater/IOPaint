# IOPaint Docker Compose 部署指南

此目录包含 `docker-compose.yaml` 文件，用于通过 Docker Compose 部署 IOPaint 应用。您可以选择使用 CPU 或 GPU 进行部署。

## 前提条件

- 已安装 Docker (https://docs.docker.com/get-docker/)
- 已安装 Docker Compose (https://docs.docker.com/compose/install/)
- GPU 部署需要:
    - 系统已安装 NVIDIA GPU 驱动。
    - 已安装 NVIDIA Container Toolkit (https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html)

## 服务

`docker-compose.yaml` 文件定义了两个主要服务：

- `cpu`: 使用 `docker/CPUDockerfile` 构建并运行应用。此服务配置为仅使用 CPU 进行推理。
- `gpu`: 使用 `docker/GPUDockerfile` 构建并运行应用。此服务配置为使用 NVIDIA GPU 进行推理。

## 如何部署

### 1. 克隆仓库 (如果尚未克隆)

```bash
git clone https://github.com/Sanster/iopaint.git
cd iopaint
```

### 2. 进入部署目录

```bash
cd deploy
```

### 3. CPU 部署

要仅使用 CPU 构建并运行应用：

```bash
docker-compose up cpu
```

应用将通过 `http://localhost:8080` 访问。

### 4. GPU 部署

要使用 NVIDIA GPU 构建并运行应用：

```bash
docker-compose up gpu
```

应用将通过 `http://localhost:8080` 访问。

**注意：** 首次构建镜像时，下载依赖项和设置环境可能需要一些时间。由于 Docker 的缓存机制，后续构建会更快。

### 停止应用

要在运行 `docker-compose up` 的终端中停止正在运行的服务，请按 `Ctrl+C`，或者在另一个终端的 `deploy` 目录中运行以下命令：

```bash
docker-compose down
```

## 自定义

您可以通过修改 `docker-compose.yaml` 文件或父目录中相应的 Dockerfile（`docker/CPUDockerfile` 和 `docker/GPUDockerfile`）来自定义构建过程或服务配置。
