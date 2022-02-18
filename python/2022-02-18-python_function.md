# 목차

- [함수](#함수)
  - [input()](#input)
  - [print()](#print)
  - [재귀함수](#재귀함수)
  - [입력인자](#입력인자)

## 함수

def 함수명(입력인자1,입력인자2....):
    명령문1
    .
    .
    .
    명령문k
    return 표현식
    

- 어떤기능을 반복적으로 사용할때 함수를 정의하면 편하다
- 개수에 상관없이 모든 타입의 인자 사용가능
- return값도 개수에 상관없이 모든타입 return 가능
- return값을 정의하지 않으면 none을 반환
- return값이 여러개이고 이를 할당할 변수가 지정되지 않으면 이를 튜플형태로 반환


```python
def a(x,y):
    return x+y, x*y

a(3,4)
```




    (7, 12)



### input()

- 입력되는 모든것을 문자열로 반환

### print()

- 큰 따옴표로 둘러쌓인 문자열은 +연산과 동일


```python
print("life""is""short")
```

    lifeisshort


- print함수 문내의 콤마는 띄어쓰기와 같다


```python
print("life","is","short")
```

    life is short


- 마지막 입력 인자로(end='')를 사용시 줄바꿈 삭제 가능


```python
for a in range(10):
    print(a,end=' ')
```

    0 1 2 3 4 5 6 7 8 9 

### 재귀함수

- 함수안에서 자기 자신을 호출


```python
def a(num):
    if num == 0:    #  종료조건
        return
    print('hi',num)
    num -= 1
    a(num)     # 재귀호출
    
a(3)
```

    hi 3
    hi 2
    hi 1


### 입력인자

#### 위치 인자

- 호출 함수의 인자 값을 순서대로 매개 변수에 복사하여 전달하는 방식
- 인자의 순서를 정확히 알아야함


```python
def dic(a, b, c):
    return{'a':a,'b':b,'c':c}

dic('에이','비','씨')
```




    {'a': '에이', 'b': '비', 'c': '씨'}



#### 키워드 인자

- 위치 인자의 혼동을 피하기 위해 매개 변수에 해당하는 이름을 인자에 지정
- 인자의 순서를 다르게 해도됨


```python
def dic(a, b, c):
    return{'a':a,'b':b,'c':c}

dic(b='비',c='씨',a='에이')
```




    {'a': '에이', 'b': '비', 'c': '씨'}



- 위치 인자와 키워드 인자를 혼용할 때에는 위치 인자를 먼저 쓴다

#### *args

def 함수명(*args):

- 입력 인자들을 튜플 자료형으로 모아 args변수명으로 함수에 전달
- 입력 인자의 개수가 정해지지 않은 경우 사용


```python
def sum(*values):
    a=0
    for i in values:
        a += i
    return a

print(sum(1,2,3,4,5,6,7,8,9,10))
print(sum(1,2,3,4,5))
```

    55
    15


- 일반적인 (입력인자)와 (*입력인자)를 혼합하여 사용하는 경우 (*입력인자)를 뒤에 위치시킨다

#### **kwargs

def 함수명(**kwargs)

- 입력 인자들을 딕셔너리로 모아 kwargs변수명으로 함수에 전달


```python
def dic(**kwargs):
    return kwargs

dic(name='son',age='24')
```




    {'name': 'son', 'age': '24'}



#### 기본값

- 입력 인자 = 기본값 형태
- 함수를 정의할 때 설정
- 다른 인자들에 비해 항상 뒤에 위치


```python
def a(*b,name = 'son'):
    for i in b:
        print(name)
a('a','b','c','d')
```

    son
    son
    son
    son


### decorator

def 함수명1(func):
    def 함수명2(*args, **kwargs)
        추가기능
        func(*args, **kwargs)
        추가기능
        return
    return 함수명2

- 원래 함수의 소스코드를 바꾸지 않고 기능을 더하는 것
- 원래 함수명을 인수로 취하여 추가기능을 가진 새로운 함수를 정의하여 반환


```python
def hi():
    print('hi')
    
def hi2(func):
    def new_func(*args, **kwargs):
        print('start')
        func(*args, **kwargs)
        print('end')
    return new_func

a = hi2(hi)
a()
```

    start
    hi
    end


#### @함수명

- 데코레이터 함수를 정의한 후 원래 함수의 정의구문 위에 '@decorator_함수명' 을 부착해도 된다



```python
def decorator(func):
    def new_func(*args, **kwargs):
        print('start')
        func(*args, **kwargs)
        print('end')
    return new_func


@decorator
def sum(a,b):
    print('a+b=',a+b)

sum(4,5)
```

    start
    a+b= 9
    end

