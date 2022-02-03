# 목차

- [숫자 자료형(number)](#01 숫자 자료형)
  - [정수(integer)](#정수)
  - [실수(floating point)](#실수)
  - [복소수(complex number)](#복소수)
  - [2진수(binary number)](# 2진수)
  - [8진수(octal number)](#8진수)
  - [16진수(hexadecial number)](#16진수)
  - [연산자](#연산자)

- [문자열 자료형(string)](#02 문자열 자료형)
  - [문자열 표현방식 4가지](#문자열 표현방식 4가지)
  - [이스케이프 문자](#이스케이프 문자)
  - [문자열 연산](#문자열 연산)
  - [문자열 인덱싱](#문자열 인덱싱)
  - [문자열 슬라이싱](#문자열 슬라이싱)
  - [문자열 포매팅](#문자열 포매팅)
  - [문자열 관련 함수](#문자열 관련 함수)
- [리스트(list)](#03 리스트)
  - [list()](#list())
  - [리스트의 인덱싱 슬라이싱](#리스트의 인덱싱 슬라이싱)
  - [요소 바꾸기](#요소 바꾸기)
  - [리스트 연산](#리스트 연산)
  - [리스트 관련 함수](#리스트 관련 함수)
- [튜플(tuple)](#04 튜플)
  - [tuple()](# tuple())
  - [튜플의 인덱싱 슬라이싱](#튜플의 인덱싱 슬라이싱)
  - [언패킹](#언패킹)
  - [값교환](#값교환 )
- [딕셔너리(dictionary)](#05 딕셔너리)
  - [dict()](#dict())
  - [요소 바꾸기](#요소 바꾸기)
  - [딕셔너리 관련 함수](#딕셔너리 관련 함수)
- [집합(set)](#06 집합)
  - [set()](#set())
  - [집합 연산](#집합 연산)
  - [집합 관련 함수](#집합 관련 함수)

# 파이썬 자료형



##  01 숫자 자료형

### 정수

- 1,2,3,5....

### 실수

- 1.537, 4.237435 ............

- 소수점 표현 방식에는 2가지가 있다.

  -고정 소수점: 1.2345 (움직이지 않고 고정된 소수점)
  (fixed point)

  -부동 소수점: 123.45*10^-2 or 12.345*10-1 (고정되지 않고 움직이는 소수점, 한개의 숫자를 여러 방식으로 표현 가능)
  (floating point)
  
### 복소수

- 2-3j, 2.0+4j........
  (파이썬에서는 허수 i를 j로 나타낸다.)

- 복소수 관련함수


```python
Z = 2+3j
print(Z.real)
print(Z.imag)
print(Z.conjugate())
```

    2.0
    3.0
    (2-3j)


Z.real  ---> 2.0 (복소수의 실수부분을 리턴)   

Z.imag ---> 3.0 (복소수의 허수부분을 리턴)

Z.conjugate() ---> 2-3j (켤례복소수를 리턴)

###  2진수

- 0b11, 0B10 ......
  (0b 혹은 0B 뒤에 0,1로 숫자를 표현)

### 8진수

- 0o13, 0o47......
   (0o 혹은 0O 뒤에 0~7로 숫자를 표현)
   
### 16진수

- 0xF, 0XEF......
  (0x 혹은 0X 뒤에 0~9,A~F로 숫자를 표현....A는10 F는15)
  
### 연산자

- '+' , - , *, /  각각 더하기, 빼기, 곱하기, 나누기

- //  나눈 값의 정수부분 구하기
  45.5//25 ---> 1.0
   (계산 과정에 실수가 포함되면 결과도 실수로 나온다.)
  
- % 나머지 구하기
  45%4 ---> 1
  
- ** 지수 
  2**5 ---> 32
  
- =할당하기
  A=3 ---> 3이라는 객체를 생성하고 A는 그 객체를 가리킨다. 절대 A와 3이 같다는 뜻이 아님
  예) A = 3 , B = 3 이면 3이라는 1개의 객체를 A와 B가 가리키고 있는것
  
- == 같음
  2 == 2 

- = 와 연산자의 결합
  A = A* 3을 A*=3으로 표현 가능

  예) a +=1 은  a = a+1 과 같다.
      a * =1 은  a = a* 1 과 같다.
      
      
      
## 02 문자열 자료형

### 문자열 표현방식 4가지

    'hello'
    "hello"
    '''hello'''
    """hello"""

### 이스케이프 문자

    \n 줄바꿈    \r 커서를 현재줄 맨 앞으로 이동    \\ \문자 그대로를 표현
    \' '표현     \a 벨소리
    \" "표현     \b 백스페이스

### 문자열 연산


```python
print('-'*50)
```

    --------------------------------------------------


### 문자열 인덱싱

- 문자열에서 문자의 위치를 정수로 나타낸것


```python
a = "Life is short"
     
#   0123456789101112
# -13-12-11-10-9-8-7-6-5-4-3-2-1

print(a[1])
```

    i


- 파이썬 인덱싱은 0부터 시작, 띄어쓰기도 셈

- 역방향 시작 가능(-1부터 시작)

- 0은 -0 과 같음

### 문자열 슬라이싱

- 문자열에서 일정한 길이를 한번에 뽑아낼때 사용


```python
a = 'Life is short'
print(a[0:4])
print(a[:4])
print(a[:])
print(a[0:8:2])
print(a[8:-1])
print(a[::-1])
```

    Life
    Life
    Life is short
    Lf s
    shor
    trohs si efiL


- a[시작:끝:step] 형식으로 사용(시작 숫자 이상 끝숫자 미만까지 step단위로 띄어서 자른다)

- 시작숫자가 생략될시 처음부터, 끝숫자가 생략될시 끝까지, step이 생략될시 띄어서 자르는거 없이 슬라이싱 한다.

### 문자열 포매팅

- 문자열에서 특정부분만 바꾸고 싶을때 사용

      %s 문자열    %o 8진수
      %c 문자 1개  %x 16진수
      %d 정수      %% %그 자체를 표현
      %f 실수


```python
print('온도는 %d도 습도는 %d 입니다.'%(11,23))
```

    온도는 11도 습도는 23 입니다.


    %10d ---> 10자리 오른쪽 정렬
    %10.2f ---> 10자리 오른쪽 정렬 소수점 2째 자리까지 표현
    %-10.2f ---> 10자리 왼쪽 정렬 소수점 2째 자리까지 표현


```python
print('온도는%10d'%23.123)
print('온도는%10.2d'%23.123)
print('온도는%-10d'%23.123)
```

    온도는        23
    온도는        23
    온도는23        


### 문자열 관련 함수


```python
a = 'Life is short'
print(a.count('i')) 
print(a.find('f')) 
print(a.index('f')) 
print('/'.join(a))
print(a.upper()) 
print(a.lower()) 
print(a.capitalize()) 
print(a.replace('short','long'))
print(a.split()) 
print(a.split('i')) 
print(len(a))
```

    2
    2
    2
    L/i/f/e/ /i/s/ /s/h/o/r/t
    LIFE IS SHORT
    life is short
    Life is short
    Life is long
    ['Life', 'is', 'short']
    ['L', 'fe ', 's short']
    13


a.count('문자'): a문자열에 포함된 문자의 개수를 정수로 반환

  (a는 문자열이여야 함)

a.find('문자'): a문자열에 포함된 문자의 위치를 index 번호로 반환(없으면 -1 반환)

a.index('문자'): a문자열에 포함된 문자의 위치를 index 번호로 반환(없으면 오류)

string.join(a): string 문자열을 a문자열에 끼워넣기

a.upper(): 소문자를 대문자로 변환

a.lower(): 대문자를 소문자로 변환

a.capitalize(): 첫번째 문자를 대문자로변환

a.lstrip(), a.rstrip(), a.strip(): 각각 a문자열의 왼쪽, 오른쪽, 양쪽 공백 지우기

a.replace('문자열1','문자열2'): a 문자열에서 문자열1을 문자열2로 바꾸기

a.split(): 공백,탭,엔터를 기준으로 a문자열을 분리하여 리스트 자료형으로 반환

a.split(''): ''안의 값을 기준으로  a문자열을 분리하여 리스트 자료형으로 반환

*len(a): a문자열의 길이를 정수로 반환(문자열만의 함수는 아님)



***

1.시퀀스란?

연속적으로 값이 증가하거나 감소하는 요소들로 구성되는 데이터들

예)

1,2,3,4,......

a,b,c,d......

-1,-2,-3.......

"python"

2.파이썬의 2가지 시퀀스 자료형: 리스트, 튜플




## 03 리스트

- [요소1,요소2,요소3.....] 으로 표현

- 리스트의 요소는 0개 이상이다.

- 리스트의 요소는 서로 다른 자료형이 될 수 있다.

### list()


```python
L = list()
print(L)
a = list('python')
print(a)
```

    []
    ['p', 'y', 't', 'h', 'o', 'n']


### 리스트의 인덱싱 슬라이싱

문자열과 인덱싱, 슬라이싱 규칙 동일


```python
a = [['kim', 'park', 3], 'name', '1999']
print(a[2])
print(a[0])
print(a[0][1])
print(a[::2])
print(a[::-2])
```

    1999
    ['kim', 'park', 3]
    park
    [['kim', 'park', 3], '1999']
    ['1999', ['kim', 'park', 3]]


### 요소 바꾸기

a[m] = 요소1


```python
a = [['kim', 'park', 3], 'name', '1999']
a[0] = 1
print(a)
```

    [1, 'name', '1999']


### 리스트 연산


```python
a = [1,2,3,4]
b = [3,4,5,6]
print(a+b)
print(a*3)
```

    [1, 2, 3, 4, 3, 4, 5, 6]
    [1, 2, 3, 4, 1, 2, 3, 4, 1, 2, 3, 4]


### 리스트 관련 함수


```python
a = ['mangu',1999]
a.append('year') 
print(a) 
a.insert(1,'name') 
print(a) 
b = [1,2,3,4] 
a.extend(b) 
print(a) 
print(a.count(2)) 
```

    ['mangu', 1999, 'year']
    ['mangu', 'name', 1999, 'year']
    ['mangu', 'name', 1999, 'year', 1, 2, 3, 4]
    1


a.append(요소1): a리스트의 끝에 요소1을 추가

  (a는 리스트)

a.insert(m,요소1): a리스트에 원하는 자리(m)에 요소1을 추가

a.extend(b): a리스트와 b리스트를 병합(리스트의 더하기연산과 같음)

a.count(n): a리스트 내의 요소값n 의 개수

a.sort(): 리스트를 알파벳순or 오름차순으로 정렬(요소들의 자료형이 동일해야함)

   a.sort(reverse=True): 리스트를 알파벳순or 오름차순의 역순으로 정렬(요소들의 자료형이 동일해야함)


## 04 튜플

- (요소1, 요소2, 요소3...)으로 표현

- 튜플과 리스트는 거의같다


- 튜플과 리스트의 다른점

  - 괄호는 생략해도 된다

  - 구성요소가 하나일 경우 뒤에 콤마(,)를 반드시 붙인다

    (a=1과 a=1, 은 다름)

  - 요소값을 바꿀 수 없다

  - 튜플은 적은 메모리 공간을 차지한다
  
### tuple()


```python
a = tuple('python')
print(a)
```

    ('p', 'y', 't', 'h', 'o', 'n')


### 튜플의 인덱싱 슬라이싱

리스트와 동일

### 언패킹

튜플의 요소들에 대해 여러개의 변수를 할당


```python
unpack = ['name','year',25],'hi','python'
a,b,c = unpack
print(a) 
print(b) 
print(c) 
```

    ['name', 'year', 25]
    hi
    python


### 값교환 

튜플이 아니여도 사용 가능


```python
a = 'kim',
b = 'park',
a,b = b,a
print(a) 
print(b) 
```

    ('park',)
    ('kim',)


## 05 딕셔너리


- {key1:component1, key2:component2...........}로 표현한다

- 리스트와 유사하나 순서를 따지지 않는다

- key는 불변하는 어떤 자료형이든 들어갈 수 있다(리스트는 불가)

- key는 유일해야 한다

- 딕셔너리의 'key:component'값은 변경할 수 있다(추가,삭제,수정 가능)

### dict()


```python
a = [['year',1999],['name','son']]
b = dict(a)
print(b) 
```

    {'year': 1999, 'name': 'son'}


단 두값이 쌍으로 이루어진 자료여야 함(하나는 key, 하나는 component로 변환 해줌)

### 요소 바꾸기

key를 이용한 딕셔러니 요소 변경하기


```python
b = {'year': 1999, 'name': 'son'}
b['name'] = 'kim'
print(b) 
```

    {'year': 1999, 'name': 'kim'}


a[key1] = 요소1

a딕셔너리의 key1 에 해당하는 요소를 요소1로 바꾼다

key1이 없을시 딕셔너리에 'key1:요소1' 값을 a딕셔너리에 추가한다

### 딕셔너리 관련 함수


```python
a = {'year': 1999, 'name': 'son'}
b = {'job': 'unemployed', 'name': 'kim'}
a.update(b)
print(a) 
print(a['year']) 
print(a.keys()) 
print(a.values()) 
print(a.items()) 
c = a.copy()  #---> {'year': 1999, 'name': 'kim', 'job': 'unemployed'} #c와a는 서로 다른 객체를 가리킴#
print(c) 
del c['year']
print(c)
print(c.clear())
```

    {'year': 1999, 'name': 'kim', 'job': 'unemployed'}
    1999
    dict_keys(['year', 'name', 'job'])
    dict_values([1999, 'kim', 'unemployed'])
    dict_items([('year', 1999), ('name', 'kim'), ('job', 'unemployed')])
    {'year': 1999, 'name': 'kim', 'job': 'unemployed'}
    {'name': 'kim', 'job': 'unemployed'}
    None


a.update(b): 딕셔너리 a와 딕셔너리 b를 합침(만약, a와b에 같은 key값이 있다면 마지막 딕셔너리 요소 값이 생존한다)

 (a는 딕셔너리임)

a[key]: a딕셔너리의 key에 해당하는 요소값을 반환(key값이 없을시 에러)

a.get(key): a딕셔너리의 key에 해당하는 요소값을 반환(key값이 없을시 none 반환)

a.keys(): a딕셔너리의 모든 key값 출력

a.values(): a딕셔너리의 모든 value값(요소값) 출력

a.items(): a딕셔너리의 모든 key와 요소값을 튜플로 출력

a.copy(): a딕셔너리를(객체를) 복사(새로운 객체를 메모리 공간에 생성)

a.pop(key1,X): a딕셔너리의 key1에 해당하는 요소를 a에서 뽑아내어 반환(key1 값이 없으면 X를 반환, X를 설정 안하면 오류메세지)

del.a[key]: a딕셔너리의 key에 해당하는 key와 요소를 삭제

a.clear(): 모든 항목 삭제


## 06 집합

- {요소1, 요소2, 요소3.....}으로 표현

- 중복을 허용하지 않는다

- 순서가 없다(인덱싱 불가)

### set()

- 빈 집합은 {}으로 표현하지 않고 set()으로 표현한다   ({}은 빈 딕셔너리 표현이다)


```python
a = set('letter')
print(a)

a = set(['hi','python',1,2])
print(a)

a = set({'apple':'red', 'melon':'green', 'orange':'yellow'})
print(a)
```

    {'t', 'l', 'r', 'e'}
    {'hi', 2, 'python', 1}
    {'apple', 'melon', 'orange'}


### 집합 연산


```python
a = {1,2,3,4,5,6}
b = {4,5,6,7,8,9}

print(a&b)
print(a|b)
print(a-b)
print(a^b)
```

    {4, 5, 6}
    {1, 2, 3, 4, 5, 6, 7, 8, 9}
    {1, 2, 3}


& 교집합
| 합집합
'-' 차집합
^ 교집합의 여집합

### 집합 관련 함수


```python
a = {1,2,3,4,5,6}
b = {4,5,6,7,8,9}

a.add(7)
print(a)

a.update(b)
print(a)

a.remove(7)
print(a)
```

    {1, 2, 3, 4, 5, 6, 7}
    {1, 2, 3, 4, 5, 6, 7, 8, 9}
    {1, 2, 3, 4, 5, 6, 8, 9}


add() 집합에 요소1개 추가

update 집합에 요소 여러개 추가

remove() 특정 요소값 제거
