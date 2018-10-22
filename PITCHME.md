# gRPC

High-performance services using Go and gRPC

---

### Agenda

Intro (2m)  
What is gRPC? (2m)  
HTTP/1.1 vs HTTP/2.0 (4m)  
Protocol Buffers (4m)  
Development Demo (15-20m)  
Deployment Demo (10m)  
Questions (or ask them throughout)  
@snap[north-east]
@fa[clock-o fa-3x]
@snapend
---

### What is gRPC?

gRPC stands for gRPC Remote Procedure Calls.  

gRPC uses an Interface Definition Language (IDL) to describe APIs (Protocol Buffers).  

Server/client stubs are generated from .proto file using Protocol Buffers compiler.  

Client/server communication using HTTP/2.  

---

### HTTP/1.1 vs HTTP/2

HTTP/1 allowed pipelining, but responses have to be processed in order.  

This leads to head-of-line blocking and requires client-server communications
to use many connections for better parallelism.

@fa[arrow-down]

+++

### HTTP/1.1 vs HTTP/2

HTTP/2 is a binary protocol and supports header compression.  

HTTP/2 allows for multiplexed streams. This allows concurrent
requests/responses to be processed asynchronously and independently
over a single TCP connection.

---?code=src/addressbook.proto&title=Sample .proto file

@[1-9]
@[11-30]
@[12-14]
@[27]
@[29]

---

### Why not just use XML?

Protocol buffers are:  

Simpler   
3-10 times smaller   
20-100 times faster  
Less ambiguous  

@fa[arrow-down]

+++

### Why not just use XML?

But protocol buffers are not:  

Human-readable  
Human-editable  
Self-describing

---

### Demo
Go server: mux -> gRPC server  
Go client: http client / json -> gRPC client  

Hopefully side-by-side deployment with Istio/k8s
---

### Questions

