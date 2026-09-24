# System Design – Introduction

## 1. What is System Design?

System Design is the process of designing the architecture, components, data flow, and interactions of a software system to satisfy its requirements.

In simple words:

> System Design is about deciding how different parts of a software system will work together to solve a problem.

When building a real-world application, we don't only think about writing code. We also need to decide:

- How many servers are needed?
- Which database should be used?
- How will users communicate with the application?
- How will different services communicate?
- How will the system handle millions of users?
- What happens if a server fails?
- How can we make the system faster?
- How do we protect user data?

All of these decisions are part of System Design.

---

## 2. Why Do We Need System Design?

A simple application may work perfectly when there are only a few users.

For example:

    Users
      |
      v
    Server
      |
      v
    Database

This may work for a small application.

But imagine the application becomes popular:

    100 Users
        |
        v
    10,000 Users
        |
        v
    1,00,000 Users
        |
        v
    10,00,000 Users

Now a single server may not be enough.

The system can become:

- Slow
- Unavailable
- Difficult to maintain
- Expensive
- Vulnerable to failures

System Design helps us build systems that can handle increasing users, traffic, and data.

---

## 3. Example of System Design

Consider an E-Commerce application.

The application should allow users to:

- Register
- Login
- Search products
- View products
- Add products to cart
- Place orders
- Make payments
- Track orders

A simple high-level architecture could look like:

    Users
      |
      v
    Load Balancer
      |
      +-------------------+
      |                   |
      v                   v
    Server 1            Server 2
      |                   |
      +---------+---------+
                |
                v
             Database

As the system grows, we may introduce additional components:

    Users
      |
      v
    Load Balancer
      |
      v
    Backend Servers
      |
      +---------> Redis Cache
      |
      +---------> Database
      |
      +---------> Message Queue
      |
      +---------> External Services

The System Designer decides how these components should work together.

---

## 4. What Does a System Designer Do?

A System Designer makes decisions about the structure and behavior of a system.

Some important questions are:

1. What problem are we solving?
2. What are the system requirements?
3. How many users will use the system?
4. How much traffic will the system receive?
5. How much data will we store?
6. Which database should we use?
7. Do we need caching?
8. Do we need a load balancer?
9. How should services communicate?
10. What happens if a component fails?
11. How can the system scale?
12. How do we secure the system?
13. How much will the system cost?
14. What trade-offs are we making?

---

# 5. Main Areas of System Design

System Design is commonly divided into two major areas:

- High-Level Design (HLD)
- Low-Level Design (LLD)

---

## 5.1 High-Level Design (HLD)

High-Level Design focuses on the overall architecture of the system.

It describes the major components and how they communicate.

Common HLD components include:

- Clients
- Servers
- APIs
- Load Balancers
- Databases
- Caches
- Message Queues
- API Gateways
- Microservices
- External Services

Example:

    Client
      |
      v
    API Gateway
      |
      v
    Load Balancer
      |
      v
    Backend Services
      |
      +-------> Redis
      |
      +-------> Database
      |
      +-------> Message Queue

HLD answers:

> "How should the entire system be structured?"

---

## 5.2 Low-Level Design (LLD)

Low-Level Design focuses on the internal implementation of individual components.

LLD deals with:

- Classes
- Objects
- Interfaces
- Methods
- Relationships
- Design Patterns
- SOLID Principles

For example, a payment component may contain a class such as:

    class Payment {
        void pay() {
            // payment logic
        }
    }

LLD answers:

> "How should the individual components and classes be designed?"

---

# 6. HLD vs LLD

| HLD | LLD |
|---|---|
| Overall architecture | Internal implementation |
| System-level design | Code-level design |
| Services | Classes and objects |
| Databases | Methods |
| Load Balancers | Interfaces |
| Caching | Design Patterns |
| Message Queues | SOLID Principles |
| Scalability | Object relationships |

### Easy Way to Remember

> HLD = Big Picture

> LLD = Code-Level Details

---

# 7. Important Characteristics of a Good System

A good system design should consider several important properties.

## 7.1 Scalability

Scalability is the ability of a system to handle increasing users, traffic, or data.

For example:

    1,000 Users
        |
        v
    1,00,000 Users
        |
        v
    1 Crore Users

A scalable system should be able to grow without completely redesigning the application.

---

## 7.2 Availability

Availability refers to how often the system is operational and accessible to users.

A highly available system should continue working even when some components fail.

Example:

    Server 1 ---- X
                   \
                    Load Balancer ---- Users
                   /
    Server 2 -------

If Server 1 fails, traffic can be redirected to Server 2.

---

## 7.3 Reliability

Reliability is the ability of a system to consistently perform its expected functions correctly.

A reliable system should produce correct results and handle failures properly.

---

## 7.4 Performance

Performance describes how efficiently and quickly a system responds to requests.

Two important performance concepts are:

- Latency
- Throughput

### Latency

The time taken to process a request.

Example:

    User Request
         |
         v
    Server Processing
         |
         v
    Response

If the response takes 100 ms, the latency is approximately 100 ms.

