---
layout: post
title:  "[Technical Interview] Basic Knowledge"
date:   2016-11-16 01:14:55 -0500
categories: Interview
---


## Programming Language

- Java 8 特性
  - Interface changes with default and static methods  - Functional interfaces and Lambda Expressions  - Java Stream API for collection classes  - Java Date Time API

- static和final
   
   ```java
      class Example {
          public static final int CONSTANT = 123;   
      }
   
   ```

- final vs finally vs finalize
   
- garbage collection
  clear explanation [here]()


- 什么是reference
- nums==null 和 nums.length==0 有什么区别
- 什么是继承
- HashMap Implementation
- 什么是单例Singleton
- 什么是工厂模式 Factory

## Operating System

- 进程和线程有什么区别
   
   Process: 
   Thread: 

   Both processes and threads are independent sequences of execution. The typical difference is that threads (of the same process) run in a shared memory space, while processes run in separate memory spaces.

- User Thread vs. Kernel Thread

- 进程地址空间

   general C program model [here](http://www.geeksforgeeks.org/memory-layout-of-c-program/)
   
   more detailed.[here](http://duartes.org/gustavo/blog/post/anatomy-of-a-program-in-memory/)

   ```
      -------------------------- high address
      Kernel Space
      --------------------------
      Stack (grows down)
      --------------------------
      Heap (grows up)
      --------------------------
      BSS segment
      --------------------------
      Data segment 
      -------------------------- 
      Text segment (ELF)
      -------------------------- low address
   ```

- Deadlock

- Condition Variable

- 什么是锁mutex
- 什么是信号量(semaphore)
- 什么是栈溢出
- 不同存储结构的速度量级（磁盘、SSD、内存、L1 cache）
- 什么是IO
- Object Oriented Design


## Network

- 什么是Socket
A socket is one endpoint of a two-way communication link between two programs running on the network. A socket is bound to a port number so that the TCP layer can identify the application that data is destined to be sent to.

- TCP 和 UDP有什么区别


- TCP/IP三次握手
- 什么是HTTP
- 什么是API
 
- 在输入框里输入google.com之后会发生什么
 1. browser checks cache; if requested object is in cache and is fresh, skip to #9
 2. browser asks OS for server's IP address
 3. OS makes a DNS lookup and replies the IP address to the browser
 4. browser opens a TCP connection to server (this step is much more complex with HTTPS)
 5. browser sends the HTTP request through TCP connection
 6. browser receives HTTP response and may close the TCP connection, or reuse it for another request
 7. browser checks if the response is a redirect or a conditional response (3xx result status codes), authorization request (401), error (4xx and 5xx), etc.; these are handled differently from normal responses (2xx)
 8. if cacheable, response is stored in cache
 9. browser decodes response (e.g. if it's gzipped)
 10. browser determines what to do with response (e.g. is it a HTML page, is it an image, is it a sound clip?)
 11. browser renders response, or offers a download dialog for unrecognized types



## Database

MySQL：设计场景，问foreign key、inner join /outer join
多对多的关系怎么设计（比如好友关系）
SQL 与NoSQL的区别
什么是Transaction
什么是ACID

