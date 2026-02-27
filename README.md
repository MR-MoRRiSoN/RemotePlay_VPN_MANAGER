# RemotePlay VPN Manager

> A custom REST API for managing WireGuard VPN configurations — built with Spring Boot.

[![Java](https://img.shields.io/badge/Java-Spring%20Boot-6DB33F?style=for-the-badge&logo=spring)](https://spring.io/projects/spring-boot)
[![WireGuard](https://img.shields.io/badge/WireGuard-VPN-88171A?style=for-the-badge&logo=wireguard)](https://www.wireguard.com)
[![Maven](https://img.shields.io/badge/Maven-Build-C71A36?style=for-the-badge&logo=apache-maven)](https://maven.apache.org)

---

## 📋 About

**RemotePlay VPN Manager** is a Spring Boot-based backend application that provides a custom REST API layer on top of WireGuard. It allows programmatic management of VPN peers, tunnels, and configurations — eliminating the need for manual CLI interaction with WireGuard.

---

## ✨ Features

- 🔐 **WireGuard Integration** — manage peers, keys, and tunnel configs via REST API
- 👤 **Role-based access control** — admin authentication & authorization
- ⚙️ **System-level command execution** — interacts with WireGuard CLI under the hood
- 🌐 **RESTful API** — clean endpoints for VPN lifecycle management
- 🔒 **Secure by design** — credentials managed via environment variables

---

## 🛠 Tech Stack

| Technology | Usage |
|---|---|
| **Java** | Core language |
| **Spring Boot** | REST API framework |
| **Spring Security** | Authentication & role management |
| **WireGuard** | VPN protocol & tunnel management |
| **Maven** | Build & dependency management |

---

## 🚀 Getting Started

### Prerequisites

- Java 17+
- Maven 3.8+
- WireGuard installed on the server (`apt install wireguard`)
- Linux environment (Ubuntu recommended)

### Installation

```bash
# Clone the repository
git clone https://github.com/MR-MoRRiSoN/RemotePlay_VPN_MANAGER.git

cd RemotePlay_VPN_MANAGER
```

### Configuration

Create your `application.properties` based on the example below:

```properties
spring.application.name=VpnManager
spring.application.app-manager-user=${APP_MANAGER_USER}
spring.application.app-manager-passwd=${APP_MANAGER_PASSWD}
spring.application.app-manager-role=${APP_MANAGER_ROLE}
ubuntu.sudo.password=${UBUNTU_SUDO_PASSWORD}
server.port=8000
```

Set environment variables before running:

```bash
export APP_MANAGER_USER=your_username
export APP_MANAGER_PASSWD=your_password
export APP_MANAGER_ROLE=ADMINISTRATOR
export UBUNTU_SUDO_PASSWORD=your_sudo_password
```

### Run

```bash
./mvnw spring-boot:run
```

API will be available at `http://localhost:8000`

---

## 📡 API Overview

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/api/peers` | List all WireGuard peers |
| `POST` | `/api/peers` | Add a new peer |
| `DELETE` | `/api/peers/{id}` | Remove a peer |
| `GET` | `/api/status` | WireGuard tunnel status |

> Endpoints may vary — see source for full API documentation.

---

## 🔒 Security

This application uses role-based authentication. All sensitive credentials must be provided via environment variables — **never hardcode credentials in `application.properties`**.

For CI/CD pipelines, use GitHub Actions Secrets to inject environment variables at build/deploy time.

---

## 📄 License

This project is proprietary. All rights reserved © 2026 RemotePlay.
