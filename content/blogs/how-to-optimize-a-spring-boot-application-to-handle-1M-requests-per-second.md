---
title: "How to optimize a Spring Boot Application to Handle 1M Requests/Second"
date: 2025-02-20T10:00:00+07:00
draft: false
tags: ["spring", "spring boot", "optimize"]
categories: ["blog"]
description: "How to optimize a Spring Boot Application to Handle 1M Requests/Second"
weight: 1
ShowToc: true
---
Scaling a Spring Boot application to handle 1 million requests per second might sound like an impossible feat, but with the right strategies, it’s absolutely achievable. Here’s how I did it:

![Spring Boot and friends](/images/optimize-spring-boot/optimize-spring-boot-1.webp)

## 1. Understand Your Bottlenecks

Before optimizing, I conducted a thorough performance analysis using tools like JProfiler and New Relic.

This helped identify key issues:
High response times for certain APIs.
Database queries taking too long.
Thread contention in critical parts of the application.

💡 Lesson Learned: Always measure before you optimize. Guesswork can lead to wasted effort.

## 2. Implement React Programming

Switching to Spring WebFlux for critical parts of the application enabled a nonblocking, reactive architecture. This significantly reduced thread usage, allowing the server to handle more concurrent requests.

## 3. Optimize Database Queries

Database performance was a huge bottleneck. Here’s what worked:
Query Optimization: Rewrote complex queries, added proper indexes, and avoided N+1 queries using Hibernate’s `@BatchSize`.
Caching: Leveraged Redis for caching frequently accessed data, cutting down repetitive database hits.
Connection Pooling: Tuned HikariCP settings to handle high traffic efficiently.

## 4. Tune Thread Pool and Connection Limits

Finetuning thread pools and connection limits in Tomcat and Netty (used by WebFlux) was a gamechanger.
Used `spring.task.execution.pool` settings for async tasks.
Increased Netty’s connection limits and optimized worker threads.

## 5. Leverage CDN and Load Balancers

To distribute the load, I:
Integrated a CDN (like Cloudflare) to cache static assets.
Used a load balancer (NGINX + AWS ALB) to distribute traffic across multiple app instances.

## 6. Optimize Serialization and Compression

Switching to Kryo serialization for data transfer and enabling GZIP compression for responses significantly reduced payload sizes and improved response times.

## 7. Adopt Horizontal Scaling

Deployed the app in a containerized environment using Kubernetes:
Added autoscaling rules to spin up more pods during traffic surges.
Used Istio for traffic shaping and resilience.

## 8. Test, Test, Test Again

I used Gatling and Apache JMeter to simulate realworld traffic. Stress testing helped identify weak spots before deploying to production.

## 🌟 The Result

With these optimizations, our Spring Boot application went from struggling under 100K requests/second to consistently handling 1M requests/second with low latency and high reliability.

## Key Takeaway
Performance optimization is not about finding one magic solution — it’s a combination of small, targeted improvements that align with your specific bottlenecks.


## Refs
This blog post is inspired by How I Optimized a Spring Boot Application to Handle 1M Requests/Second 🚀 by Yatinsindhi on Medium. You can read the full post [here](https://medium.com/system-design-for-beginners-a-roadmap-to-mastery/how-i-optimized-a-spring-boot-application-to-handle-1m-requests-second-322273c8342d).