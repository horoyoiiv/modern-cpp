# modern-cpp

## [1.안전한 casting](/all/cast.md)  
* **static_cast<T>()** : 컴파일 시점에 invalid한 캐스팅을 잡는다.  
* **dynamic_cast<T>()** : 런타임에 invalid한 **다운캐스팅**을 잡는다. 
* **reinterpret_cast<T>()** : 서로 다른 클래스 타입 간의 캐스팅이 가능.  
  
## [2. 이동 생성자](/all/move_cons.md)  
* c++11 이전에는 임시 객체를 바탕으로 새로운 객체 생성 시 `복사 생성자`가 호출되었고 이는 곧 불필요하고 과도한 메모리 복사를 유발했다.  
* c++11 이후, 임시 객체를 바탕으로 새로운 객체를 생성 시 **임시 객체**를 **rvalue 참조자**로 받은 후 **이동 생성자**를 호출하여, 메모리 복사 비용을 줄인다.  

```c++
User(User&& rhs){
  mPtr = rhs.mPtr;
  rhs.mPtr = nullptr;
}
```

## [3. 타입 추론](/all/deduction.md)  
* **auto** : `초기화 값`에 의해 컴파일러가 타입을 추론한다.  
* **decltype** : 변수나 expression이 인자처럼 넘어와서 이를 통해 타입을 추론한다.  

## [4. explicit](/all/explicit.md)  
* 생성자가 호출되어 **암시적 형변환**이 되는 것을 방지한다.  
```c++
User u = 10;    
```
## [5. mutable](/all/const_mutable.md)  
* mutable 변수는 `const 멤버 함수`내에서도 수정이 가능해진다.  

## [6. 스마트 포인터](/all/spointer.md)  
* RAII 패턴이 적용된 C++의 메모리 관리 기법  
1. unique_ptr  
2. shared_ptr  
3. weak_ptr  



# functional  

## [1. std::function](/all/function.md)  
* callable 혹은 함수 포인터를 가질 수 있는 객체  
```c++
std::function<int(int, int)> myf = foo();
myf(10, 20);
```

## [2. std::bind](/all/bind.md)  
* `함수`에 넘겨줄 `인자`가 미리 결정되었다면 이를 `동적으로` 바인딩시켜주는 역할.  
왜 동적? default 값을 지정하면 컴파일 시점에 가능하기 때문  

```c++
auto my_f = std::bind(my_function, std::placeholders::_1, 100, std::placeholders::_2);
```





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



