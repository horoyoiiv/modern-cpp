# modern-cpp

## [1.안전한 casting](/all/cast.md)  
* static_cast<T>() : 컴파일 시점에 invalid한 캐스팅을 잡는다.  
* dynamic_cast<T>() : 런타임에 invalid한 **다운캐스팅**을 잡는다. 
* reinterpret_cast<T>() : 서로 다른 클래스 타입 간의 캐스팅이 가능.  
  
  

## 기본적인 용어  
#### 1. 선언  
* [타입(자료형)] + [이름]을 지정하는 것.  
* 컴파일러에게 자료형 크기만큼 메모리에 할당하고 그 곳을 변수 이름으로 접근함.  
```c++
int a;
```
#### 2. 정의  
* **변수**는 선언과 정의가 동일한 의미  
* **함수**는 body를 서술하는 것.  

#### 3. 초기화  
* 메모리를 할당받은 곳에 실제로 값을 넣는 것.  
```c++
int a = 10; // int타입의 변수 a를 선언하고 동시에 초기화 수행
int b;      // 변수를 선언한 후 따로
b= 12;      // 그 값을 초기화한다.
```
#### 4. 참조값  
* JAVA에서는 참조변수가 가지고 있는, 메모리 상의 객체에 접근할 수 있는 주소를 의미한다.  

```c++

```

#### 5. 참조변수  
* 그러한 참조값을 가지는 변수.  



