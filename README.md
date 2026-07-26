Build Your Own Distributed Cloud Platform (Mini AWS)
This is the kind of project that immediately signals elite engineering ability.
Imagine building:
CloudX
Users
   │
   ▼
API Gateway
   │
───────────────
Authentication Service
Scheduling Service
Container Service
Storage Service
Load Balancer
Monitoring
Logging
Database
Queue
────────────────
Worker Nodes
Users can:
Deploy Docker containers
Upload applications
Autoscale services
View logs
Restart crashed services
Monitor CPU/RAM
Use load balancing
Store files
Authenticate
Use REST APIs
It looks like a tiny version of AWS/GCP.
Tech Stack
Backend
Go (preferred)
Rust (bonus)
Java (excellent)
Frontend
Next.js
React
Tailwind
Database
PostgreSQL
Redis
Infrastructure
Docker
Kubernetes
Nginx
Prometheus
Grafana
Communication
gRPC
REST
WebSockets
Cloud
AWS EC2
Terraform
CI/CD
GitHub Actions
Features
1. Authentication
JWT
Refresh Tokens
RBAC
OAuth Login
2. Deploy Containers
User uploads Docker image
↓
Scheduler picks node
↓
Runs container
↓
Returns URL
3. Health Monitoring
Heartbeat
Auto restart
Crash recovery
4. Autoscaling
CPU > 70%
↓
Create new container
↓
Update load balancer
5. Metrics
CPU
RAM
Requests/sec
Latency
6. Logging
Centralized logs
Search
Filtering
7. Distributed Storage
Upload files
Replicate
Serve
8. Reverse Proxy
Nginx
Rate limiting
TLS
9. Queue
RabbitMQ
Kafka
Background jobs
10. Dashboard
Realtime graphs
Deployment status
Logs
Metrics
