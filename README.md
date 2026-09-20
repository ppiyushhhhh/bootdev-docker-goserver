# GoServer: Dockerized HTTP Web Server

[![Docker Image Version](https://img.shields.io/badge/docker%20image-0.2.0-blue)](https://hub.docker.com/r/ppiyushhhh/goserver)
[![Go Version](https://img.shields.io/badge/go-1.20%2B-00ADD8?logo=go)](https://golang.org)
[![Docker](https://img.shields.io/badge/docker-ready-2496ED?logo=docker)](https://www.docker.com/)
[![License: MIT](https://img.shields.io/badge/license-MIT-green)](#license)

A lightweight, containerized Go HTTP web server built for fast deployment with Docker. Designed around cross-compilation and a minimal runtime footprint.

---

## Table of Contents

- [Features](#features)
- [Prerequisites](#prerequisites)
- [Quick Start with Docker](#quick-start-with-docker)
- [Configuration](#configuration)
- [Building and Running Locally](#building-and-running-locally)
- [Repository Structure](#repository-structure)
- [Docker Hub Versions](#docker-hub-versions)
- [Certification](#certification)
- [License](#license)
- [Author](#author)

---

## Features

- **Lightweight footprint**: runs on a trimmed Debian Linux base image.
- **Configurable port**: binds dynamically through the `PORT` environment variable.
- **Cross-compiled binary**: native Linux `amd64` executable produced with Go's built-in toolchain.
- **Registry ready**: published and versioned on [Docker Hub](https://hub.docker.com/r/ppiyushhhh/goserver).

---

## Prerequisites

- [Docker](https://docs.docker.com/get-docker/) installed locally
- [Go](https://go.dev/doc/install) 1.20 or newer (only required if you build without Docker)

---

## Quick Start with Docker

Pull and run the pre-built image from Docker Hub. No local compilation needed.

```bash
# Pull version 0.2.0
docker pull ppiyushhhh/goserver:0.2.0

# Run the container, mapping host port 8991 to container port 8991
docker run -d -p 8991:8991 ppiyushhhh/goserver:0.2.0
```

Verify the server is running by opening <http://localhost:8991> or running:

```bash
curl http://localhost:8991/
```

**Expected response:**

```html
<html>
<head></head>
<body>
	<p> Hi Docker, I pushed a new version. </p>
</body>
</html>
```

---

## Configuration

| Variable | Description                          | Example |
| -------- | ------------------------------------ | ------- |
| `PORT`   | Port the HTTP server listens on      | `8991`  |

To run on a different port, pass `PORT` and map it accordingly:

```bash
docker run -d -e PORT=9000 -p 9000:9000 ppiyushhhh/goserver:0.2.0
```

---

## Building and Running Locally

To modify the source and build the image yourself:

**1. Clone the repository**

```bash
git clone https://github.com/ppiyushhhhh/docker-goserver.git
cd docker-goserver
```

**2. Compile the Go executable**

Cross-compile for Linux on AMD64:

```bash
GOOS=linux GOARCH=amd64 go build -o goserver
```

**3. Build the Docker image**

```bash
docker build -t ppiyushhhh/goserver:0.2.0 .
```

**4. Run the container**

```bash
docker run -d -p 8991:8991 ppiyushhhh/goserver:0.2.0
```

---

## Repository Structure

```
.
├── Dockerfile          # Containerizes the Go binary
├── .dockerignore       # Files excluded from the Docker build context
├── .gitignore          # Files excluded from Git (binaries, system files)
├── go.mod              # Go module definition
├── main.go             # Application entrypoint and HTTP router
└── README.md           # Project documentation
```

---

## Docker Hub Versions

| Tag      | Status   | Description                        |
| -------- | -------- | ---------------------------------- |
| `latest` | Released | Baseline Go HTTP server build      |
| `0.2.0`  | Active   | Updated endpoint message release   |

---

## Certification

Completed the **Learn Docker** course on Boot.dev.

<a href="https://www.boot.dev/certificates/7f95769a-a178-48bc-a164-ce336f8aad6e">
  <img src="https://qvault-webapp-dynamic-assets.storage.googleapis.com/certificates/7f95769a-a178-48bc-a164-ce336f8aad6e.jpeg?v=1789927305" alt="Boot.dev Learn Docker certificate" width="450" />
</a>

---

## License

This project is open source and available under the [MIT License](LICENSE).

---

## Author

**Piyush Prasad**, Cloud & DevOps Engineer

- GitHub: [@ppiyushhhhh](https://github.com/ppiyushhhhh)
- LinkedIn: [linkedin.com/in/ppiyushhhh](https://linkedin.com/in/ppiyushhhh)
- Portfolio: [piyushprasad.in](https://piyushprasad.in)
