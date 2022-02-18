# 목차

- [제어문](#제어문)
  - [if문](#if문)
  - [비교 연산자](#비교-연산자)
  - [and or not](#and-or-not)
  - [False로 간주](#False로-간주)
  - [while문](#while문)
  - [for문](#for문)
  - [break](#break)
  - [continue](#continue)
  - [zip()함수](#zip함수)
- [컨테이너](#컨테이너)
- [iterable 객체](#iterable-객체)
- [iterator](#iterator)
- [comprehension](#comprehension)
  - [list comprehension](#list-comprehension)
  - [dictionary comprehension](#dictionary-comprehension)
  - [set comprehension](#set-comprehension)
  - [tuple comprehension](#tuple-comprehension)
- [generator](#generator)
  - [generator 함수](#generator-함수)
  - [generator comprehension](#generator-comprehension)
- [lamda 함수](#lamda-함수)

## 제어문

- '#' 문자가 시작된 곳부터 라인 끝까지 코멘트로 간주
- '#' 이 문자열 안에 있으면 평범한 문자로 간주
- \ 라인 유지하기


```python
a = 'life is short \
you need python'
print(a)
```

    life is short you need python


### if문

if 조건문1:               조건문1이 True 이면 명령문1~k 를 실행하고 if문을 빠져나온다
    명령문1               조건문1이 False 이면 조건문2를 테스트한다
    .
    .
    .
    명령문k
    
elif 조건문2:             조건문2가 True 이면 명령문1~m 을 실행하고 if문을 빠져나온다
    명령문1
    .
    .
    .
    명령문m
    
else:                     조건문2가 False 이면 명령문1~n 을 실행하고 if문을 빠져나온다
    명령문1
    .
    .
    .
    명령문n
    
### 비교 연산자

- == 같다    != 같지 않다    > 크다    >= 크거나 같다     < 작다    <= 작거나 같다

- in 맴버십


```python
1 in [1,2,3]
```




    True




```python
4 in [1,2,3]
```




    False



### and or not

- 동시에 여러개 조건식 비교해야할때 사용
- 여러번 비교 가능


```python
12>10
```




    True




```python
not 12>10
```




    False




```python
5<7<10
```




    True




```python
5<4<10
```




    False



### False로 간주

- Null  None
- 정수  0
- 실수  0.0
- 문자열 ''
- 리스트 []
- 튜플 ()
- 딕셔너리 {}
- 집합 set()
- 이외는 모두 True로 간주

### while문

while 조건식:
    명령문1
    .
    .
    .
    명령문k

- 조건식이 True인 동안 명령문1~k 를 무한으로 실행한다
- 조건식이 False가 되면 즉시 while문을 빠져나온다

### for문

for 변수 in 이터레이블 객체:
    명령문1
    .
    .
    .
    명령문k
    
- iterable객체는 문자열,리스트,튜플,딕셔너리,셋과 같은 객체이다
- 이터레이블 객체의 첫번째 요소부터 마지막 요소까지 차례로 변수에 대입되어 명령문1~k 가 실행된다

### break

- 명령문1~k를 실행하는동안 break를 만나면 즉시 처음으로 돌아가서 명령문1~k를 실행한다
- while문을 실행했을때 break문을 만나지 못했을 경우 다음에 else가 있으면 else이하를 실행한다
- else는 break를 체크하는 성격을 갖는다

### continue

- 명령문1~k를 실행하는동안 continue를 만나면 즉시 처음으로 돌아가서 명령문1~k를 실행한다

### zip()함수


```python
day = ['mon','tue','thu']
fruit = ['orange','melon','apple']
dessert = ['cake','pie','ice cream','cheeze']

for a,b,c in zip(day,fruit,dessert):
    print(a,b,c)
```

    mon orange cake
    tue melon pie
    thu apple ice cream


- 여러 시퀀스를 병렬로 순회 하고자 할때 사용
- 짧은 시퀀스가 완료되면 zip()함수는 멈춘다

## 컨테이너

- 원소들을 포함하고 있는 데이터 구조로 멤버십 테스트가 가능하다
- 메모리를 차지하는 데이터 구조이고 원소 값들은 메모리에 저장되어 있다
- 리스트, 집합, 딕셔너리, 튜플, 문자열


```python
1 in [1,2,3]
```




    True




```python
1 in {1:'a',2:'b',3:'c'}
```




    True




```python
'a' in {1:'a',2:'b',3:'c'}
```




    False




```python
'ab' in 'abcde'
```




    True



## iterable 객체

- 이터레이블 객체는 순회가능객체 라고도 한다
- for루프를 순회하면서 한번에 하나씩 이터레이블 객체를 구성하는 요소 값을 뽑아 사용한다

- 문자열 'abc' 한번에 한문자씩 순회 a-b-c
- 리스트 [1,2,3] 한번에 한요소씩 순회 1-2-3
- 튜플 (1,2,3) 한번에 한요소씩 순회 1-2-3
- 딕셔너리 {'a':1,'b':2,'c':3} 한번에 한key씩 순회 a-b-c

  한번에 한요소값을 순회하려면 values()함수 사용
  key값과 요소값을 모두 순회하려면 items()함수 사용
  
- 집합 {1,2,3} 한번에 한요소씩 순회 1-2-3

- 컨테이너는 대부분 iterable하다
- 이터러블 객체는 반드시 데이터 구조일 필요는 없다(파일을 열어 순회할수 있음)
- 이터러블 객체는 iter()함수를 이용해 iterator로 만들 수 있다


```python
a = [1,2,3]
b = iter(a)
print(type(a))
print(type(b))
print(next(b))
print(next(b))
print(next(b))
```

    <class 'list'>
    <class 'list_iterator'>
    1
    2
    3


- 이터레이터에 next()함수를 적용하여 호출하면 이터레이터는 요소 값을 하나씩 생성해 출력함
- 즉 이터레이터는 이터레이터 객체에 포함된 요소들을 하나씩 생성해서 돌려주는 생성기이다

## iterator



```python
a = [1,2,3]
b = iter(a)
for i in b:
    print(i)
    
    
x = range(10)
type(x)
iter(x)
```

    1
    2
    3





    <range_iterator at 0x2bed7f59f30>



- iterator 자체로 순회가능하다
- range()함수는 iterable 객체를 반환한다

## comprehension

### list comprehension

[표현식 for 변수명 in 이터러블 객체]

- 리스트 생성하는 방법중 하나로 파이썬 코드임


```python
[a for a in range(1,6)]
```




    [1, 2, 3, 4, 5]




```python
[a for a in range(1,6) if a%2 ==1]
```




    [1, 3, 5]




```python
[a**2 for a in range(1,6)]
```




    [1, 4, 9, 16, 25]




```python
list = [(a,b) for a in range(1,4) for b in range(1,3)]
list
```




    [(1, 1), (1, 2), (2, 1), (2, 2), (3, 1), (3, 2)]




```python
list = [(a,b) for a in range(1,4) for b in range(1,3)]
for a1,a2 in list:   #리스트 언패킹
    print(a1,a2)
```

    1 1
    1 2
    2 1
    2 2
    3 1
    3 2


### dictionary comprehension

{key:value for 변수명 in 이터러블 객체}

- 딕셔너리를 생성하는 방법중 하나


```python
a = 'life is short'
b = {i:a.count(i) for i in a}
b
```




    {'l': 1,
     'i': 2,
     'f': 1,
     'e': 1,
     ' ': 2,
     's': 2,
     'h': 1,
     'o': 1,
     'r': 1,
     't': 1}



### set comprehension

{표현식 for 변수명 in 이터러블 객체}

- 집합을 생성하는 방법중 하나


```python
{i for i in range(1,6) if i%2 == 1}
```




    {1, 3, 5}



### tuple comprehension

- 튜플은 컴프리헨션이 없다
- 제너레이터 컴프리헨션

## generator

- 파이썬의 시퀀스를 생성하는 객체 (예: range()함수)
- 이터레이터에 대한 데이터 소스로 자주 이용됨
- 이터레이터에 포함된다

### generator 함수

- 이전에 호출된 값을 기억했다가 다음값을 생성하는 방식으로 순회하는 데이터값 생성
- 일반함수는 기억능력이 없고 항상 첫번째 라인부터 수행
- return이 아닌 yield로 반환값 받음
- 시퀀스들을 메모리에 저장하지 않음(시퀀스를 생성하는 코드임)
- 한번 순회하면 더이상 사용불가


```python
def myrange(a=0,b=10,c=1):
    num = a
    while num < b:
        yield num
        number += c
        
num_seq = myrange(1,20,2)
num_seq
```




    <generator object myrange at 0x000001963EFDB900>



num_seq는 1,3,5,7,....19 시퀀스를 생성하는 객체
즉, num_seq는 1,3,5,7....19 시퀀스를 생성하는 코드를 가지고 있음

### generator comprehension

- 리스트 컴프리헨션은 메모리에 저장되며 얼마든지 재사용가능
- 제너레이터 컴프리헨션은 메모리에 저장되지 않으며 한번 사용하면 더이상 사용불가


```python
[x**2 for x in [1,2,3,4,5]]
```




    [1, 4, 9, 16, 25]




```python
(x**2 for x in[1,2,3,4,5])
```




    <generator object <genexpr> at 0x000001963F16C970>



## lamda 함수

- 이름이 없는 함수
- 보통 한줄이고 return도 없다 단지 인자들과 반환값들의 관계식으로만 표현
- 비교적 간단한 기능의 함수가 컨테이너의 요소로 있는경우 혹은 다른 함수의 인자로 넘겨줄 필요가 있는경우 사용


```python
add = lambda x,y: x+y

add(5,12)
```




    17




```python
sum_mul = [lambda x,y:x+y, lambda x,y:x*y]
sum_mul
```




    [<function __main__.<lambda>(x, y)>, <function __main__.<lambda>(x, y)>]




```python
sum_mul[0](5,7)
```




    12




```python
sum_mul[1](5,7)
```




    35



sum_mul 리스트 객체의 각 요소에 저장된 익명함수 lambda
