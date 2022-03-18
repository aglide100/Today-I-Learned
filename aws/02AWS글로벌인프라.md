# AWS의 글로벌 인프라

우선 AWS는 글로벌하게 서비스를 제공하는데 AWS에서 언급이 되는 단어들이 있다.

 - 리전(Region)
 - 가용성 지역 AZ (Availablity Zones)
 - 로컬 영역 (Local Zone)
 - POP (Point Of Presence)  


 # Region

<img src="img/aws-global-region.png
" width="100%" ></img>
> ##### 사진출처:  https://aws.amazon.com/ko/about-aws/global-infrastructure/?p=ngi&loc=1

현재 AWS는 26개의 리전을 제공하고 있다. 여기서 리전은 AWS가 전 세계에서 데이터 센터를 클러스터링하는 물리적 위치를 리전이라고 한다. 

즉, 서비스가 제공될때 이것이 제공되는 곳의 지리적 위치를 의미한다.

# Availablity Zones

각 리전에는 AZ라고 불리는 영역이 존재하는데 대개 하나의 AZ는 한 개에서 6개의 데이터 센터로 구성된다. 이는 각각 다른 층에 있으며 전력망 또한 자연재해 등에 영향을 받지 않기 위해 AZ별로 분산되도록 설계되었다고 한다.

동일 리전내에도 AZ가 여러 곳이 있을 수 있는데 이 AZ들은 저비용성과 고응답성, 고보안성의 조건을 충족하는 광케이블 네트워크로 구성되어있으며 동기적으로 AZ간의 데이터 복제 인스터스를 생성이 가능하다고 한다.

# 엣지 로케이션 (POP)

전 세계 주요 도시에 위치혀며, 대개 CDN, 즉 콘텐츠 배포 네트워크로 사용된다.

AWS에서 엣지 로케이션은 Amazon CloudFront 서비스와 Amazon Route 53 서비스 제공하는데에 활용된다.

# Local Zone

사용자는 많지만 리전이 없는 지역에 Local Zone을 추가해 서비스를 제공한다. Local Zone은 인근 Parent Region과 초고속 보안 네트워크로 연결되어 AWS서비스를 제공한다고 한다.

기존의 Local Zone은 AWS의 Region을 보조하기 위해 설계되었다고 한다.

AWS의 설명을 조금 더 빌리자면 기계 학습, 실시간 게임 등 지연 시간이 10밀리초 미만이어야 하는 매우 까다로운 애플리케이션을 쉽게 실행할 수 있다고 한다.

# AWS Wavelength
간단하게 이동 통신 사업자 데이터 센터 내의 5G 네트워크에 AWS 컴퓨팅 및 스토리지 서비스를 포함하는 인프라 배포 환경이라고 볼 수 있다. 대개 증강 및 가상 현싱등에 사용된다고 볼 수 있을 것 같다.

# AWS Outposts
온 프레미스에 남겨져 운영될 수 밖에 없는 서비스를 AWS에서 하나로 관리할 수 있는 것이라고 볼 수 있다.

고객에게 AWS환경을 온 프레미스에서 쓸 수 있게 렉과 서버를 제공한다고 한다.

다만 설치에 있어서 생각보다 복잡한것 같다. 로컬 게이트웨이에서의 라우팅 테이블에서 Outposts와 온프레미스 통신이 처리되는 것으로 보인다.

결론은 하이브리드 클라우드를 제공하는 것으로 보인다.

> https://aws.amazon.com/ko/blogs/korea/aws-outposts-now-available-order-your-racks-today/

# AWS 보안 모델

<img src="img/aws-shared-responsibility-model_V2.59.jpg" width="100%" ></img>
> ##### 사진출처:  https://aws.amazon.com/ko/compliance/shared-responsibility-model/


AWS에서의 보안은 공동 보안 모델을 사용한다. 이것이 무슨 의미인가는 간단하게 설명하자면 AWS가 제공하는 영역에서는 AWS가 책임을 지며, 고객의 영역에서는 고객이 책임을 진다는 것이다. 

예를 들어 AWS의 EC2의 같은 경우에는 IaaS로 서비스가 분류되는데 이는 고객이 보안 및 관리작업을 행하여야 한다. 이러한 구성관리에 대해서 고객이 책임을 진다는 것이다.

이러한 공동 보안 모델은 서비스별로 다르며 해당되는 사안을 확인 후 사용 사례에 적용하여아 한다.