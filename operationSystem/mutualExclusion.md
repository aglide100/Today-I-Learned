## 상호 배제(Mutual Exclusion)와 동기화

# 상호 배제(Mutual Exclusion)란

The execution if critical sections must be mutually exclusive

상호 배제란 특정 공유 자원을 한 순간에 한 개의 프로세스만 사용할 수 있을 때, 프로세스 하나가 공유 데이터에 접근하는 동안 다른 프로세스가 해당 데이터를 접근할 수 없게 하는 것

# 상호 배제와 동기화란

운영체제에서 프로세스에 대해 상호 배제를 보장할 때, 프로세스 간 동기화가 필요하다.

이때 프로세스 간 동기화를 위해

1. 공유 자원을 동시에 사용하지 못하게 실행을 제어하는 기법
2. 순차적으로 재사용 가능한 자원을 공유하기 위해 상호작용하는 프로세스 사이에서 나타난다.

즉, 공유 자원을 동시에 사용하지 못하게 하기 위함이 있다.

이때 여러 프로세스를 실행한다고 가정하였을 때 프로세스들이 동시에 사용하는 자원인 공유 자원을 임계 자원(`Critical Resource`)라며 하며

공유 메모리가 참조되는 프로그램의 부분(데이터나 데이터 구조)으로 다수의 프로세스가 접근 가능한 영역이면서 한 순간에 하나의 프로세스만이 사용할 수 있는 영역을 임계 구역(`Critical Section`)이라고 한다.

이 임계 구역은 하나의 프로세스가 공유 데이터를 접근하는 코드를 실행할 때에 그 프로세스가 임계 구역에 있다라고 정의한다.

이때 프로세스가 같은 공유 데이터를 접근할 때 순서에 따라 결과값에 영향을 준다면 이를 경쟁 상태(`race condition`)에 있다고 이야기 한다.

`race condition`에 놓인 프로세스는 세 가지 제어 문제에 직면한다.

바로 앞에서 나온 상호 배제(`Mutual exclusion`), 교착상태(`Deadlock`), 기아상태(`Starvation`)에 직면한다.

교착상태(Deadlock)은 여러 프로세스가 존재할때 각각 프로그램을 실행할때 두 자원을 동시에 필요로 할 때 한 프로그램이 수행할 때까지 이미 소유한 리소스를 해제하지 않을 때 생기는 것을 이야기한다.

기아상태(Starvation)은 프로세스가 더 이상 진행을 하지 못하고 영구적으로 블록되어 있는 상태를 이야기한다. 복수의 작업이 서로 상대방의 작업을 끝나기만을 기다리고 있는 것이다.

# SW Solutions Dijsktra's Algorithm(다익스트라 알고리즘)

실행시간이 가장 짧은 프로세스에 CPU를 할당하는 세마포 방법이다. 가장 짧은 평균 대기시간을 제공한다.

```javascript
    do {

        flag[i] = 'want-in';
        while(turn != i) {
            if (flag[turn] = 'idle') {
                turn = i
                // exit process i
            }
        }

        flag[i] = "in-CS";
        j = 0;
        while((j < n) && (j == i || j != "in-CS")) {

        }
    }
```

# 참고자료(Reference)

> https://robodream.tistory.com/559

> https://iredays.tistory.com/125