### Throughput

The number of requests a system can process in a given amount of time.

Example:

    1,000 requests / second

---

## 7.5 Security

Security protects the system and its data from unauthorized access and attacks.

Examples:

- Authentication
- Authorization
- Encryption
- Secure APIs
- Access control
- Rate limiting

---

## 7.6 Maintainability

Maintainability refers to how easily developers can understand, modify, test, and extend the system.

A maintainable system should make it easier to:

- Fix bugs
- Add features
- Modify existing functionality
- Test components
- Replace components

---

## 7.7 Cost

A system should provide the required performance and reliability while keeping infrastructure and operational costs reasonable.

Using more servers can improve scalability, but it also increases cost.

Therefore, cost is another important design consideration.

---

# 8. System Design Is About Trade-offs

There is usually no single perfect system design.

Different choices provide different advantages and disadvantages.

For example:

### SQL vs NoSQL

SQL databases provide strong structure and powerful relational queries.

NoSQL databases can provide flexibility and can be useful for certain large-scale workloads.

The correct choice depends on the requirements.

Other common trade-offs include:

- Consistency vs Availability
- Latency vs Consistency
- Cost vs Performance
- Scalability vs Complexity
- Simplicity vs Flexibility

A good System Designer understands these trade-offs and chooses an appropriate solution.

---

# 9. System Design vs Coding

Coding mainly focuses on implementing a particular functionality.

For example:

> "Write a function to send a message."

System Design focuses on the complete system.

For example:

> "How can millions of users send messages simultaneously?"

This leads to questions such as:

- How are messages transmitted?
- How are messages stored?
- How are messages delivered?
- How do we handle millions of messages?
- What happens if a server fails?
- How do we scale the system?
- How do we maintain message reliability?

Therefore:

> Coding focuses on implementing functionality.

> System Design focuses on designing the complete system and its interactions.

---

# 10. Real-World Example – Messaging Application

Consider a messaging application.

At a very basic level:

    Sender
      |
      v
    Server
      |
      v
    Receiver

But a real-world messaging system may look more like:

    Sender
      |
      v
    Internet
      |
      v
    Load Balancer
      |
      v
    Message Service
      |
      +---------> Message Queue
      |
      +---------> Database
      |
      +---------> Notification Service
      |
      v
    Receiver

At large scale, the system needs to handle:

- Millions of users
- Large numbers of messages
- Real-time communication
- Message delivery
- Database scaling
- Server failures
- Security
- High availability

Designing how all these components work together is System Design.

---

# 11. HLD and LLD Example

Suppose we are building a payment system.

### HLD

We might design:

    User
      |
      v
    API Gateway
      |
      v
    Payment Service
      |
      +-------> Database
      |
      +-------> Payment Gateway
      |
      +-------> Message Queue
      |
      +-------> Notification Service

This is concerned with the system architecture.

### LLD

Inside the Payment Service, we might design:

    Payment
    PaymentMethod
    PaymentProcessor
    PaymentService
    PaymentRepository

We may use:

- Interfaces
- Classes
- SOLID Principles
- Design Patterns

This is concerned with code-level structure.

---

# 12. System Design Mindset

When designing a system, always think about:

### Requirements

What should the system do?

### Scale

How many users and requests should it support?

### Data

What data needs to be stored?

### Performance

How quickly should the system respond?

### Availability

Should the system continue working if something fails?

### Security

How should data and services be protected?

### Failure

What happens when a component fails?

### Cost

How much infrastructure is required?

### Trade-offs

What are we gaining and what are we sacrificing?

---

# 13. Simple System Design Flow

A typical System Design process looks like:

    Requirements
         |
         v
    Traffic Estimation
         |
         v
    API Design
         |
         v
    High-Level Architecture
         |
         v
    Database Design
         |
         v
    Caching
         |
         v
    Load Balancing
         |
         v
    Message Queues
         |
         v
    Failure Handling
         |
         v
    Scalability
         |
         v
    Security
         |
         v
    Monitoring
         |
         v
    Trade-offs

We will study each of these concepts throughout this roadmap.

---

# 14. Key Takeaways

- System Design is the process of designing a software system's architecture and interactions.
- It helps systems handle increasing users, traffic, and data.
- HLD focuses on the overall system architecture.
- LLD focuses on code-level implementation.
- Important system properties include scalability, availability, reliability, performance, security, maintainability, and cost.
- System Design requires making engineering decisions.
- Every design involves trade-offs.
- There is usually no single perfect architecture.
- The correct design depends on the system requirements.

---

# 15. Interview Definition

A concise interview answer:

> System Design is the process of designing the architecture, components, data flow, and interactions of a software system to satisfy its functional and non-functional requirements while considering factors such as scalability, availability, reliability, performance, security, and cost.

---

# 16. Important Terms Introduced

- System Design
- HLD
- LLD
- Architecture
- Scalability
- Availability
- Reliability
- Performance
- Latency
- Throughput
- Security
- Maintainability
- Trade-offs
- Load Balancer
- Cache
- Database
- Message Queue
- API Gateway

---
