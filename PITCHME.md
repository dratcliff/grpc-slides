# gRPC

High-performance services using Go and gRPC

---

### Agenda

- Intro (2m)
- What is gRPC? (2m)
- HTTP/1.1 vs HTTP/2.0 (4m)
- Protocol Buffers (4m)
- Demo of converting REST server/client to gRPC (15-20m)
- Deploy services to Istio-enabled Kubernetes cluster (10m)
- Questions (or ask them throughout)

---

### What is gRPC?

- gRPC stands for gRPC Remote Procedure Calls
- Interface Definition/Description Language (IDL) to describe APIs (Protocol Buffers)
- Generate server/client stubs using Protocol Buffers compiler
- Client/server communication using HTTP/2

---

### HTTP/1.1 vs HTTP/2

- HTTP/2 is a binary protocol
- HTTP/2 supports header compression
- HTTP/2 allows for multiplexed streams
  - HTTP/1 allowed pipelining, but responses had to be processed in order
  - HTTP/2 removes head-of-line blocking, allows concurrent requests/responses to be processed
    asynchronously and independently over single TCP connection

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

@snap[north-west why-proto]
@size(1.5em](Why not just use XML?)
@snapend

@snap[west proto-pro]
Protocol buffers:
 - are simpler
 - are 3 to 10 times smaller
 - are 20 to 100 times faster
 - are less ambiguous
 - generate data access classes that are easier to use programmatically
@snapend

@snap[east proto-con]
But:
 - not human-readable and human-editable
 - not self-describing
@snapend

---

### Demo

 - Client/server
 - Istio routing

---

### Questions

