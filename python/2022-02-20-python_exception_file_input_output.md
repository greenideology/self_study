# 목차

- [예외처리](#예외처리)
  - [try...except 명령문](#tryexcept-명령문)
  - [새로운 예외 만들기](#새로운-예외-만들기)
- [파일 입출력](#파일-입출력)
  - [파일 열고 쓰고 닫기](#파일-열고-쓰고-닫기)
  - [파일 내용읽기](#파일-내용읽기)

## 예외처리

- 프로그램에서 오류 발생시 오류를 핸들링 하는 기능
- 프로그램 실행시 발생할 수 있는 오류를 사용자에게 알려주고 프로그램을 종료할 수 있도록 하는 기능
- try except문을 사용

### try...except 명령문

try:
    명령문1
    명령문2
except 예외타입1 as 예외변수1:
    예외처리 명령문1
    예외처리 명령문2
except 예외타입2 as 예외변수1:
    예외처리 명령문1
    예외처리 명령문2
else:
    예외처리 명령문1
    예외처리 명령문2
finally:
    항상 수행할 명령문
    
    

- try 블록 내의 명령문에서 오류 발생시 except문으로 이동하여 예외 처리함
- try 블록 내의 명령문에서 오류 발생 여부와 관계없이 finally문은 항상 마지막에 실행됨
- finally문은 없어도됨
- else블록은 오류 발생시에 실행이 되지 않고 오류가 없으면 실행됨


```python
a = [1,2,3]
a[4]
```


    ---------------------------------------------------------------------------
    
    IndexError                                Traceback (most recent call last)
    
    ~\AppData\Local\Temp/ipykernel_10688/571634228.py in <module>
          1 a = [1,2,3]
    ----> 2 a[4]


    IndexError: list index out of range


위에서 IndexError 는 예외 타입임


```python
a = [1,2,3,4,5]
b = 5
try:
    a[b]
except IndexError as c:
    print('there is no index\n''errormessage: ',str(c))
finally:
    print(a[b-1])
```

    there is no index
    errormessage:  list index out of range
    5


c는 에러메세지를 담고 있는 변수

### 새로운 예외 만들기

class 새로운 예외타입 명(Exception):
    명령문1
    명령문2

raise 예외타입 명(오류메세지)

- 모든 예외는 클래스 객체 타입으로 정의됨
- 모든 예외 클래스는 exception 클래스를 부모 클래스로 가짐
- raise 문을 이용해 강제로 오류를 발생시킬 수 있음


```python
class lowercase(Exception):
    pass
a = ['A','B','C','d']
for word in a:
    if word.islower():
        raise lowercase('this word is lowercase: '+word)
```


    ---------------------------------------------------------------------------
    
    lowercase                                 Traceback (most recent call last)
    
    ~\AppData\Local\Temp/ipykernel_10688/2230997868.py in <module>
          4 for word in a:
          5     if word.islower():
    ----> 6         raise lowercase('this word is lowercase: '+word)


    lowercase: this word is lowercase: d


## 파일 입출력

### 파일 열고 쓰고 닫기

1. 파일 객체 = open('파일이름','열기모드')
2. with open('파일이름','열기모드') as 파일 객체
      명령문1
      명령문2


- open(): 파일을 열어주는 내장함수
- close(): 파일을 닫아주는 내장함수
- write(): 파일에 내용을 써주는 내장함수
- 입력값으로 파일 이름과 모드를 받고 파일을 연 후 파일 객체를 반환

- 예) f = open('agsdh.txt','wt')

- <앞글자>
  r 읽기 모드
  w 쓰기모드(이전내용 지워짐)
  x 쓰기모드(파일이 존재하지 않을때 새로 생성)
  a 추가모드(파일의 마지막에 새로운 내용을 추가)
  
- <뒤글자>
  t 텍스트타입(생략가능)
  b 이진 타입


```python
f = open(r'C:\Users\gusrn\Desktop\손민구\프로그래밍\computer science\예시파일.txt','w')
for number in range(1,5):
    f.write('%d 번째 응시자입니다\n'%number)
f.close()
```

### 파일 내용읽기

- read() 열려있는 파일 객체로부터 한번에 모든 라인을 읽어 전체 내용을 문자열로 반환
- readline() 열려있는 파일 객체로부터 한줄씩 읽어 내용을 반환하고 내용이 없으면 none을 반환
- readlines() 열려있는 파일 객체로부터 한번에 모든 라인을 읽고 한 라인의 문자열을 요소값으로 하는 리스트를 반환


```python
f = open(r'C:\Users\gusrn\Desktop\손민구\프로그래밍\computer science\예시파일.txt','r')
while True:
    line = f.readline()
    if not line:
        break
    print(line)
```

    1 번째 응시자입니다
    
    2 번째 응시자입니다
    
    3 번째 응시자입니다
    
    4 번째 응시자입니다


​    


```python
f = open(r'C:\Users\gusrn\Desktop\손민구\프로그래밍\computer science\예시파일.txt','r')
lines = f.readlines()
lines
```




    ['1 번째 응시자입니다\n', '2 번째 응시자입니다\n', '3 번째 응시자입니다\n', '4 번째 응시자입니다\n']




```python
f = open(r'C:\Users\gusrn\Desktop\손민구\프로그래밍\computer science\예시파일.txt','r')
lines = f.read()
lines
```




    '1 번째 응시자입니다\n2 번째 응시자입니다\n3 번째 응시자입니다\n4 번째 응시자입니다\n'

