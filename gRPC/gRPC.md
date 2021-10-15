# gRPC란

gRPC는 protocol buffers라고 불리는 IDL(Interface Definition Language)를 마치 내부의 시스템처럼 읽고 쓸 수 있다.

gRPC는 다른 RPC시스템처럼 클라이언트에서 직접적으로 서버의 메소드를 호출할 수 있습니다.

gRPC는 Protocol Buffers를 사용하며 구글에서 만들 직렬화된 데이터 구조를 가지는 것입니다.

>

2. 그렇다면 gRPC는 Restfull한가

우선 gRPC는 HTTP2를 기본적으로 이용하여 통신하며 client와 server에서 proto request/response를 통 직렬화덴 바이너리 데이터를 주고 받습니다.

그렇지만 기본적으로 client와 server간의 통신을 위해 IDL(Interface Define Language)를 선언하여야 합니다.

이 grpc의 IDL은 기본적으로 message와 rpc를 가지는데 이렇게 선언된 두 가지 타입으로 원격으로 프로시저를 호출하게 됩니다.

작성중....
