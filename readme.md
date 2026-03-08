# 📐 System Design Guide

This document explains the basic concepts of **System Design**, including **System Requirements, High Level Design (HLD), and Low Level Design (LLD)**.

---

# 1. System Requirements

System requirements define **what the system should do and how it should behave**.

There are two main types:

```
System Requirements
 ├── Functional Requirements
 └── Non-Functional Requirements
```

---

# 2. Functional Requirements

Functional requirements describe **what features the system should provide**.

Examples:

* User Registration
* Login / Authentication
* Create Post
* Comment on Posts
* Search Content
* Notifications
* Payment Processing

Example (Blog Platform)

```
User → Login
User → Create Post
User → Read Posts
User → Comment
```

These requirements define the **core functionality of the system**.

---

# 3. Non-Functional Requirements

Non-functional requirements define **how well the system performs**.

Examples:

* Scalability
* Reliability
* Security
* Performance
* Maintainability

---

## Latency

Latency is the **time required to complete a single request**.

```
User Request → Server Processing → Response
```

Example:

```
Request Processing Time = 200ms
Latency = 200 milliseconds
```

Lower latency means **faster responses**.

---

## Throughput

Throughput is the **number of requests the system can process in a given time**.

Example:

```
1000 requests per second
5000 requests per minute
```

Higher throughput means the system can **handle more traffic**.

---

## Concurrent Users

Concurrent users are **the number of users using the system at the same time**.

Formula:

```
Concurrent Users =
Peak Requests per Second × Average Session Duration (seconds)
```

Example:

```
Peak Requests per Second = 40
Average Session Duration = 50 seconds

Concurrent Users = 40 × 50
Concurrent Users = 2000
```

So the system must support **2000 simultaneous users**.

---

# 4. High Level Design (HLD)

High Level Design describes the **overall architecture of the system**.

It focuses on:

* Major system components
* Component interactions
* Data flow between services

---

## Architecture Types

### 1. Monolithic Architecture

All components exist in **one single application**.

```
          ┌───────────────┐
          │   Web App     │
          │               │
User ───▶ │ Auth Module   │
          │ Post Module   │
          │ Comment       │
          │ Notification  │
          └───────┬───────┘
                  │
               Database
```

Advantages

* Simple development
* Easy deployment

Disadvantages

* Hard to scale
* Hard to maintain large systems

---

### 2. Microservices Architecture

The system is divided into **multiple independent services**.

```
            ┌─────────────┐
User ─────▶ │ API Gateway │
            └──────┬──────┘
                   │
   ┌───────────────┼───────────────┐
   │               │               │
User Service   Post Service   Comment Service
   │               │               │
   └───────────────┴───────────────┘
           │
        Databases
```

Advantages

* High scalability
* Independent deployment
* Easier maintenance

Disadvantages

* More complex
* Requires service communication

---

### 3. Event Driven Architecture

In this architecture, services communicate through **events**.

Example:

```
User creates post
        │
        ▼
   Event Generated
        │
        ▼
Message Queue (Kafka / RabbitMQ)
        │
        ▼
Notification Service → Sends notification
```

Benefits

* Loose coupling
* Highly scalable
* Asynchronous communication

---

# 5. Low Level Design (LLD)

Low Level Design focuses on the **detailed implementation of each component**.

It includes:

* Class Design
* Database Schema
* API Design
* Technology Stack
* Communication Protocols

---

## Class Design

Example classes for a blog system:

```
User
Post
Comment
Notification
```

Example structure:

```
User
 ├── id
 ├── name
 ├── email
 └── password

Post
 ├── id
 ├── userId
 ├── content
 └── createdAt
```

---

## Database Schema

Example tables:

Users Table

```
id
name
email
password
created_at
```

Posts Table

```
id
user_id
content
created_at
```

Comments Table

```
id
post_id
user_id
comment
created_at
```

---

## API Design

Example REST APIs:

```
POST   /api/register
POST   /api/login

GET    /api/posts
POST   /api/posts
GET    /api/posts/:id

POST   /api/comments
DELETE /api/comments/:id
```

---

## Technology Stack

Example stack for a modern web application.

Frontend

```
React
Next.js
TailwindCSS
```

Backend

```
Node.js
Express.js
```

Database

```
MongoDB
PostgreSQL
```

---

## Communication Protocols

Services communicate using:

* REST API
* GraphQL
* WebSockets
* gRPC
* Message Queues

Example flow:

```
Client → HTTP Request → Backend API
Backend → Database Query → Database
Database → Response → Backend → Client
```

---

# System Design Summary

| Concept                     | Description                    |
| --------------------------- | ------------------------------ |
| Functional Requirements     | What the system should do      |
| Non-Functional Requirements | How the system performs        |
| Latency                     | Time required for a request    |
| Throughput                  | Requests handled per unit time |
| Concurrent Users            | Number of simultaneous users   |
| High Level Design           | Overall system architecture    |
| Low Level Design            | Detailed implementation        |

---

# Conclusion

A good system design ensures:

* Scalability
* Reliability
* Performance
* Maintainability

Understanding **HLD and LLD** helps developers design **large-scale applications like social media platforms, streaming services, and cloud applications**.


<!-- #Software architecture process
1.Requirements
2.Design
3.Evaluation
4.Documentation
5.Implementation -->

<!-- 
##System Requirements##
Two types:
1.Functional Requirement
2.Non-functional requirements

**Latency**
Time to complete single task
**Throughput**
Total tasks completed per second/minute

**Concurrent user*
How many users can use the system simultaneously

concurrent user=Peak Request per second * Avg.Session Duration in seconds

*High Level Design*
#System's structure identifying major components and their interaction
#Monolithic#
#microservices#
*Evenet driven
*Low Level Design*
*implementation of each component, including class diagrams,database schema and api specifications*
*Stack ,data models,communication protocols,other architectural elements* -->

