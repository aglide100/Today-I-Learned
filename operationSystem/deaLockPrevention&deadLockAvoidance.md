# 교착 상태 예방(Dead lock Prevention)

교착 상태 예방는 문자 그대로 교착 상태에 진입하지 않게 예방을 위한 방법이다.

그래서 교착 상태의 조건인 4가지 조건중 하나 이상을 부정한다면 교착 상태에 빠지는 것을 예방할 수 있다.

1. 상호 배제(Mutual Exclusion) 부정
   우선 상호 배제란 비공유를 전제로 하는, 특정 공유 자원을 한 순간에 한 개의 프로세스만 사용할 수 있을 떄를 이야기한다. 여기서 교착 상태 예방을 위해 상호 배제를 부정한다는 것은 이 자원을 공유 자원으로 사용하겠다는 이야기로 볼 수 있다.

   되지만 현실적으로 모든 자원이 공유자원이 된다는 것에는 불가능하다고 볼 수 있기에 상호 배제를 부정하는 것은 힘들다고 볼 수 있다.

2. 점유 및 대기(Hold and Wait) 부정

3. 비선점(No Preemption) 부정

4. 순환 대기(Circular Wait) 부정

# 교착 상태 회피(Dead lock Avoidance)

# 참고자료(Reference)

> https://wonit.tistory.com/96

> https://hoyeonkim795.github.io/posts/%EA%B5%90%EC%B0%A9%EC%83%81%ED%83%9C%ED%95%B4%EA%B2%B0%EB%B0%A9%EB%B2%95/

> https://yoongrammer.tistory.com/67

> 한빛아카데미사의 그림으로 쉽게 배우는 운영체제
