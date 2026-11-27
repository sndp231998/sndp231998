# Hi, I'm Sandip Chapagain 👋

**Backend & DevOps engineer for startups.** I design, build and run production systems end to end: Java/Spring Boot microservices, event-driven architecture, Kubernetes, and Flutter mobile apps.

CTO of **Tufan** (ride-sharing, Nepal) · CTO of **KRYZOX**, **GigFine** and **GigsRentals** · Founder of **[A1 IT Innovation](https://www.a1itinnovation.com.np)**

📍 Kathmandu, Nepal · 🌍 Working remotely with teams worldwide

---

## 🚀 What I've built (in production)

| Product | What it is | My role |
|---|---|---|
| **Tufan** | Ride-sharing & delivery: car, comfort, bike, scheduled rides, cargo and parcel, free in-app calls, smart safety system | CTO: architecture, backend, infra, Flutter apps |
| **KRYZOX** | Esports tournament platform for PUBG Mobile, BGMI and Free Fire with entry fees and prize money | CTO |
| **GigFine** | Platform to report problems with ride-sharing and delivery apps in Nepal | CTO |
| **GigsRentals** | Rental marketplace for cars, bikes and houses | CTO |
| **T-Meet** | White-label video conferencing for online classes and meetings | Built and deployed |
| **A1 Scanner** | Offline document scanner app | Product owner |

## 🏗️ System design: real-time ride dispatch (Tufan)

```mermaid
flowchart LR
    A[Rider / Driver apps<br/>Flutter] -->|REST + WebSocket| G[API Gateway<br/>Spring Cloud Gateway + JWT]
    G --> U[User Service]
    G --> R[Ride Request Service]
    G --> P[Payment Service<br/>Khalti / eSewa]
    U -->|live location| RD[(Redis GEO)]
    R -->|find riders within 3 km| RD
    R -->|ride events| K[[Kafka]]
    K -->|replay on reconnect| R
    R -->|instant offers| MQ[[RabbitMQ STOMP]]
    MQ -->|push| A
```

- **Redis GEO** keeps live rider locations, so nearby riders are found in milliseconds
- **Kafka** stores ride events durably; a rider who lost network gets the offer again on reconnect
- **RabbitMQ (STOMP/WebSocket)** pushes offers instantly; once one rider accepts, the offer is cleared for everyone else
- **Self-hosted maps** (OSRM, Nominatim, Valhalla) with zero-downtime blue-green data refresh

## ⚙️ How I ship

- **Kubernetes** on VPS (kubeadm, containerd, Flannel), multi-node, one cluster per product
- **GitOps** with ArgoCD · **CI/CD** with Jenkins (cut deploy time from ~30 min to ~3 min)
- **Observability** with Prometheus, Grafana and Loki
- **Edge**: Cloudflare, cert-manager, Nginx

## 🧰 Stack

![Java](https://img.shields.io/badge/Java-ED8B00?style=flat-square&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-6DB33F?style=flat-square&logo=springboot&logoColor=white)
![Kafka](https://img.shields.io/badge/Apache_Kafka-231F20?style=flat-square&logo=apachekafka&logoColor=white)
![RabbitMQ](https://img.shields.io/badge/RabbitMQ-FF6600?style=flat-square&logo=rabbitmq&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=flat-square&logo=kubernetes&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Argo CD](https://img.shields.io/badge/Argo_CD-EF7B4D?style=flat-square&logo=argo&logoColor=white)
![Jenkins](https://img.shields.io/badge/Jenkins-D24939?style=flat-square&logo=jenkins&logoColor=white)
![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=flat-square&logo=prometheus&logoColor=white)
![Grafana](https://img.shields.io/badge/Grafana-F46800?style=flat-square&logo=grafana&logoColor=white)
![Flutter](https://img.shields.io/badge/Flutter-02569B?style=flat-square&logo=flutter&logoColor=white)
![React](https://img.shields.io/badge/React-20232A?style=flat-square&logo=react&logoColor=61DAFB)

## 🤝 Work with me

I help startups and product teams to:

- Build or scale a **Spring Boot / microservices backend**
- Set up or fix **Kubernetes, Docker and CI/CD**
- Build **cross-platform mobile apps** with Flutter
- Launch a **white-label ride-sharing, delivery or video-conferencing platform** in weeks, not months

Most client code is private, so I'm happy to walk you through architecture and live demos on a call.

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/sandip-chapagain)
[![Website](https://img.shields.io/badge/a1itinnovation.com.np-4F46E5?style=for-the-badge&logo=googlechrome&logoColor=white)](https://www.a1itinnovation.com.np)
[![Email](https://img.shields.io/badge/info@a1itinnovation.com.np-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:info@a1itinnovation.com.np)
