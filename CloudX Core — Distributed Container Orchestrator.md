I would not try to finish an entire Cloud Run in one month. You'll either rush it or leave it half-finished.

Instead, build the core orchestration engine. It is much smaller but retains almost all of the engineering value.

Project
CloudX Core — Distributed Container Orchestrator

Think of this as:

Kubernetes Scheduler + Worker + Health Monitor

without autoscaling, logging, Prometheus, Grafana, CI/CD, etc.

Scope
          User

            │

            ▼

      Deployment API

            │

            ▼

       Scheduler

            │

   ┌────────┴────────┐

   ▼                 ▼

Worker 1         Worker 2

   │                 │

 Docker           Docker

   │                 │

Containers      Containers

This is already an impressive systems project.

Week 1
Build Worker Node

Worker exposes

POST /deploy

POST /stop

POST /restart

GET /status

Internally

docker pull

↓

docker run

↓

docker stop

↓

docker rm

Worker also

tracks containers
monitors status
reports CPU
reports RAM
Learn
Docker SDK
REST/gRPC
Go concurrency
Week 2
Build Scheduler

Maintain

Worker

CPU

RAM

Alive

Containers

Implement

Round Robin
Least CPU
Weighted Score

When deployment comes

Scheduler

↓

Choose worker

↓

Call Worker API
Nice optimization

Resource reservation

Worker CPU

30%

↓

Deployment arrives

↓

Reserve CPU

↓

Another deployment

↓

Worker now appears

45%

↓

Avoid overload

Interviewers love discussing this kind of race condition.

Week 3
Heartbeat + Failure Recovery

Every worker

every 5 seconds

↓

Heartbeat

Scheduler

No heartbeat

10 seconds

↓

Worker dead

Now

Worker dies

↓

Container lost

↓

Redeploy somewhere else

This is a genuine distributed systems feature.

Week 4
Dashboard

Show

Workers
CPU
RAM
Running containers
Deployments
Logs (basic)

Use

React
Tailwind

No fancy UI needed.

Final Architecture
             User

               │

               ▼

        Deployment API

               │

               ▼

          Scheduler

       ┌───────┴────────┐

       ▼                ▼

 Worker 1          Worker 2

       │                │

 Docker           Docker

       │                │

 Containers     Containers

       ▲                ▲

       └──── Heartbeats ─┘
Features

✅ Deploy Docker containers

✅ Scheduler

✅ Multiple workers

✅ Health monitoring

✅ Crash detection

✅ Automatic redeployment

✅ Resource-aware scheduling

✅ Dashboard

Things NOT to build

Don't spend time on

❌ Kubernetes

❌ Terraform

❌ Kafka

❌ RabbitMQ

❌ Prometheus

❌ Grafana

❌ OAuth

❌ CI/CD

❌ Distributed storage

❌ Autoscaling

❌ Nginx

These are excellent additions later, but they don't maximize interview impact within one month.

Why this is impressive

An interviewer will immediately have technical questions like:

Why did you choose weighted scheduling?
How do workers communicate?
How do you detect failures?
What happens if a deployment fails halfway?
How do you prevent two schedulers choosing the same worker?
How would you add autoscaling?
How would you support rolling updates?

Those are the kinds of discussions that showcase engineering thinking.

Resume Bullet

Built CloudX Core, a distributed container orchestration platform in Go that schedules Docker containers across multiple worker nodes using resource-aware scheduling, heartbeat-based failure detection, automatic container recovery, and a real-time monitoring dashboard.

Overall Rating
Metric	Score
Interview Impression	10/10
Uniqueness	9.8/10
Engineering Depth	10/10
Real-world Relevance	10/10
Feasible in 1 Month	9/10
