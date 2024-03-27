## Products Monitoring

This is a script to consume orders from a queue.

### Stack used
- Go 1.19
- RabbitMQ
- Docker
- Docker Compose
- Grafana
- Prometheus
- Kubernetes

### How to run
Run the following command to start the application:
```bash
docker-compose up
```
This will start the RabbitMQ server, Prometheus monitoring and Grafana dashboard.

Run the producer to send messages to the queue:
```bash
go run cmd/producer/main.go
```

Run the consumer to consume messages from the queue:
```bash
go run cmd/consumer/main.go
```

Build the Dockerfile.prod
```bash
docker build -t cerebrovinny/products_monitor:latest -f Dockerfile.prod .
```

### How to run in Kubernetes
Run the following command to start the application:
```bash
kind create cluster --name=products_monitor
kubectl apply -f k8s
```

Check the deployment configuration
```bash
kubectl get deployments
```

Remember to access the deployment on Kubernetes, you need to change the domain for the RabbitMQ 
currently is running in localhost
