# 목차

- [수학적 귀납법](#수학적-귀납법)
  - [수학적 강귀납법](#수학적-강귀납법)
- [직접 증명법](#직접-증명법)
- [간접 증명법](#간접-증명법)
  - [대우증명법](#대우증명법)
  - [모순증명법](#모순증명법)
  - [반례에 의한 증명법](#반례에-의한-증명법)
- [재귀법](#재귀법)

# 증명



## 수학적 귀납법



자연수 n 에 관한 명제 p(n)에 대하여 다음 두 조건이 성립한다고 하자

1. p(1) 은 참이다
2. 임의의 자연수 k에 대하여 p(k)가 참이면 p(k+1)도 참이다

이때 모든 자연수 n에 대하여 p(n)은 참이다. 이를 수학적 귀납법 이라고 한다



즉, 수학적 귀납법에 의한 증명에서는 n = 1 인경우 명제 p(1)이 참임을 보이고, 

양의 정수  n = k에 대해 p(k)가 참이라고 가정한 후에 p(k+1)도 참임을 보이면 된다.



### 수학적 강귀납법

1.  p(1)은 참이다
2. 임의의 자연수 k에 대하여 p(1), p(2), p(3), ..... p(k)가 모두 참이면 p(k+1)도 참이다

이때 모든 자연수 n에 대하여 p(n)은 참이다. 이를 수학적 강귀납법 이라고 한다



## 직접 증명법



직접증명법은 명제의 함축 p → q 가 참이 됨을 증명하는 방법이다

이 방법은 p가 참이라고 가정하고, q 가 참임을 증명하는 것이다. (그러면 p → q 가 참임이 증명된다)



## 간접 증명법



직접증명법 외의 모든 다른 증명 방법들을 '간접증명법' 이라고한다

간접증명법은 명제를 증명하기 쉬운 명제로 변환하여 증명하는 방법이다

대우증명법, 모순증명법, 반례증명법 등이 있다



### 대우증명법

- 대우증명법은 p → q 가 참이면 그 대우인￢ q → ￢ p 도 참이라는 점, 두 명제가 서로 동치라는 점을 이용한다
- 즉, 대우명제가 참임을 증명하여 그 명제가 참임을 증명하는 방법이다



### 모순증명법

- 모순증명법은 주어진 명제를 부정한 뒤 그 식을 전개할 때 결론이 모순임을 보여 명제가 참임을 증명하는 방법
-  p → q 와 ￢ (p ∧ ￢ q)가 동치인 점을 이용한다
- (p ∧ ￢ q) 가 참이라고 가정한뒤에 결과가 모순임을 찾는다



예) √2는 유리수가 아님을 증명하라

√2 가 유리수라고 가정하면  √2 = n/m (n,m은 정수, n은 0이 아님, n,m은 공통인수를 갖지 않는 정수)

양변을 제곱하면 2m^2 = n^2 이다. 2m^2은 짝수 이므로 n^2도 짝수이고 n도 짝수이다

n = 2k를 다시 대입하면 2m^2 = 4k^2 즉, m도 짝수이다

n,m은 공통인수를 갖지 않는다는 가정에 모순이 되므로(공통인수 2를 가짐)  √2는 유리수가 아니다



### 반례에 의한 증명법

모순을 찾아서 명제가 거짓임을 밝히는 방법



## 재귀법

하나의 문제를  그보다 작은 값을 가지는 동일한 문제로 단순화 시켜 해결하는 방법을 '재귀법' 이라고 한다

재귀법을 이용하여 문제를 해결하기 위해서는 일련의 규칙을 찾아 문제를 다시 정의해야하는데

1. 초기조건을 정의하고
2. 재귀조건을 정의한다

(이때 초기조건은 하나 이상일 수 있다)



예) n! (n 은 양의 정수) 을 구해주는 함수를 정의 해보자

factorial(n) = n! 이라고 하자

1. 초기조건 

   factorial(0) = 0! = 1

2. 재귀조건

​		n=>1 일때

​	    factorial(n) = factorial(n-1) * n