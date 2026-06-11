# Load Balancer

## What is a Load Balancer?

A Load Balancer sits between users and servers and distributes incoming traffic across multiple servers.

Instead of sending all requests to one server, it spreads the traffic so that no single server becomes overloaded.

---

## Why Do We Need a Load Balancer?

Imagine an e-commerce website.

Without a Load Balancer:

User Requests → EC2 Instance 1

If traffic suddenly increases:

* EC2 Instance 1 becomes overloaded.
* Website becomes slow.
* Website may even crash.

With a Load Balancer:

User Requests → Load Balancer → EC2 Instance 1
→ EC2 Instance 2
→ EC2 Instance 3

Traffic is distributed evenly, improving performance and availability.

---

## Why Can't Users Directly Access EC2 Instances?

They can.

However, this creates several problems:

* One instance may receive too much traffic while others remain idle.
* If an instance fails, users connected to it will experience downtime.
* Managing traffic becomes difficult.

A Load Balancer solves these problems automatically.

---

## Benefits of a Load Balancer

* Distributes traffic across multiple servers.
* Improves application availability.
* Prevents individual servers from being overloaded.
* Automatically routes traffic away from unhealthy instances.
* Works together with Auto Scaling.

---

## Health Checks

A Load Balancer continuously checks whether an EC2 instance is healthy.

Healthy Instance:

* Receives traffic.

Unhealthy Instance:

* Does not receive traffic.

Example:

EC2 Instance 1 → Healthy
EC2 Instance 2 → Healthy
EC2 Instance 3 → Unhealthy

The Load Balancer sends requests only to Instance 1 and Instance 2.

---

## What Happens If a Server Goes Down?

The Load Balancer detects the failure through health checks.

Traffic is automatically redirected to healthy instances.

Users can continue using the application with little or no disruption.

---

## Relationship Between Load Balancer and Auto Scaling

Load Balancer:

* Distributes traffic.

Auto Scaling:

* Adds or removes EC2 instances based on demand.

Example:

Normal Traffic:

* 2 EC2 Instances

High Traffic:

* Auto Scaling launches 3 more instances.

Load Balancer automatically starts sending traffic to all available healthy instances.

Together they provide scalability and high availability.

---

## Types of AWS Load Balancers

### Application Load Balancer (ALB)

Operates at Layer 7 (Application Layer).

Used for:

* HTTP
* HTTPS

Can route traffic based on:

* URL paths
* Hostnames

Example:

example.com/products → Server A

example.com/payments → Server B

---

### Network Load Balancer (NLB)

Operates at Layer 4 (Transport Layer).

Used when:

* Extremely high performance is required.
* Very low latency is needed.

Works with:

* TCP
* UDP

---

### Gateway Load Balancer (GWLB)

Used for deploying and scaling network security appliances such as firewalls.

---

## Easy Way to Remember

Load Balancer = Traffic Manager

Auto Scaling = Capacity Manager

The Load Balancer decides:

"Which server should handle the request?"

Auto Scaling decides:

"Do I need more servers or fewer servers?"

---

## Exam Tip

A common AWS exam scenario:

Problem:
Traffic is increasing and one EC2 instance cannot handle all requests.

Solution:
Use an Application Load Balancer together with an Auto Scaling Group.

This provides:

* High Availability
* Fault Tolerance
* Scalability

---

## Quick Revision

* Load Balancer distributes traffic across multiple servers.
* Prevents servers from becoming overloaded.
* Performs health checks.
* Routes traffic only to healthy instances.
* Works closely with Auto Scaling.
* ALB = Layer 7 (HTTP/HTTPS)
* NLB = Layer 4 (TCP/UDP)
* GWLB = Security appliances
