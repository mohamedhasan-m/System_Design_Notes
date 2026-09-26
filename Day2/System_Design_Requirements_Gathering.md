# System Design – Requirements Gathering

## 1. Introduction

Requirements Gathering is one of the first and most important steps in System Design.

Before designing databases, APIs, servers, caches, or microservices, we first need to understand what the system is supposed to do and what constraints it must satisfy.

In simple words:

> Requirements Gathering is the process of understanding and defining what a system needs to do and how well it needs to perform.

A good system design starts with good requirements.

---

# 2. Why Is Requirements Gathering Important?

Suppose an interviewer asks:

> "Design a food delivery system."

If we immediately start drawing:

    User
      |
      v
    Load Balancer
      |
      v
    Servers
      |
      v
    Database

we are making assumptions.

We don't yet know:

- Who will use the system?
- What features are required?
- How many users are expected?
- How much traffic will we receive?
- How quickly should the system respond?
- How much data will be stored?
- How reliable should the system be?

Different requirements can result in completely different architectures.

Therefore:

> Do not start designing the architecture before understanding the requirements.

---

# 3. Main Goals of Requirements Gathering

During requirements gathering, we try to understand:

1. Who will use the system?
2. What should users be able to do?
3. What data does the system handle?
4. How much traffic will the system receive?
5. How much data will be generated?
6. What performance is expected?
7. How available should the system be?
8. What security is required?
9. What failures should the system handle?
10. What constraints or limitations exist?

---

# 4. Types of Requirements

Requirements are mainly divided into:

## 4.1 Functional Requirements

Functional Requirements describe:

> What should the system do?

Examples:

- Users can register.
- Users can login.
- Users can search products.
- Users can place orders.
- Users can send messages.

---

## 4.2 Non-Functional Requirements

Non-Functional Requirements describe:

> How well should the system perform?

Examples:

- The system should support millions of users.
- Requests should have low latency.
- The system should be highly available.
- User data should be secure.
- The system should be reliable.

---

# 5. Functional Requirements Gathering

First identify the core functionality of the system.

For example, suppose we need to design a URL Shortener.

Possible functional requirements:

1. User can submit a long URL.
2. System generates a short URL.
3. User can access the short URL.
4. System redirects the user to the original URL.
5. URLs may optionally expire.

We should also identify what is NOT required.

For example:

- User authentication may not be required.
- Analytics may not be required.
- Custom aliases may not be required.

This prevents unnecessary complexity.

---

# 6. Non-Functional Requirements Gathering

After identifying functionality, determine the quality requirements.

For example:

### Scalability

How many users should the system support?

### Availability

How much downtime is acceptable?

### Performance

How quickly should requests be processed?

### Reliability

Can requests or data be lost?

### Security

What data needs protection?

### Consistency

How quickly should data updates become visible?

### Durability

Should stored data survive system failures?

These requirements influence our architecture.

---

# 7. Identify the Users

First understand who will interact with the system.

For example, in a food delivery system:

    Customer
       |
       v
    Restaurant
       |
       v
    Delivery Partner
       |
       v
    Admin

Each user type may have different requirements.

### Customer

- Search restaurants
- View menus
- Place orders
- Make payments
- Track orders

### Restaurant

- Manage menu
- Accept orders
- Update order status

### Delivery Partner

- Receive delivery requests
- Accept deliveries
- Update location
- Complete delivery

### Admin

- Manage users
- Manage restaurants
- Monitor the platform

Identifying users helps us understand the system's use cases.

---

# 8. Identify Core Use Cases

A use case describes an interaction between a user and the system.

For example:

    Customer
       |
       +----> Search Restaurant
       |
       +----> View Menu
       |
       +----> Place Order
       |
       +----> Make Payment
       |
       +----> Track Order

Focus on the most important use cases first.

Do not try to design every possible feature immediately.

---

# 9. Define the Scope

Scope defines what is included and excluded from the system.

For example:

### Problem

Design a basic URL Shortener.

### In Scope

- Create short URL
- Redirect short URL
- Store URL mapping

### Out of Scope

- User accounts
- Analytics
- Custom domains
- Advertising

Defining scope prevents the design from becoming unnecessarily complex.

---

# 10. Ask Clarifying Questions

In a System Design interview, requirements are often intentionally incomplete.

You should ask questions before designing.

For example:

> "Design a chat application."

You can ask:

### Users

- How many users are expected?

### Messaging

- One-to-one messaging or group messaging?
- Should messages be delivered in real time?

### Media

- Do users send images and videos?

### Message History

- Should messages be stored permanently?

### Availability

- Should the system work 24/7?

### Scale

- How many messages per second should we support?

These questions help define the system.

