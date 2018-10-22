# gRPC

High-performance services using Go and gRPC

---

@snap[north-west]
@size[2.0em](Agenda)
@snapend

@snap[west]
Intro (2m)  
What is gRPC? (2m)  
HTTP/1.1 vs HTTP/2.0 (4m)  
Protocol Buffers (4m)  
Demo of converting REST server/client to gRPC (15-20m)  
Deployment example (k8s/Istio) (10m)  
Questions (or ask them throughout)
@snapend

---

### What is gRPC?

gRPC stands for gRPC Remote Procedure Calls. grpc uses an Interface Definition/Description Language (IDL) to describe APIs (Protocol Buffers).
To use: generate server/client stubs from .proto file using Protocol Buffers compiler.

Client/server communication using HTTP/2

---

### HTTP/1.1 vs HTTP/2

HTTP/1 allowed pipelining, but responses have to be processed in order.
This leads to head-of-line blocking and requires client-server communications
to use many connections for better parallelism.

+++

### HTTP/1.1 vs HTTP/2

HTTP/2 is a binary protocol and supports header compression.
HTTP/2 allows for multiplexed streams. This allows concurrent
requests/responses to be processed asynchronously and independently
over a single TCP connection.

---

### Protocol Buffers

```
message Person {
  required string name = 1;
  required int32 id = 2;
  optional string email = 3;

  enum PhoneType {
    MOBILE = 0;
    HOME = 1;
    WORK = 2;
  }

  message PhoneNumber {
    required string number = 1;
    optional PhoneType type = 2 [default = HOME];
  }

  repeated PhoneNumber phone = 4;
}
```

---

@snap[north-west]
@size[1.5em](Why not just use XML?)
@snapend

Protocol buffers are: <br><br>simpler<br>3-10 times smaller<br>20-100 times faster<br>less ambiguous

@fa[arrow-down]

+++

@snap[north-west]
@size[1.5em](Why not just use XML?)
@snapend

But protocol buffers are not: <br><br>human-readable<br>human-editable<br>self-describing

---

### Demo

 - Client/server
 - Istio routing

---

### Questions

