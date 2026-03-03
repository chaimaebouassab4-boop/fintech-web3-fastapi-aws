<div align="center">

# 🏦 FinTech Web3 Platform
### Microservices · Blockchain · FastAPI · AWS

[![Python](https://img.shields.io/badge/Python-3.11+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.100+-009688?style=for-the-badge&logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com)
[![Angular](https://img.shields.io/badge/Angular-17+-DD0031?style=for-the-badge&logo=angular&logoColor=white)](https://angular.io)
[![Ethereum](https://img.shields.io/badge/Ethereum-Sepolia-3C3C3D?style=for-the-badge&logo=ethereum&logoColor=white)](https://ethereum.org)
[![AWS](https://img.shields.io/badge/AWS-EKS%20%7C%20EC2%20%7C%20RDS-FF9900?style=for-the-badge&logo=amazonaws&logoColor=white)](https://aws.amazon.com)
[![Docker](https://img.shields.io/badge/Docker-Enabled-2496ED?style=for-the-badge&logo=docker&logoColor=white)](https://docker.com)
[![License](https://img.shields.io/badge/License-MIT-22c55e?style=for-the-badge)](LICENSE)

<br/>

> A **production-grade FinTech platform** combining microservices architecture, Ethereum blockchain, and advanced data analytics — deployed on AWS with full CI/CD automation.

<br/>

[🚀 Quick Start](#-quick-start) · [🏗️ Architecture](#️-architecture) · [📡 API Docs](#-api-reference) · [🔗 Blockchain](#-blockchain-integration) · [📊 Analytics](#-data-analytics)

</div>

---

## ✨ Key Features

| Feature | Description |
|---|---|
| 🔐 **Secure Auth** | JWT + OAuth2 with role-based access control |
| ⛓️ **Blockchain** | Smart contracts on Ethereum Sepolia Testnet via Solidity & Web3.py |
| 💳 **Transactions** | Full lifecycle management for traditional & crypto payments |
| 📈 **Analytics** | Real-time dashboards with candlestick charts & trend analysis |
| ☁️ **Cloud-Native** | Auto-scaling on AWS EKS with Terraform-managed infrastructure |
| 🔄 **CI/CD** | Automated pipelines via Jenkins + Docker + Kubernetes |
| 📡 **Monitoring** | Prometheus, Grafana & AWS CloudWatch observability |

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                        Angular SPA                          │
│              (MetaMask · Web3.js · Dashboard)               │
└───────────────────────┬─────────────────────────────────────┘
                        │ REST / WebSocket
              ┌─────────▼──────────┐
              │    API Gateway     │  ← JWT / OAuth2
              └──────┬──────┬──────┘
        ┌────────────┘      └────────────┐
        │                               │
┌───────▼────────┐             ┌────────▼────────┐
│  User Service  │             │ Transaction Svc │
│  (FastAPI)     │             │   (FastAPI)     │
└───────┬────────┘             └────────┬────────┘
        │                               │
┌───────▼────────┐             ┌────────▼────────┐
│  Blockchain    │             │  Analytics Svc  │
│  Service       │             │  (Pandas/Plotly)│
│  (Web3.py)     │             └─────────────────┘
└───────┬────────┘
        │
┌───────▼──────────────┐
│  Ethereum Sepolia     │
│  (Solidity Contracts) │
└──────────────────────┘
```

### Microservices

| Service | Responsibility | Tech |
|---|---|---|
| **User Management** | Auth, wallets, account CRUD | FastAPI, JWT, SQLAlchemy |
| **Transaction Service** | Payment processing, history | FastAPI, PostgreSQL |
| **Blockchain Service** | Smart contracts, on-chain txns | Web3.py, Solidity, MetaMask |
| **Analytics Service** | Insights, dashboards, reports | Pandas, Plotly, Seaborn |

---

## 🛠️ Tech Stack

<details>
<summary><strong>Backend</strong></summary>

- **Framework**: FastAPI + Uvicorn
- **ORM**: SQLAlchemy
- **Database**: PostgreSQL (AWS RDS)
- **Auth**: JWT, OAuth2, bcrypt

</details>

<details>
<summary><strong>Blockchain</strong></summary>

- **Smart Contracts**: Solidity (ERC-20, payable, staking)
- **Network**: Ethereum Sepolia Testnet
- **Integration**: Web3.py, Infura
- **Wallet**: MetaMask

</details>

<details>
<summary><strong>Frontend</strong></summary>

- **Framework**: Angular 17 (SPA)
- **Wallet UI**: MetaMask integration
- **Charts**: Plotly, Seaborn

</details>

<details>
<summary><strong>DevOps & Cloud</strong></summary>

- **Containers**: Docker, Docker Compose
- **Orchestration**: Kubernetes (AWS EKS)
- **IaC**: Terraform
- **CI/CD**: Jenkins
- **Cloud**: AWS EC2, RDS, S3, CloudWatch
- **Monitoring**: Prometheus, Grafana

</details>

---

## 🚀 Quick Start

### Prerequisites

- Docker & Docker Compose
- Node.js 18+
- Python 3.11+
- MetaMask browser extension
- AWS CLI (for cloud deployment)

### 1. Clone the Repository

```bash
git clone https://github.com/chaimaebouassab4-boop/fintech-web3-fastapi-aws.git
cd fintech-web3-fastapi-aws
```

### 2. Configure Environment

```bash
cp .env.example .env
```

Edit `.env` with your credentials:

```env
# Database
DATABASE_URL=postgresql://user:password@localhost:5432/fintech_db

# Security
SECRET_KEY=your-256-bit-secret-key
ALGORITHM=HS256
ACCESS_TOKEN_EXPIRE_MINUTES=30

# Blockchain
INFURA_PROJECT_ID=your-infura-project-id
CONTRACT_ADDRESS=your-deployed-contract-address
ETHEREUM_NETWORK=sepolia

# AWS (optional for local dev)
AWS_ACCESS_KEY_ID=your-key
AWS_SECRET_ACCESS_KEY=your-secret
AWS_REGION=eu-west-1
```

### 3. Launch All Services

```bash
docker-compose up --build
```

| Service | URL |
|---|---|
| 🌐 Frontend | http://localhost |
| 📡 API Docs (Swagger) | http://localhost:8000/docs |
| 📊 Grafana Dashboard | http://localhost:3000 |
| 🗄️ PostgreSQL | localhost:5432 |

---

## 📡 API Reference

### Authentication

```http
POST /register          # Create a new user account
POST /token             # Obtain JWT access token
```

### User & Wallet Management

```http
GET    /users/me                      # Get current user profile
POST   /users/{username}/wallets      # Create a new crypto wallet
GET    /users/{username}/wallets      # List all wallets
```

### Transactions

```http
POST   /transactions                  # Submit a new transaction
GET    /transactions/{id}             # Get transaction details
GET    /transactions/history          # Full transaction history
```

### Blockchain

```http
POST   /blockchain/deploy             # Deploy smart contract
POST   /blockchain/send               # Send ETH via contract
GET    /blockchain/balance/{address}  # Get on-chain wallet balance
```

> 📘 Full interactive docs available at `http://localhost:8000/docs`

---

## 🔗 Blockchain Integration

### Smart Contract (Solidity)

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract FinTechPayments {
    address public owner;

    constructor() { owner = msg.sender; }

    receive() external payable {}

    function withdraw(uint256 amount) external {
        require(msg.sender == owner, "Unauthorized");
        payable(owner).transfer(amount);
    }

    function getBalance() external view returns (uint256) {
        return address(this).balance;
    }
}
```

### Deployment

The contract is deployed and verified on **Ethereum Sepolia Testnet** via Etherscan. Users connect via **MetaMask** to sign and submit transactions directly from the browser.

---

## 📊 Data Analytics

Powered by the **CoinGecko API**, the analytics service generates:

- 📉 **Candlestick Charts** — OHLC price data per asset
- 📊 **Volume Graphs** — Transaction volume over time
- 📈 **Closing Price Trends** — Historical price curves
- 🔢 **Log-Scale Price Graphs** — Normalized for volatility comparison

Libraries used: `Pandas` · `NumPy` · `Plotly` · `Seaborn`

---

## ☁️ Cloud Deployment (AWS)

```bash
# 1. Provision infrastructure with Terraform
cd infra/terraform
terraform init && terraform apply

# 2. Build & push Docker images
docker build -t fintech-api ./backend
docker tag fintech-api:latest <ECR_URI>/fintech-api:latest
docker push <ECR_URI>/fintech-api:latest

# 3. Deploy to EKS
kubectl apply -f k8s/
kubectl get pods -n fintech
```

**AWS Services Used:**

| Service | Purpose |
|---|---|
| **EKS** | Kubernetes cluster for microservices |
| **RDS (PostgreSQL)** | Managed relational database |
| **S3** | Static assets & Terraform state |
| **EC2** | Worker nodes |
| **CloudWatch** | Logs & alerting |
| **IAM** | Secure access management |

---

## 🔄 CI/CD Pipeline

```
[Git Push] → [Jenkins Trigger]
               ├── Lint & Unit Tests
               ├── Docker Build
               ├── Push to ECR
               └── Deploy to EKS (kubectl apply)
```

---

## 📁 Project Structure

```
fintech-web3-fastapi-aws/
├── backend/
│   ├── user_service/
│   │   ├── database/main.py        # DB initialization
│   │   ├── user/model.py           # SQLAlchemy models
│   │   ├── user/repository.py      # DB operations
│   │   ├── user/services.py        # Business logic
│   │   ├── user/routes.py          # API endpoints
│   │   ├── utils/auth.py           # JWT utilities
│   │   └── config.py               # Environment config
│   ├── transaction_service/
│   ├── blockchain_service/
│   └── analytics_service/
├── frontend/                        # Angular SPA
├── contracts/                       # Solidity smart contracts
├── infra/
│   ├── terraform/                   # AWS infrastructure
│   ├── k8s/                         # Kubernetes manifests
│   └── jenkins/                     # CI/CD pipeline config
├── docker-compose.yml
├── .env.example
└── README.md
```

---

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create your feature branch: `git checkout -b feature/amazing-feature`
3. Commit your changes: `git commit -m 'feat: add amazing feature'`
4. Push to the branch: `git push origin feature/amazing-feature`
5. Open a Pull Request

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

<div align="center">

Made with ❤️ by **chaimaebouassab4**

⭐ Star this repo if you found it helpful!

</div>