---

# 11. Scale Requirements

Scale is extremely important in System Design.

We need to estimate:

- Number of users
- Daily active users
- Requests per second
- Peak requests
- Data generated per day
- Storage required

For example:

    Total Users = 10 Million

    Daily Active Users = 2 Million

    Average Requests/User/Day = 20

Then:

    Daily Requests
    = 2 Million × 20
    = 40 Million requests/day

This information helps determine the required architecture.

We will study these calculations in detail in:

> Capacity Planning and Back-of-the-Envelope Estimation

---

# 12. Traffic Requirements

We need to understand how much traffic the system receives.

For example:

    1,000 requests/second

is very different from:

    1,000,000 requests/second

We should also consider peak traffic.

For example:

    Normal Traffic = 10,000 requests/sec

    Peak Traffic = 50,000 requests/sec

The system should be designed to handle the expected peak load.

---

# 13. Read vs Write Traffic

Another important question is:

> Is the system read-heavy or write-heavy?

### Read-heavy system

Example:

Social media feed.

Users may read content much more often than they create content.

    Reads  = 90%
    Writes = 10%

Caching and read replicas may be useful.

### Write-heavy system

Example:

Logging or event collection system.

    Reads  = 10%
    Writes = 90%

The architecture may require different optimizations.

---

# 14. Data Requirements

We need to understand:

- What data is stored?
- How much data is generated?
- How long should data be stored?
- How frequently is data accessed?
- Is the data structured or unstructured?

Example:

For an e-commerce system:

    User Data
    Product Data
    Order Data
    Payment Data
    Review Data

We also need to estimate how quickly this data grows.

---

# 15. Performance Requirements

Performance requirements describe how quickly the system should respond.

Important metrics include:

### Latency

Time taken to process a request.

Example:

    Request → 100 ms → Response

### Throughput

Number of requests processed per unit of time.

Example:

    50,000 requests/second

We should clarify performance expectations when they matter.

---

# 16. Availability Requirements

Ask:

> How available does the system need to be?

For example:

### Normal Application

Some downtime may be acceptable.

### Banking / Payment System

Downtime can be very expensive and dangerous.

Therefore, the availability requirement will influence architecture.

Highly available systems may require:

- Multiple servers
- Load balancing
- Replication
- Failover
- Multiple regions

---

# 17. Reliability Requirements

Reliability asks:

> Can the system consistently perform its intended operations correctly?

For example, in a payment system:

    User pays ₹1000
          |
          v
       Payment
          |
          v
       Success

We must avoid situations such as:

- Money deducted but order not created.
- Payment processed twice.
- Transaction lost.

Therefore, reliability is especially important for systems involving payments and critical data.

---

# 18. Consistency Requirements

We need to determine how quickly changes should become visible across the system.

Example:

User changes their profile name.

Should every server immediately show the new name?

If yes, stronger consistency may be required.

For some applications, temporary differences may be acceptable.

For example:

    Social Media Likes

A small delay in showing the latest count may be acceptable.

But:

    Bank Balance

requires much stronger consistency.

---

# 19. Security Requirements

Determine:

- Who can access the system?
- Who can access specific data?
- How should users authenticate?
- How should sensitive data be protected?
- What actions require authorization?

Examples:

- Authentication
- Authorization
- Encryption
- Rate limiting
- Access control
- Secure communication

Security requirements should be identified before architecture decisions are finalized.

---

# 20. Failure Requirements

We should ask:

> What happens if something fails?

Possible failures:

- Server crashes
- Database becomes unavailable
- Network failure
- Cache failure
- Message queue failure
- Region failure

For example:

    Server 1 → FAILED

What should happen?

    Load Balancer
          |
          +-----> Server 2
          |
          +-----> Server 3

The system should ideally continue operating.

---

# 21. Identify Constraints

Real-world systems have constraints.

Examples:

### Technical Constraints

- Must use Java
- Must use PostgreSQL
- Must integrate with an existing API

### Business Constraints

- Limited budget
- Must launch quickly

### Regulatory Constraints

- Data must remain within a specific region
- Sensitive data must be protected according to regulations

### Infrastructure Constraints

- Limited servers
- Cloud provider restrictions

Constraints can significantly influence the final architecture.

---

# 22. Prioritize Requirements

Not every requirement has equal importance.

For example, in a payment system:

### High Priority

- Correct payment processing
- Security
- Reliability
- Data consistency

### Lower Priority

- Advanced analytics
- Custom themes
- Non-essential UI features

We should prioritize the requirements that are most important to the business and users.

---

# 23. Avoid Over-Engineering

A common mistake is designing a huge architecture before understanding the actual requirements.

For example, if a system only needs to support:

    100 users

