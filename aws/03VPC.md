# VPC

## VPC란
---
VPC(Virtual Private Cloud)는 AWS에서 이야기하는 전용 가상 네트워크라고 한다. 

<br>


VPC는 간단하게 ```서브넷(Subnet)```과 ```라우트테이블(Route Table)```, ```보안 그룹(Security Group)```, ```인터넷 게이트웨이(Internet Gateway)```로 구성된다.


우리가 흔히 필요로 하는 인스턴스 생성을 위해서는 VPC가 정의되지 않으면 인스턴스 생성이 되지 않기에 필수적으로 요구되는 과정이다.

아래 사진은 오늘 내용의 내용이라고 보면 이해가 편하다.

<img src="img/VPC-Network-Engineers-Part-1-2.png
" width="80%" ></img>
> ##### 사진출처:  https://aws.amazon.com/ko/blogs/apn/amazon-vpc-for-on-premises-network-engineers-part-one/

<br>

대략적인 흐름은 아래와 같다.

<br>

VPC(내부적으로 여러 AZ가 있음) -> 서브넷 생성 -> 라우트 테이블 정의 -> IG 정의(또는 Elastic IP) -> 인스턴스 생성 및 VPC 및 서브넷 부착  

이때 VPC사용에는 추가적인 요금은 부과되지 않지만 NAT 게이트웨이나 다른 서비스(Reachability Analyzer, 트래픽 미러링 등)을 사용시 부과될 수 있다.



<br>

위의 사진에서 VPC는 내에 여러 가용 영역이 존재하는데 이는 VPC생성시 여러 가용 영역에 적용된다고 한다. 아래의 사진을 참고한다면 좋다고 생각한다.

<img src="img/vpc-diagram.png
" width="40%" ></img>
> ##### 사진출처:  https://docs.aws.amazon.com/ko_kr/vpc/latest/userguide/configure-your-vpc.html

## Subnet?
---
AWS에서 이야기하길 서브넷은 VPC의 CIDR로 표현되는 IP 주소 범위라고 한다.

만약 서브넷이 없다면 인스턴스는 IP주소를 부여받지 못하기에 VPC와 함께 서브넷 또한 함께 생성되어야한다.

<br>

* 각 서브넷은 단일 가용 영역 내에서만 존재해야 한다. (AWS에서 말하길 단일 영역에서 장애 발생시 애플리케이션을 보호하기 위함이라고 함)

* 여러 영역으로의 확장이 불가능하다.


<br>


서브넷을 구성할 때 IPv4, IPv6옵션 및 유형을 선택하게 되는데 

<br>


IPv4, Ipv6로는 단일 구성 또는 듀얼 스택(IPv4 및 IPv6)으로 구성된다.

서브넷의 유형으로 퍼블릭(Public), 프라이빗(Private), VPN 전용으로 나누어진다고 한다.


<img src="img/subnet-diagram.png
" width="100%" ></img>
> ##### 사진출처:  https://docs.aws.amazon.com/ko_kr/vpc/latest/userguide/configure-subnets.html#subnet-diagram


## Public Subnet & Private Subnet??
---
여기서 서브넷은 주로 퍼블릭 또는 프라이빗 서브넷으로 구성되는데 간단하게 설명하자면 IG의 attach 여부에 따라 퍼블릭 또는 프라이빗 서브넷이라고 불린다.

즉, 퍼블릭 인터넷의 접근 여부라고 볼 수 있다.

## 서브넷 라우팅
---

IP주소를 위해 서브넷을 정의하였는데 모든 서브넷은 라우트 테이블을 지나간다고 표현한다. 

이는 라우트 테이블에 따라 서브넷마다 다른 접근 권환을 가질 수 있다고 이야기된다.

예를 들자면 특정 서브넷의 라우트 테이블 중 IG가 붙어있다면 해당되는 서브넷을 통해 퍼블릭 인터넷에 접근가능하다.

<br>

VPC를 생성한다면 자동적으로 메인 라우트 테이블이 생성이 된다. 이때 대개 권장되는 방식은 메인 라우트 테이블은 로컬 라우트를 유지하고 새로운 서브넷은 커스텀된 라우트 테이블을 적용하는 방식을 많이 사용된다.

|대상주소(Destination)|대상(Target)|
|------|-----------------|
|10.0.0.0/16|Local|
|0.0.0.0/0|igw-something|
|172.31.0.0/16|eigw-something|

## 보안 그룹 & NACL
---

서비스를 제공한다고 하면 보안은 꼭 살펴보아야 하는 영역이다. VPC에서 네트워킹을 통한 리소스 접근의 제어는 ```Security Group``` 및 ```Network Access Control List(NACL)```을 통해 구현이 가능하다.


## 보안 그룹(Security Group)
---

보안 그룹은 VPC내에 있는 인스턴스에 대한 가상 방화벽이라고 설명된다. 인스턴스에 대해 내부/외부로 이동되는 트래픽에 대해 접근을 정의한다.

이러한 보안 그룹은 인스턴스 단위로 할당되기에 인스턴스마다 새로운 시큐리티 그룹을 생성하여야 한다.

또한 기본적으로는 아웃바운드에 대해서는 허용이 되지만 인바운드에 대해서는 모두 거절이 default로 되어 있다. 

보안 그룹을 생성시 아래의 규칙에 따라 생성하여야 한다.

* 보안 그룹의 이름은 VPC 내에서 유일무일해야한다.
* 이름과 설명은 최대 255자로 제한된다.
* 이름과 설명은 다음과 같은 문자를 포함 할 수 없다. a-z, A-Z, 0-9, 공백 및 ._-:/()#,@[]+=&;{}!$*
* 이름에 후행 공백이 포함되어 있으면 이름 끝의 공백을 잘린다. 예를 들어 이름에 “테스트 보안 그룹 ”을 입력하면 “테스트 보안 그룹”으로 저장된다..
* 보안 그룹 이름은 sg-로 시작할 수 없다.

아래는 보안 그룹의 특징이다.

* 허용 규칙만이 지정가능하고 거부 규칙은 지정이 불가능하다.
* 보안 그룹을 처음 생성시 인바운드 규칙이 없다. 따라서 인바운드 규칙을 추가하기 전까지는 어떤 인바운드 트래픽은 허용이 불가능하다. 

## Reference

> https://docs.aws.amazon.com/ko_kr/vpc/latest/userguide/what-is-amazon-vpc.html

> https://docs.aws.amazon.com/ko_kr/vpc/latest/userguide/configure-subnets.html

> https://docs.aws.amazon.com/ko_kr/vpc/latest/userguide/VPC_SecurityGroups.html