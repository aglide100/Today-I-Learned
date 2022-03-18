# gRPC란

## 1. gRPC란?

---

gRPC는 protocol buffers라고 불리는 IDL(Interface Definition Language)를 마치 내부의 시스템처럼 읽고 쓸 수 있다.

gRPC는 다른 RPC시스템처럼 클라이언트에서 직접적으로 서버의 메소드를 호출할 수 있습니다.

gRPC는 Protocol Buffers를 사용하며 구글에서 만들 직렬화된 데이터 구조를 가지는 것입니다.

>

## 2. gRPC, Rest??

---

우선 gRPC는 HTTP2를 기본적으로 이용하여 통신하며 client와 server에서 proto `request`/`response`를 통해 직렬화된 바이너리 데이터를 주고 받는다.

이러한 통신을 위해서는 기본적으로 client와 server간의 원할한 통신을 위해 IDL(Interface Define Language)를 명시하여 사용하는데

이 grpc의 IDL은 기본적으로 message와 rpc를 가지는데 이렇게 선언된 두 가지 타입으로 원격으로 프로시저를 호출하게 됩니다.

간혹 자료조사를 하다보면 gRPC와 rest를 비교하는데

rpc와 rest는 성격이 다소 다르지만 gRPC의 protocolbuf로 명시한 데이터도 결국은 직렬한 데이터이기에 이 부분을 좀더 다듬으면 rest한 api로 컨버팅이 쉽다는 얘기로 귀결된다.

이러한 것은 gRPC Gateway등 오픈소스 라이브러리를 쓴다면 더 손쉽게 하나의 서버에서 gRPC서버와 rest한 api를 꾸릴 수 있다.

## 3. 그럼 브라우저에서는 어떻게 데이터를 받나요??

---

기본적으로 gRPC는 rpc(`remote procedure call`)이다. 하지만 HTTP2를 지원하기에 동일한 커넥션으로 병렬 요청이 가능하다.

브라우저는 기본적으로 gRPC통신을 지원해주지 않기에 브라우저와 서버간의 통신을 위해서는 grpc-gateway등을 통해 데이터를 컨버팅하여 전달하야 된다.

이는 기본적으로 브라우저가 지원을 하지 않으니 중간에 proxy를 구성해야 한다는 단점이 생긴다.

이를 위해서 google에서는 `envoy proxy`을 이용해서 구현을 하고
`improbable`은 클로저 라리브러리를 기반으로 구현을 하였다.

이러한 방식은 연유가 어떻든 proxy가 중간에 들어가게 되는 것이다.

작성중....

## 참고자료

---

> https://devjin-blog.com/golang-grpc-server-1/

> https://velog.io/@kyusung/grpc-web-example
