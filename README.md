# 🧠 Text Summarizer API

![FastAPI](https://img.shields.io/badge/framework-FastAPI-green)
![Docker](https://img.shields.io/badge/container-docker-blue)
![Kubernetes](https://img.shields.io/badge/deployment-kubernetes-success)
![Transformers](https://img.shields.io/badge/model-HuggingFace-orange)

This project demonstrates how to:
- Load a Hugging Face summarization model
- Serve it via a FastAPI REST API
- Package the app in a Docker container
- Deploy it using Kubernetes with autoscaling

## 🔧 Features
- Model: `sshleifer/distilbart-cnn-12-6`
- Endpoint: `POST /summarize`
- Input: Raw text, Output: Summary

## 🚀 Getting Started

### 📦 Local Docker
```bash
docker build -t summarizer-api .
docker run -p 8000:8000 summarizer-api
```
Access: http://localhost:8000/docs

### ☸️ Kubernetes
Apply manifests:
```bash
kubectl apply -f kubernetes/deployment.yaml
kubectl apply -f kubernetes/service.yaml
kubectl apply -f kubernetes/hpa.yaml
```

Get external IP:
```bash
kubectl get svc summarizer-api-service
```
Then test:
```bash
curl -X POST http://<EXTERNAL-IP>/summarize \
  -H "Content-Type: application/json" \
  -d '{"text": "Your text here..."}'
```

## 📄 License
MIT
