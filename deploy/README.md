# Docker Compose Deployment for IOPaint

This directory contains the `docker-compose.yaml` file to deploy the IOPaint application using Docker Compose. You can deploy the application using either CPU or GPU.

## Prerequisites

- Docker installed (https://docs.docker.com/get-docker/)
- Docker Compose installed (https://docs.docker.com/compose/install/)
- For GPU deployment:
    - NVIDIA GPU drivers installed on your system.
    - NVIDIA Container Toolkit installed (https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html)

## Services

The `docker-compose.yaml` defines two main services:

- `cpu`: Builds and runs the application using the `docker/CPUDockerfile`. This service is configured for CPU-only inference.
- `gpu`: Builds and runs the application using the `docker/GPUDockerfile`. This service is configured to use an NVIDIA GPU for inference.

## How to Deploy

### 1. Clone the Repository (if you haven't already)

```bash
git clone https://github.com/Sanster/iopaint.git
cd iopaint
```

### 2. Navigate to the Deployment Directory

```bash
cd deploy
```

### 3. CPU Deployment

To build and run the application using only the CPU:

```bash
docker-compose up cpu
```

The application will be accessible at `http://localhost:8080`.

### 4. GPU Deployment

To build and run the application using an NVIDIA GPU:

```bash
docker-compose up gpu
```

The application will be accessible at `http://localhost:8080`.

**Note:** The first time you build the images, it might take a while to download dependencies and set up the environment. Subsequent builds will be faster due to Docker's caching mechanism.

### Stopping the Application

To stop the running services, press `Ctrl+C` in the terminal where `docker-compose up` is running, or run the following command from the `deploy` directory in another terminal:

```bash
docker-compose down
```

## Customization

You can customize the build process or service configurations by modifying the `docker-compose.yaml` file or the respective Dockerfiles (`docker/CPUDockerfile` and `docker/GPUDockerfile`) in the parent directory.