we probably don't need:

- 50 microservices
- Multiple regions
- Complex distributed systems
- Huge Kafka clusters

Start with the simplest architecture that satisfies the requirements.

Then scale it based on actual needs.

> Design for the expected requirements, not imaginary requirements.

---

# 24. Requirements Gathering Example

Let's design a simple URL Shortener.

## Step 1 – Functional Requirements

The system should:

- Accept a long URL.
- Generate a short URL.
- Redirect the short URL to the original URL.

## Step 2 – Users

Anyone with the URL can use the service.

Authentication is not required for the basic version.

## Step 3 – Scale

Suppose:

    10 Million URLs created/month

    100 Million redirects/month

This means the system is more read-heavy than write-heavy.

## Step 4 – Performance

Redirect requests should have low latency.

## Step 5 – Availability

The service should be highly available because users expect links to work whenever they access them.

## Step 6 – Data

We need to store:

    Short URL
        ↓
    Original URL

We may also store:

- Creation time
- Expiration time
- User ID (if authentication is added)

## Step 7 – Security

We should prevent:

- Malicious URLs
- Abuse
- Excessive requests

## Step 8 – Out of Scope

For the basic design:

- Advanced analytics
- Custom domains
- Advertising
- Complex user management

Now we have enough information to start designing the architecture.

---

# 25. Requirements Gathering Checklist

Before designing any system, go through this checklist:

## Users

- Who uses the system?
- What types of users exist?

## Functionality

- What should users be able to do?
- What are the core features?

## Scope

- What is included?
- What is excluded?

## Scale

- How many users?
- How many requests?
- What is the peak traffic?

## Data

- What data is stored?
- How much data?
- How fast does it grow?

## Performance

- What latency is acceptable?
- What throughput is required?

## Availability

- How much downtime is acceptable?

## Reliability

- Can data or requests be lost?

## Consistency

- How quickly should updates be visible?

## Security

- What needs protection?
- Who can access what?

## Failure

- What happens when a component fails?

## Constraints

- Budget?
- Technology?
- Regulations?
- Existing infrastructure?

---

# 26. Requirements Gathering in an Interview

A strong System Design interview usually begins like this:

    Interviewer:
    "Design a food delivery system."

             ↓

    Candidate:
    "Before designing the system,
     I'd like to clarify the requirements."

             ↓

    Identify Users
             ↓
    Functional Requirements
             ↓
    Non-Functional Requirements
             ↓
    Scale
             ↓
    Data
             ↓
    Constraints
             ↓
    Start Architecture

This shows the interviewer that you are thinking systematically rather than immediately jumping into technology choices.

---

# 27. Common Mistakes

## Mistake 1: Starting Architecture Immediately

Wrong approach:

    "We'll use Kafka, Redis, MongoDB, and Kubernetes."

Before knowing the requirements.

### Better approach:

    Requirements
        ↓
    Scale
        ↓
    Constraints
        ↓
    Architecture
        ↓
    Technology Choices

---

## Mistake 2: Making Assumptions

Don't silently assume:

- Number of users
- Traffic
- Data size
- Availability
- Features

Instead, clarify them or explicitly state reasonable assumptions.

---

## Mistake 3: Over-Engineering

Don't introduce complex technologies without a reason.

Every component should solve a requirement.

---

## Mistake 4: Ignoring Non-Functional Requirements

A system may provide all required features but still fail because it is:

- Too slow
- Not scalable
- Not secure
- Not reliable
- Not available

---

# 28. Key Takeaways

- Requirements Gathering is the first major step in System Design.
- Understand the problem before choosing technologies.
- Identify users and their use cases.
- Define Functional Requirements.
- Define Non-Functional Requirements.
- Define the system scope.
- Estimate users, traffic, and data.
- Understand performance and availability expectations.
- Identify security and reliability requirements.
- Identify failures and constraints.
- Prioritize important requirements.
- Avoid unnecessary complexity.
- Requirements determine architecture.

---

# 29. Simple Requirements Gathering Flow

    Problem
       |
       v
    Who are the users?
       |
       v
    What should they do?
       |
       v
    Functional Requirements
       |
       v
    Non-Functional Requirements
       |
       v
    Scale & Traffic
       |
       v
    Data Requirements
       |
       v
    Security & Reliability
       |
       v
    Constraints
       |
       v
    Define Scope
       |
       v
    Design Architecture

---

# 30. Interview Definition

> Requirements Gathering is the process of identifying and understanding the functional requirements, non-functional requirements, users, scale, constraints, data, performance, availability, security, and other expectations of a system before designing its architecture.

---

## Next Topic

**OOP – Abstraction & Encapsulation**
