# 목차

- [주요 내장 함수](#주요-내장-함수)
  - [dir(object)](#dirobject)
  - [enumerate()](#enumerate)
  - [eval(실행 가능한 문자열)](#eval실행-가능한-문자열)
  - [filter(함수,iterable)](#filter함수iterable)
  - [id(object)](#idobject)
  - [map(함수,iterable)](#map함수iterable)
  - [max(iterable),min(iterable)](#maxiterableminiterable)
  - [sorted(iterable)](#sortediterable)
  - [zip()](#zip)
- [주요 외장 함수](#주요-외장-함수)
  - [sys 모듈](#sys-모듈)
  - [pickle 모듈](#pickle-모듈)
  - [os 모듈](#os-모듈)
    - [os.getcwd()](#osgetcwd)
    - [os.chdir(디렉터리)](#oschdir디렉터리)
    - [os.mkdir(디렉터리)](#osmkdir디렉터리)
    - [os.rmdir(디렉터리)](#osrmdir디렉터리)
    - [os.rename(src,dst)](#osrenamesrcdst)
  - [time 모듈](#time-모듈)
    - [time.time()](#timetime)
    - [time.localtime(time.time())](#timelocaltimetimetime)
    - [time.ctime()](#timectime)
  - [random 모듈](#random-모듈)
    - [random.random()](#randomrandom)
    - [random.randint(a,b)](#randomrandintab)
    - [random.choice()](#randomchoice)
    - [random.shuffle()](#randomshuffle)

## 주요 내장 함수

###  dir(object) 

- 객체와 관련된 함수 혹은 변수들을 리스트로 보여줌


```python
dir([1,2,3])
```




    ['__add__',
     '__class__',
     '__class_getitem__',
     '__contains__',
     '__delattr__',
     '__delitem__',
     '__dir__',
     '__doc__',
     '__eq__',
     '__format__',
     '__ge__',
     '__getattribute__',
     '__getitem__',
     '__gt__',
     '__hash__',
     '__iadd__',
     '__imul__',
     '__init__',
     '__init_subclass__',
     '__iter__',
     '__le__',
     '__len__',
     '__lt__',
     '__mul__',
     '__ne__',
     '__new__',
     '__reduce__',
     '__reduce_ex__',
     '__repr__',
     '__reversed__',
     '__rmul__',
     '__setattr__',
     '__setitem__',
     '__sizeof__',
     '__str__',
     '__subclasshook__',
     'append',
     'clear',
     'copy',
     'count',
     'extend',
     'index',
     'insert',
     'pop',
     'remove',
     'reverse',
     'sort']



### enumerate() 

- 리스트, 튜플과 같이 순서(index)가 있는 자료형을 입력으로 받아 인덱스 값과 그 인덱스 값에 해당하는 요소를 차례로 반환


```python
for index,value in enumerate(['a','b','c']):
    print(index,value)
```

    0 a
    1 b
    2 c


### eval(실행 가능한 문자열)  

- 실행 가능한 문자열을 입력으로 받아 이를 실행한 후 그 결과를 반환


```python
eval('sum(range(1,11))')
```




    55



### filter(함수,iterable) 

- 이터러블 객체의 요소들이 첫 번째 인자인 함수에 입력인자로 들어갔을 때 출력되는 값 중에서 참인 것만을 걸러내어(fitering) 반환해줌


```python
def a(x):
    return x<0

print(list(filter(a,[1,5,-12,53,-4,7,-9])))
```

    [-12, -4, -9]


### id(object)

- 객체의 주소값을 출력해줌


```python
a = 123
b = 123

print(id(a),id(b))
```

    2438860331184 2438860331184


### map(함수,iterable)

- 이터러블 객체의 요소 값을 함수에 입력 인자로 넣어 출력되는 값을 묶어 반환


```python
def square(x):
    return x**2

list(map(square,[1,2,3,4,5]))
```




    [1, 4, 9, 16, 25]



### max(iterable),min(iterable)

- 이터러블 객체의 요소값중 최대,최소값을 반환

### sorted(iterable)

- 이터러블 객체의 요소값을 오름차순으로 정령하여 리스트로 반환


```python
sorted((5,2,4,3,1))
```




    [1, 2, 3, 4, 5]



### zip()

- 동일한 개수로 이루어진 자료형들에 대해 같은 index를 갖는 요소들을 튜플로 묶어 반환


```python
a = [1,2,3]
b = ('a','b','c')
c = ('ㄱ','ㄴ','ㄷ')

list(zip(a,b,c))
```




    [(1, 'a', 'ㄱ'), (2, 'b', 'ㄴ'), (3, 'c', 'ㄷ')]



## 주요 외장 함수

### sys 모듈

- sys.argv 명령창에서 입력된 인수들을 sys.argv에 리스트로 전달


```python
import sys

sys.argv
```




    ['C:\\Users\\gusrn\\anaconda3\\lib\\site-packages\\ipykernel_launcher.py',
     '-f',
     'C:\\Users\\gusrn\\AppData\\Roaming\\jupyter\\runtime\\kernel-d96e09ba-be32-4558-911c-f6c05c1e60f3.json']



### pickle 모듈

- 객체의 형태를 그대로 유지하면서 파일을 저장(dump)하거나 불러올 수(load) 있도록 하는 모듈


```python
import pickle
f = open(r'C:\Users\gusrn\Desktop\손민구\프로그래밍\computer science\예시파일.txt','wb')
data = {1:'a', 2:'b'}
pickle.dump(data,f)
f.close()
```


```python
f=open(r'C:\Users\gusrn\Desktop\손민구\프로그래밍\computer science\예시파일.txt','rb')
data1 = pickle.load(f)
print(data1)
```

    {1: 'a', 2: 'b'}


### os 모듈

- 환경변수, 디렉터리, 파일등의 os자원을 제어할 수 있도록 해주는 모듈

#### os.getcwd() 

- 현재 자신의 디렉터리 위치를 리턴

#### os.chdir(디렉터리) 

- 현재 디렉터리를 변경

#### os.mkdir(디렉터리)

- 디렉터리 생성

#### os.rmdir(디렉터리)

- 디렉터리 삭제(단, 디렉터리가 비어있어야함)

#### os.rename(src,dst)

- src라는 이름의 파일을 dst라는 이름으로 바꿈


```python
import os

os.getcwd()
```




    'C:\\Users\\gusrn\\Compute Science\\Python_basic'



### time 모듈

#### time.time()

- 세계표준시를 이용해 1970년 1월 1일 0시를 기준으로 지난 시간을 초단위로 리턴

#### time.localtime(time.time())

- time.time()에 의해 반환된 실수 값을 이용해 연,월,일,시,분,초의 형태(튜플)로 바꾸어주는 함수

#### time.ctime()

- 현재 시간만 반환

### random 모듈

#### random.random()

- 0.0~1.0 사이의 난수 발생


```python
import random

random.random()
```




    0.19271103051801708



#### random.randint(a,b)

- a~b 사이의 정수 난수 발생


```python
random.randint(0,10)
```




    0



#### random.choice()

- 입력으로 받은 리스트에서 무작위로 하나를 선택하여 반환


```python
a = [12,13,14,15,16]
random.choice(a)
```




    15



#### random.shuffle()

- 리스트의 항목을 무작위로 섞어 반환


```python
random.shuffle(a)
a
```




    [14, 16, 15, 12, 13]

