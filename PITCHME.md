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

---

### What is gRPC?

gRPC stands for gRPC Remote Procedure Calls.  

grpc uses an Interface Definition/Description Language (IDL) to describe APIs (Protocol Buffers).  
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

---?code=src/addressbook.proto&title=Protocol Buffers

@[10-13]
@[27-29]
@[31-35]
@[37-42]

---

### Why not just use XML?

Protocol buffers are: <br><br>simpler<br>3-10 times smaller<br>20-100 times faster<br>less ambiguous

@fa[arrow-down]

+++

### Why not just use XML?

But protocol buffers are not: <br><br>human-readable<br>human-editable<br>self-describing

---

### Demo

 - Client/server
 - Istio routing

---

### Questions

