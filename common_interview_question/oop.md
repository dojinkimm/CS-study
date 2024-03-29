# OOP란? 

## 들어가기 앞서
OOP를 설명하기 이전에 Prodcedural programming을 설명을 먼저 해보려고 한다. 

Procedural programming language중 우리가 흔하게 접할 수 있는 언어는 C이다. C의 프로그램을 보면 많은 Function(함수)들과 variables(변수)들로 이뤄져있다. 프로그램의 크기가 작을 때는 정상적으로 작동하지만 만약에 프로그램의 크기가 커지게 되면 함수들과 변수들의 수가 너무 많아져서 매우 복잡해진다. 

<img src="images/oop1.png"/>


특히, 함수들간에 변수를 공유하던지 서로 호출하는 관계일 때 한 함수의 내용을 수정하면 다른 함수의 내용도 수정해야 하는 상황이 발생한다.

<img src="images/oop2.png"/>


# OOP란?

OOP는 이 때 이 문제를 해결하고자 고안된 programming 방법이다. OOP를 제 나름대로 간략하게 설명하면 서로 연관이 있는 함수나 변수들을 하나의 그룹(객체,object)로 만드는 것이다. 이 object 안에 있는 function(함수)의 이름을 **`Method`** 그리고 object 안에 있는 variable(변수)의 이름을 **`Property`**라고 부른다. 

<img src="images/oop3.png"/>


# OOP의 특성

이제는 OOP의 장점이 무엇이고 어떠한 특성을 가지고 있는지 알아보고자 한다. OOP의 중요한 특성을 꼽으라면 다음의 4가지가 대표적으로 꼽힌다 : Encapsulation, Abstraction, Inheritance, Polymorphism.

### 1. Encapsulation (캡슐화)

다음의 코드를 한번 보자.

```python
def multiply(a, root_two, pi):
    return a * b * pi
    
a = 10
root_two = 1.414212
pi = 3.141592653
result = multiply_pi(a,root_two,pi)
print("Result is", result)
```

```python
class Calculator:
    pi = 3.141592653
    root_two = 1.414212
    
    def __init__(self,a):
        self.a = a
        return

    def multiply_pi(self):
        return self.a * self.root_two * self.pi
    
    
calculator = Calculator(10)
result = calculator.multiply_pi()
print("Result is", result)
```

첫 번째 코드는 encapsulation을 하지 않았고 두 번째 코드는 object를 사용해서 encapsulation을 이뤄졌다. Encapsulation이 안된 코드를 보면 전달되는 parameter가 더 많은 것을 알 수 있다. 

Clean Code의 저자 Uncle Bob은 다음과 같이 말을 했다 "Avoid Too Many Arguments In Functions". 즉, 함수에 너무 많은 parameter를 전달하는 것은 가독성도 떨어지게 되고 내가 관리해야할 변수가 많아진다는 의미이기도 하다. 

Encapsulation은 프로그래밍을 덜 복잡하게 만들어준다. 예를 들어, pi의 값, root 2의 값을 매번 찾아서 쓰려고 하면 가끔씩 오타가 날 수 있고 잘못된 숫자를 작성할 수 있다. 하지만, encapsulation은 모든 함수들과 변수들이 object안에 있고 이미 정의돼있는 상태이기 때문에 그 값은 항상 일정하다. 또한, 안에 변수들 값을 private으로 설정을 하면 외부에서 변수를 변경할 수 없게 되기 때문에 값이 항상 일정할 것이라는 걸 보장할 수 있다. 

### 2. Abstraction(추상화)

Abstraction은 유저가 object의 내부를 알 필요가 없다는 의미이다. 현실적인 예시를 들자면, 여름에 에어컨을 켜서 시원한 바람이 나오게 하려면 리모컨으로 on 만 누르면 된다. 내부적으로 어떻게 공기가 시원해지는지 유저는 알 필요가 하나도 없다. OOP에서도 이와 유사하다. 원의 크기, 혹은 넓이를 구하는 method를 호출했으면 그에 대한 결과물을 리턴해줄 것이고, 어떤 방식으로 계산이 됐는지 유저는 알 필요가 없다. 

### 3. Inheritance(상속)

Inheritance는 반복적인 코드를 제거하는데 도움을 준다. 사칙연산만 하는 일반 계산기가 있고 사칙연산 뿐만 아니라, root, sin, cos가 다 들어있는 공학용 계산기가 있다고 가정해보자. 공학용 계산기는 이 때 일반 계산기의 기능을 상속받는 것이다. 즉, 일반 계산기에 있는 모든 기능들을 공학용 계산기에서 사용할 수 있는 것이다. 상속이 없었더라면, 똑같은 사칙연산 기능을 공학용 계산기에 삽입했을 것이고 이때문에 코드의 길이가 늘어나게 됬을 것이다.

### 4. Polymorphism(다형성)

Polymorphism은 같은 명령어도 다른 상황(?)에 따라서 다르게 작동할 수 있다는 것이다. 밑에 코드를 보며 이해를 좀더 해보려고 한다.

```python
class Helloman:
    def __init__(self, name):
        self.name = name
        
    def say(self):
        print(self.name, 'say HI')
    
class Byeman:
    def __init__(self, name):
        self.name = name
        
    def work(self):
        print(self.name, 'say BYE')
    
p1 = Helloman('Henry')
p2 = Byeman('Lisa')

p1.say()
p2.say()
    
    # Henry say HI
    # Lisa say BYE
```

2개의 object가 있고 2개의 instance가 생성이 되었다. p1, p2가 각자 같은 이름을 가진 `say()` 라는 method를 호출했는데 결과 값이 다르게 나온다. 이처럼 같은 이름 혹은 명령어지만 이 상황에서는 다른 instance이기 때문에 결과가 다르게 나온 것이다. 이 특성을 우리는 polymorphism이라고 부른다.

# Override Overload 개념 짚고 가기

OOP를 하면 이 2가지의 개념이 헷갈리는 경우가 많다. 

Override는 inheritance에서 사용되는 경우이다. 상위 object에 있는 method를 하위 object에서 굳이 다시 정의할 필요는 없었다. 하지만, 상위 object에 있는 method의 내용을 바꾸고 싶을 떄가 있을 것이다. 그 때 하위 object에서 같은 method 이름을 작성하고 다른 내용을 넣는다면 override가 발생하는 것이다.

Overload는 같은 object내에 이름이 같은 method가 있는데 parameter가 다른 경우이다(object가 아니어도 두 함수의 이름이 같고 paramter가 달라도 된다). 

```python
def addition(a,b):
    return a+b

def addition(a,b,c):
    return a+b+c

print(addition(1,2))
print(addition(1,2,3))
```

### 참고한 사이트 및 영상

[Object-oriented Programming in 7 minutes](https://www.youtube.com/watch?v=pTB0EiLXUC8)