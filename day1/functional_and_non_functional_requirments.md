# Functional vs Non-Functional Requirements

## 1. Introduction

Before designing a software system, we first need to understand what the system is expected to do and what qualities the system should have.

These requirements are mainly divided into two categories:

1. Functional Requirements
2. Non-Functional Requirements

Understanding the difference is one of the most important foundations of System Design.

---

# 2. What is a Requirement?

A requirement describes something that a software system must provide or satisfy.

In simple words:

> A requirement tells us what the system needs to do or how the system needs to behave.

For example, consider an E-Commerce application.

The system may need to:

- Allow users to register
- Allow users to login
- Search products
- Add products to cart
- Place orders
- Make payments

These are requirements of the system.

But we also need to define qualities such as:

- How fast should the system respond?
- How many users should it support?
- Should the system be available 24/7?
- How secure should it be?

These lead to Functional and Non-Functional Requirements.

---

# 3. Functional Requirements

## Definition

Functional Requirements describe **what the system should do**.

They define the actual features, behaviors, and operations that the system must provide.

In simple words:

> Functional Requirements describe the functionality of the system.

Examples:

- User registration
- User login
- Product search
- Adding products to cart
- Placing an order
- Sending messages
- Uploading files
- Making payments

---

## 3.1 Example – E-Commerce System

Suppose we are designing an E-Commerce application.

Functional requirements could be:

### User Management

- Users should be able to register.
- Users should be able to login.
- Users should be able to logout.
- Users should be able to update their profile.

### Product Management

- Users should be able to search for products.
- Users should be able to view product details.
- Users should be able to filter products.

### Cart

- Users should be able to add products to the cart.
- Users should be able to remove products from the cart.
- Users should be able to update product quantity.

### Order

- Users should be able to place an order.
- Users should be able to view order history.
- Users should be able to track an order.

### Payment

- Users should be able to make payments.
- The system should confirm successful payments.
- The system should handle failed payments.

All of these describe **what the system does**.

Therefore, they are Functional Requirements.

---

# 4. Non-Functional Requirements

## Definition

Non-Functional Requirements describe **how the system should perform or behave**.

They define the quality attributes and constraints of the system rather than specific features.

In simple words:

> Non-Functional Requirements describe how well the system should work.

Examples:

- Performance
- Scalability
- Availability
- Reliability
- Security
- Maintainability
- Durability

---

## 4.1 Example – E-Commerce System

Suppose the E-Commerce application has these requirements:

### Performance

The system should respond to most requests within 200 ms.

### Scalability

The system should support millions of users.

### Availability

The system should remain available even if some servers fail.

### Security

User passwords and payment information must be protected.

### Reliability

Orders and payments should not be lost or incorrectly processed.

### Maintainability

Developers should be able to easily add new features.

These describe **how the system should behave or perform**.

Therefore, they are Non-Functional Requirements.

---

# 5. Functional vs Non-Functional Requirements

| Functional Requirements | Non-Functional Requirements |
|---|---|
| Describe what the system does | Describe how the system behaves |
| Define features | Define quality attributes |
| Focus on functionality | Focus on performance and constraints |
| Usually feature-specific | Usually system-wide |
| Example: Login | Example: Login should respond within 200 ms |
| Example: Search products | Example: Search should support high traffic |
| Example: Place order | Example: Orders must be reliable |
| Example: Send message | Example: Messages should be delivered quickly |

---

# 6. Simple Way to Remember

Ask two questions:

### Functional Requirement

> "What should the system do?"

Examples:

- Login
- Register
- Search
- Upload
- Download
- Payment
- Send message

### Non-Functional Requirement

> "How well should the system do it?"

Examples:

- Fast
- Scalable
- Secure
- Reliable
- Available

Therefore:

> **Functional = WHAT**

> **Non-Functional = HOW WELL**

---

# 7. Real-World Example – WhatsApp

Consider a messaging application.

## Functional Requirements

The system should allow users to:

- Create an account
- Login
- Send messages
- Receive messages
- Send images
- Send videos
- Create groups
- Make voice calls
- Make video calls

These describe what the application should do.

---

## Non-Functional Requirements

The system should:

- Support millions of users.
- Deliver messages with low latency.
- Be highly available.
- Protect user messages.
- Handle server failures.
- Store messages reliably.
- Scale as the number of users increases.

These describe how well the system should operate.

---

# 8. Functional Requirements in System Design Interviews

During a System Design interview, the first step is usually to clarify what functionality we need.

For example:

> "Design a URL Shortener."

Before drawing an architecture, we need to ask:

### Functional Questions

- Should users be able to create short URLs?
- Should users be redirected to the original URL?
- Should users be able to create custom aliases?
- Should URLs expire?
- Should users be able to delete URLs?
- Do we need analytics?

These define the functionality.

---

# 9. Non-Functional Requirements in System Design Interviews

After understanding the functionality, we need to understand the quality requirements.

For example:

### Scalability

How many users or requests should the system support?

### Availability

How much downtime is acceptable?

### Latency

How quickly should a request receive a response?

### Consistency

How quickly should data updates become visible?

### Reliability

Can we lose data or requests?

### Security

Who can access the data?

These requirements influence our architecture.

---

# 10. Why Are Non-Functional Requirements Important?

Non-Functional Requirements have a major impact on System Design.

Consider two systems.

### System A

100 users

A single server may be enough.

    Users
      |
      v
    Server
      |
      v
    Database

### System B

100 million users

A single server is not enough.

We may need:

    Users
      |
      v
    Load Balancer
      |
      +--------+--------+
      |        |        |
      v        v        v
     S1       S2       S3
      |        |        |
      +--------+--------+
               |
             Cache
               |
             Database
               |
          Read Replicas

