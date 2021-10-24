## 한국어는 자연어 처리가 어렵다??

문득 자연어처리 자체도 쉬운일이 아니지만 한국어가 다른 언어에 비해 쉽지 않다는 글을 어디선가 본적이 있었다.

우선 자연어 처리(`Natural Processing`)에 대해서 무엇인지는 간략히 알아봤으니 바로 왜 어려운지 부터 확인해보자

우선 이유부터 보자면 크게는 아래와 같다.

> [1. 교착어](#교착어)

> [2. 띄어쓰기](#띄어쓰기)

> [3. 평서문과 의문문](#평서문과-의문문)

> [4. 주어 생략](#주어-생략)

> [5. 한자기반의 언어](#한자기반의-언어)

## 교착어

언어는 종류에 따라 교착어, 굴적어, 고립어로 나누어지는데 특징은 아래와 같다.

| 종류   | 대표적 언어              | 특징                                                         |
| :----- | :----------------------- | :----------------------------------------------------------- |
| 교착어 | 한국어, 일본어, 몽골어   | 어간에 접사가 붙어 단어를 이루고 의미와 문법적 기능이 정해짐 |
| 굴절어 | 라틴어, 독일어, 러시아어 | 단어의 형태가 변함으로써 문법적 기능이 정해짐                |
| 고립어 | 영어, 중국어             | 어순에 따라 단어의 문법적 기능이 정해짐                      |

여기서 한국어는 교착어에 속한다. 테이블에서도 확인할 수 있듯이 어간과 접사에 따라 단어, 의미를 이루고 문법적 기능이 정해진다.

이러한 특징은 조합을 통해 정말 많은 경우의 수가 생기는 것을 볼 수 있다. 예를 들어 `잡다`라는 원형에서 파생될 수 있는 것들은 정말 많다.
`잡히다`, `잡혔다`, `잡더라` 등 여러 조합이 생길 수 있다.

## 띄어쓰기

근대 이전까지는 동양의 언어에서 띄어쓰기라는 개념이 존재하지 않았다는 점을 볼 수 있다는데 우선은 그점을 접어두더라도 띄어쓰기에 모호성이 있는것은 사실이다.

한국어는 맥락상 띄어쓰기를 하지 않더라도 이해에 무리가 없다.

다만 이러한 특징은 띄어쓰기를 하지 않고 쓰는 것이고 이를 컴퓨터가 이해하기에 다소 힘들다는 것에 있다.

## 평서문과-의문문

영어같은 경우 평서문에서 의문문으로 변형시 주어와 동사의
자리를 바꾸는 등 여러 변화가 생긴다.

아래의 예문을 보자면 이해가 빠르다

### 영어

---

> 평서문

```
I had lunch.
```

> 의문문

```
Did you have lunch?
```

### 한국어

---

> 평서문

```
점식 먹었어.
```

> 의문문

```
점심 먹었어?
```

한국어에서는 그저 마침표와 물음표를 바꾸는 것으로 의미가 변하기도 한다.

또한 마침표와 물음표없이도 맥락에 따라 의문문과 평서문으로 나누어지기도 한다.

## 주어-생략

주어 생략에도 문제가 생기는데 한국어에서는 주어에 대한 정보를 주지 않아도 문장이 완성되기에 이 또한 컴퓨터에서 처리하기에 문제가 생긴다.

## 한자기반의-언어

한자는 '표어 문자'이다. 문자 하나당 하나의 단어를 나타내며 읽는 소리는 같아도 형태와 뜻이 다르다.

다만 이것을 한글로 표시하면서 문제가 생기는데 이것을 '정보의 손실'이라고 표현한다.

사람은 문맥을 통해 이러한 손실에도 문제를 해결이 가능하지만 컴퓨터는 그렇지 않기에 이런 중의성 문제가 더욱 심화되었다.

## 참고자료(Reference)

> https://kh-kim.gitbook.io/natural-language-processing-with-pytorch/00-cover/04-korean-is-hell

> https://ebbnflow.tistory.com/246

> https://media.fastcampus.co.kr/knowledge/data-science/nlp-korean-4reasons/