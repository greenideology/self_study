# 목차

- [클래스](#클래스)
  - [생성자와 self](#생성자와-self)
  - [네임스페이스](#네임스페이스)
    - [class namespace](#class-namespace)
    - [instance namespace](#instance-namespace)
    - [클래스 네임스페이스와 인스턴스 네임스페이스의 관계](#클래스-네임스페이스와-인스턴스-네임스페이스의-관계)
  - [클래스 상속](#클래스-상속)
  - [메소드 오버라이딩](#메소드-오버라이딩)
  - [연산자 오버로딩](#연산자-오버로딩)
- [모듈](#모듈)
  - [__name__변수](#name변수)
  - [sys.path](#syspath)
- [패키지](#패키지)
  - [패키지 안의 모듈](#패키지-안의-모듈)

## 클래스

클래스 생성

class 클래스이름(상속 클래스이름)
    클래스 변수1
    클래스 변수2
    
    def 클래스 함수1
    
    def 클래스 함수2

인스턴스 생성

인스턴스 이름 = 클래스 이름()
    
- 클래스의 필요성: 변수가 늘어남에 따라 변수와 함수를 같이 취급할 수 있는 도구가 필요해짐
- 클래스 변수들을 attribute(속성) 이라고 함
- 클래스내 함수들을 method(메소드)라고 함


```python
class information:
    def __init__(self,name,age,gender):
        self.name = name
        self.age = age
        self.gender = gender
    def infor_card(self):
        print('이름 %s ' %self.name)
        print('나이 %s ' %self.age)
        print('성별 %s ' %self.gender)
        
son = information('mingu','24','male')
kim = information('soyoung','25','female')

son.infor_card()
```

    이름 mingu 
    나이 24 
    성별 male 


- 클래스는 인스턴스를 만드는 틀이며 하나의 클래스로 수많은 인스턴스를 만들 수 있다. 위에서 son 과 kim 은 인스턴스 들이다.
- 인스턴스: 클래스에 의해 생성된 객체

### 생성자와 self

- __init__() 함수는 인스턴스를 만들때 항상 실행되며 클래스 생성자라고 한다
- self는 인스턴스 명(객체 명)을 가리킴


```python
class example_class:
    def __init__(self):
        print('instance created')
        
object = example_class()
```

    instance created



```python
class example_class:
    def __init__(self,name):
        self.name = name
        print(" %s's instance created"%self.name)
        
object = example_class('son')
```

     son's instance created



```python
object.name
```




    'son'



- 클래스에서 메소드의 인자로 self가 먼저오면 인스턴스 메소드라고 함
- 인스턴스가 생성되어 클래스 내의 인스턴스 메소드를 실행하면 메소드의 첫 번째 인자로 self에 인스턴스 명을 대입하여 줌


```python
class example_class:
    def my_class(self):
        print('my class created')
        print(id(self))
    def your_class():
        print('your class created')

object = example_class()
object.your_class()
```


    ---------------------------------------------------------------------------
    
    TypeError                                 Traceback (most recent call last)
    
    ~\AppData\Local\Temp/ipykernel_3316/2129902449.py in <module>
          7 
          8 object = example_class()
    ----> 9 object.your_class()


    TypeError: your_class() takes 0 positional arguments but 1 was given



```python
example_class.your_class()
```

    your class created



```python
id(object)
```




    2620447728112




```python
object.my_class()
```

    my class created
    2620447728112


- id(self)는 self에 할당된 인스턴스의 메모리 주소 값을 프린트하도록 명령

### 네임스페이스

- 유일하고 명확한 이름을 만들고 이를 사용 할 수 있도록 하는 네임 시스템이다
- 예) 김(철수,영희,용만,수용), 최(철수,재만,경수,영철) 에서 김철수는 김씨집안의 네임스페이스고 최철수는 최씨집안의 네임스페이스이다 
  즉 김철수와 최철수는 명확히 구분된다
- class namespace : 클래스가 선언되면 클래스 속성(변수) 및 메소드에 관련된 네임스페이스가 발생되어 인터프리터가 끝날때까지 유지됨
- instance namespace : 클래스가 선언되어 인스턴스가 생성되면 생성된 인스턴스 변수에 관련된 네임스페이스가 발생되어 인터프리터가 끝날때까지 유지됨

#### class namespace

- 클래스가 정의되면 하나의 독립적인 네임스페이스가 생성됨
- 클래스 내에 정의된 변수 혹은 메소드는 클래스 네임스페이스 안에 딕셔너리 타입으로 저장됨


```python
class family:
    nationality = 'korea'
    def __init__(self,name):
        self.name = name
    def family_name(self):
        print('my family name : ', self.name)
        print('my country : ', family.nationality)
        
family.__dict__
```




    mappingproxy({'__module__': '__main__',
                  'nationality': 'korea',
                  '__init__': <function __main__.family.__init__(self, name)>,
                  'family_name': <function __main__.family.family_name(self)>,
                  '__dict__': <attribute '__dict__' of 'family' objects>,
                  '__weakref__': <attribute '__weakref__' of 'family' objects>,
                  '__doc__': None})



#### instance namespace

- 클래스가 정의되고 인스턴스가 생성되면 독립적인 인스턴스 네임스페이스가 생성됨
- 클래스 네임스페이스와 이에 따른 인스턴스 네임스페이스는 밀접한 관계를 유지하면서 동작됨


```python
my_family = family('son')
my_family.__dict__
```




    {'name': 'son'}



#### 클래스 네임스페이스와 인스턴스 네임스페이스의 관계

- 인스턴스 네임스페이스에 없는 변수값이 호출되면 인스턴스가 생성된 클래스 네임스페이스를 탐색하여 해당 변수를 찾음


```python
my_family.nationality
```




    'korea'



- my_family 인스턴스의 네임스페이스에는 nationality라는 변수가 없다 그러므로 클래스 네임스페이스에서 nationality = 'korea'라는 변수를 찾음

- 클래스 내부에 선언된 변수를 클래스 변수라고 하고 클래스 네임스페이스에 위치하게됨
- self.이 붙은 변수를 인스턴스 변수라고 하고 인스턴스 네임스페이스에 위차하게됨
- 인스턴스간에 공유할 필요가 있는 변수는 클래스 변수로 설정하는것이 유리

### 클래스 상속

class 클래스명(부모 클래스명):
    클래스 변수1
    클래스 변수2
    
    메소드1
    메소드2


- 어떤 클래스를 만들때 다른 클래스의 기능을 물려 받을 수 있도록 하는것


```python
class cal1:
    def sum(self,a,b):
        return a+b
class cal2(cal1):
    def sub(self,a,b):
        return a-b
class cal3(cal2):
    def mul(self,a,b):
        return a*b
    
calculation = cal3()
calculation.sum(5,7)
```




    12




```python
calculation.sub(5,7)
```




    -2



### 메소드 오버라이딩

- 상송받은 부모 클래스의 메소드와 이름은 동일하지만 다른 기능이 필요할때 메소드를 재정의하는 기법


```python
class cal4(cal3):
    def mul(self,a,b):
        return a/b
    
calculation = cal4()
calculation.mul(6,3)
```




    2.0



### 연산자 오버로딩

- 특수 메소드를 통해 객체가 객체 연산자(+ - * /)등을 사용하여 특수메소드에서 정의된 특정 기능을 수행하도록 하는 기법

## 모듈

1. import 모듈이름 --> 모듈이름.함수이름
2. from 모듈이름 import 모듈함수 --> 함수이름
3. from 모듈이름 import * --> 함수이름

- 파이썬 파일로 코드의 재사용을 위한것
- 파이썬 프로그램에서 불러와 사용할 수 있도록 만들어진 파일 

### __name__변수


- 파이썬 자체에서 사용하는 변수
- 파이썬 파일이 직접실행된것인지 다른 프로그램에서 임포트 된것인지를 확인하는 용도
- 직접실행 --> __main__을 바인딩
- 임포트한 경우 자신의 파일명을 바인딩


```python
print(__name__)
```

    __main__



```python
def sum(a,b):
    print(a+b)

sum(5,3)
```

    8


위 코드를 모듈로 만들고 import를 하면 다음과 같이 sum(5,3)이 자동으로 실행된다 이를 방지하기위해 __name__ 변수를 사용할 수 있다


```python
def sum(a,b):
    print(a+b)

if __name__ == 'main__':
    sum(5,3)
```

### sys.path

- 파이썬 라이브러리들이 선치된 디렉터리를 리스트 형태로 담고 있는 특수 변수임
- 모듈이 저장된 디렉터리를 path에 추가 하면 어느곳에서나 모듈을 임포트 할 수 있음


```python
import sys

sys.path.append('C:\\Python')
```


```python
sys.path
```




    ['C:\\Users\\gusrn\\Compute Science\\Python_basic',
     'C:\\Users\\gusrn\\anaconda3\\python39.zip',
     'C:\\Users\\gusrn\\anaconda3\\DLLs',
     'C:\\Users\\gusrn\\anaconda3\\lib',
     'C:\\Users\\gusrn\\anaconda3',
     '',
     'C:\\Users\\gusrn\\anaconda3\\lib\\site-packages',
     'C:\\Users\\gusrn\\anaconda3\\lib\\site-packages\\locket-0.2.1-py3.9.egg',
     'C:\\Users\\gusrn\\anaconda3\\lib\\site-packages\\win32',
     'C:\\Users\\gusrn\\anaconda3\\lib\\site-packages\\win32\\lib',
     'C:\\Users\\gusrn\\anaconda3\\lib\\site-packages\\Pythonwin',
     'C:\\Users\\gusrn\\anaconda3\\lib\\site-packages\\IPython\\extensions',
     'C:\\Users\\gusrn\\.ipython',
     'C:\\Python']



## 패키지

- 모듈을 계층적으로 관리함으로서 공동작업이나 유지 보수등을 효율적으로 할 수 있도록 해놓은 묶음
- 디렉터리와 모듈로 구성됨
- 디렉터리에 __init__.py 파일이 있으면 그 디렉터리를 패키지로 인식함
  ![패키지구조](https://github.com/greenideology/self_study/blob/main/picture/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7(4).png)
  
### 패키지 안의 모듈

1. import a.b.c

   a,b는 패키지이름 c는 (마지막은) 모듈명이 되어야함

   예) import Lecture.History.Korea
   사용) Lecture.History.Korea.함수()
  
2. from a.b import 모듈명
   사용) 모듈명.함수()

3. from a.b.모듈명 import 함수명
   사용) 함수명()
   
4. from a.b import *
   사용) 모듈명.함수()
   
   b는 패키지명이며 디렉터리 b에 있는 __init__.py파일은 반드시 다음 명령문을 포함해야한다
   __all__ = ['모듈명']
   
5. from a.b.모듈명 import *
   사용) 함수()