The functionality may be the same.

But the Non-Functional Requirements are different.

This is why System Design starts with requirements.

---

# 11. Functional Requirements Are Usually More Concrete

Functional requirements often describe specific actions.

Examples:

    User registers
        ↓
    User logs in
        ↓
    User searches
        ↓
    User places order
        ↓
    Payment is processed

These can usually be converted into:

- APIs
- Use cases
- Features
- Services
- Database operations

---

# 12. Non-Functional Requirements Influence Architecture

Non-Functional Requirements determine many architectural decisions.

For example:

### Requirement

The system should handle 1 million requests per second.

Possible design decisions:

- Horizontal scaling
- Load balancing
- Caching
- Database replication
- Database partitioning
- Asynchronous processing

Another example:

### Requirement

The system should have very low latency.

Possible decisions:

- Caching
- CDN
- Geographically distributed servers
- Efficient database queries
- Reduced network communication

Therefore:

> Non-Functional Requirements strongly influence the architecture of the system.

---

# 13. Types of Non-Functional Requirements

Important Non-Functional Requirements in System Design include:

## 13.1 Scalability

Ability to handle increasing load.

## 13.2 Availability

Ability of the system to remain accessible.

## 13.3 Reliability

Ability to consistently perform correctly.

## 13.4 Performance

How efficiently and quickly the system responds.

## 13.5 Security

Protection against unauthorized access and attacks.

## 13.6 Maintainability

Ease of modifying and maintaining the system.

## 13.7 Durability

Ability to preserve data without losing it.

## 13.8 Consistency

How correctly and uniformly users observe data.

## 13.9 Fault Tolerance

Ability to continue operating when components fail.

## 13.10 Observability

Ability to understand what is happening inside the system through logs, metrics, and traces.

---

# 14. Functional + Non-Functional Example

Consider a food delivery application.

## Functional Requirements

The system should allow users to:

1. Register and login.
2. Search restaurants.
3. View menus.
4. Add food to cart.
5. Place orders.
6. Make payments.
7. Track deliveries.
8. Cancel orders.

## Non-Functional Requirements

The system should:

1. Support millions of users.
2. Provide low-latency restaurant searches.
3. Be highly available.
4. Secure payment information.
5. Handle server failures.
6. Reliably process orders.
7. Scale during peak hours.

Now the architecture can be designed based on these requirements.

---

# 15. Functional and Non-Functional Requirements Are Connected

These two types of requirements should not be considered completely separate.

For example:

### Functional Requirement

> Users should be able to place an order.

### Non-Functional Requirements

The order system should:

- Process orders quickly.
- Never accidentally create duplicate orders.
- Remain available during high traffic.
- Protect payment information.
- Reliably store order data.

Therefore, the functionality tells us **what needs to happen**, while the non-functional requirements tell us **the conditions under which it must happen**.

---

# 16. Requirements and Trade-offs

Non-functional requirements can sometimes conflict with each other.

For example:

### Strong Consistency vs Low Latency

Strong consistency may require more coordination between servers.

That coordination can increase latency.

Therefore, the designer must choose an appropriate balance based on the requirements.

Other common trade-offs include:

- Availability vs Consistency
- Cost vs Performance
- Simplicity vs Scalability
- Security vs Convenience

This is why requirements are critical before designing the architecture.

---

# 17. How to Gather Requirements

Before designing a system, clarify:

### Step 1 – Identify Users

Who will use the system?

### Step 2 – Identify Core Features

What should users be able to do?

### Step 3 – Identify Scale

How many users and requests are expected?

### Step 4 – Identify Performance

What latency and throughput are required?

### Step 5 – Identify Availability

How much downtime is acceptable?

### Step 6 – Identify Data Requirements

What data needs to be stored?

### Step 7 – Identify Security Requirements

Who can access what?

### Step 8 – Identify Constraints

Are there budget, technology, regulatory, or infrastructure constraints?

These answers help us design the correct architecture.

---

# 18. Interview Approach

When given a System Design problem, do not immediately start drawing boxes.

First clarify the requirements.

A good approach is:

    Problem
       |
       v
    Functional Requirements
       |
       v
    Non-Functional Requirements
       |
       v
    Scale Estimation
       |
       v
    API Design
       |
       v
    Architecture
       |
       v
    Database
       |
       v
    Scaling & Failure Handling

This prevents us from designing a system based on assumptions.

---

# 19. Key Takeaways

- Functional Requirements define what the system should do.
- Non-Functional Requirements define how well the system should work.
- Functional Requirements focus on features and behavior.
- Non-Functional Requirements focus on quality attributes and constraints.
- Functional requirements can lead to APIs, services, and use cases.
- Non-Functional Requirements strongly influence architecture.
- Scalability, availability, reliability, performance, security, and maintainability are important NFRs.
- Requirements should be clarified before designing the architecture.
- Different requirements can lead to completely different architectures.

---

# 20. Easy Memory Trick

Remember:

    FUNCTIONAL
        ↓
    WHAT?

    NON-FUNCTIONAL
        ↓
    HOW WELL?

Example:

    Functional:
    "Users can upload a profile picture."

    Non-Functional:
    "The upload should complete within 2 seconds
    for most users."

---

# 21. Interview Answer

### What is a Functional Requirement?

> A Functional Requirement describes what a system should do, such as user registration, login, searching, ordering, or sending messages.

### What is a Non-Functional Requirement?

> A Non-Functional Requirement describes how well a system should perform or what constraints it should satisfy, such as scalability, availability, reliability, performance, and security.

### What is the difference?

> Functional requirements define the features and behavior of the system, while non-functional requirements define the quality attributes and constraints under which those features must operate.

---

## Next Topic

**System Design Requirements Gathering**
