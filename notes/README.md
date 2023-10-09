# GRPC

gRPC is a way to communication between several services. The protocol use **http** and the interface of communication is through *protocol buffer* (protobuf).

We use protobuf to define a "contract" of the communication, gRPC with protobuff is a *Interface Definition Language*.
This communication we can do in several languages programming and the best thing is that there are a generator where we can generate a client or structure of the server part.

## ProtoBuff

There are several concept in this **IDL**. The extension of file is *.proto*. By other hand the Input/output define like a message. We must define name, data type and finally position (a number). We define the serialization/parse data to/from raw bytes.
```proto
    message Person {
        string name = 1;
        int32 id = 2;
        bool legalAge = 3;
    }
```
Then we are going to have methodd that this method work over input/ouput. We can define several services in the same file or we can split the information in several proto file.
There ara four type services:

- Unary Request.
- Client streaming.
- Server streaming.
- Bidirectional streaming.

*Unary request* is a simple request, and the other options are streaming of data for some part or both.
We are going with a little example of protobuf service:
```proto
    service Greeter {
        rpc SayHello (HelloRequest) returns (HelloReply) {}
        rpc SayHelloPeople(stream HelloRequest) returns (HelloReply){}
        rpc SayHelloGroup(HelloRequest) returns (stream HelloReply){}
        rpc SayHelloEveryOne(stream HelloRequest) returns (stream HelloReply){}
    }
```

There ara a lot of data type, optional settings and there is even a method to evolution the API with deprecated fields.
The oficial documentation of protobuf there is a lot of additional information with details [documentation](https://protobuf.dev/)
