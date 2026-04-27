# CI/CD Pipeline with Docker & AWS EC2 Deployment
[![LinkedIn](https://img.shields.io/badge/Connect%20with%20me%20on-LinkedIn-blue.svg)](https://www.linkedin.com/in/aman-devops/)
[![YouTube](https://img.shields.io/badge/Video%20On%20-YouTube-red.svg)](https://www.youtube.com/@aman-pathak)
[![GitHub](https://img.shields.io/github/stars/AmanPathak-DevOps.svg?style=social)](https://github.com/AmanPathak-DevOps)
[![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white)](https://hub.docker.com/u/avian19)

![Architecture](assets/Infra.gif)

Bu proje, bir uygulamanın Docker + GitHub Actions ile otomatik olarak AWS EC2 sunucusuna deploy edilmesini sağlar.

## ✨ Highlights
⚡ Auto Deploy: git push → otomatik deploy
🐳 Dockerized App
☁️ AWS EC2 üzerinde canlı sistem
🔐 SSH ile güvenli bağlantı
🔁 CI/CD pipeline (end-to-end)

## 🏗️ Architecture
Developer → GitHub → GitHub Actions → SSH → AWS EC2 → Docker → App 🚀

## ☁️ Infrastructure
Cloud Provider: AWS
Compute: EC2 (Ubuntu Server)
Deployment: SSH + Docker Compose

## ⚙️ CI/CD Workflow
Developer kodu GitHub’a push eder
GitHub Actions pipeline tetiklenir
Pipeline:
Sunucuya SSH ile bağlanır
Repo günceller (git pull)
Docker container rebuild eder
Uygulamayı ayağa kaldırır
