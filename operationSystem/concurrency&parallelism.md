# 병행성(Concurrency)와 병렬성(Parallelism)에 대하여

## 병행성(Concurrency)이란

컴퓨터가 여러 일(프로세스)을 마치 동시에 수행하는 것처럼 보이는 것을 말한다.

간단하게 설명하자면 프로세스를 교대로 빠르게 실행하여 마치 동시에 실행되는 것처럼 보이는 것이다.

## 병렬성(Parallelism)이란

병렬성은 병행성과는 다르게 실제로 여러 프로세스가 동시에 실행되는 것을 말한다. Concurrency는 빠르게 교체하는 것이지만 병렬성은 각 CPU마다 할당하는 것이라고 볼 수 있다.

## 병렬 컴퓨팅(Parallel computing)이란

병렬 컴퓨팅은 의존성이 없는 작업을 동시에 실행하는 것을 말한다. 병렬 실행(parallel execution)을 위해 여러 프로세스를 이용하여 수많은 연산을 동시에 병렬 처리를 할 수 있도록 조직된 컴퓨터를 병렬 컴퓨터(parallel computer)라고 한다.

## 병행 컴퓨팅(Concurrent computing)

하나의 프로세서 상에서 여러 개의 프로그램을 실행하는 것을 이야기한다. 하나의 프로세서내에서는 동시에 실행하는 것이 불가능하기에 이를 빠르게 프로세스를 교체하여 마치 동시에 실행되는 것처럼 보여주는 것을 말한다.

## 참고자료

> https://blog.naver.com/PostView.naver?blogId=with_msip&logNo=222439390237&redirect=Dlog&widgetTypeCall=true&directAccess=false

> https://statkclee.github.io/hpc/hpc-basic.html

> https://gkqlgkql.tistory.com/66

> https://blog.naver.com/beanpole2020/221441023808

> https://nesoy.github.io/articles/2018-09/OS-Concurrency-Parallelism

> https://memostack.tistory.com/49

> https://brownbears.tistory.com/213
