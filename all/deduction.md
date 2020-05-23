# Type Deduction  

* 타입 추론  

* **auto**와 **decltype** 모두 컴파일 타임에 사용된다.  


## 1. auto  
* `변수`의 `타입`을 **초기화되는 값**을 통해 추론(deduction)한다.  
* `초기화 값`을 보고 `타입`을 결정하라고 **컴파일러**에게 지시하는 것.  

```c++
double d1 = 1.2;
auto d2 = 1.3;      // d2 변수의 타입은 초기값이 1.3으로부터 추론되어 컴파일러에 의해 double로 된다.
```

```c++
cout<<typeid(d2).name()<<endl;
// d : double 의미
```

#### 1.1. 함수의 반환값을 통해 초기화하는 변수에서 사용 가능.  

```c++
auto result = sum(19, 31);
```

#### 1.2. 함수의 `반환 타입`으로 사용 가능.  

```c++
auto sum(int x, int y){
  return x + y;
}
```
#### 1.3. 함수의 `매개변수`로는 사용 불가.  


## 2. decltype  

* **declared type**의 약자.  
* `변수`나 `expression`을 통해 `타입`을 추론할 수 있다.  

```c++
int x = 3;
decltype(x) y = 123;  //  int y = 123; 과 동일하다.
```

```c++
int y = 120;
int& x = y;
decltype(x) rx = y;   // int& rx가 된다. 좌측값 참조 타입
```

```c++
int&& x = 30;
decltype(x) rx = 20;   // int&& rx가 된다. 우측값 참조 타입
```

#### 2.1. 왜 사용하는지  
* 템플릿 타입으로 정의된 인자들의 연산 결과를 받게 되는 변수가 있다면, 이 변수의 타입을 추론하기 위해서 사용.  
* 아래의 경우 초기화값으로 추론되는 auto는 매개변수 타입으로서, 사용되지 못 한다.  

```c++
template<typename T, typename U>
void add(T t, U u, decltype(t+u)& result){
  result = t + u;
}
```

```c++
double a = 1.2;
int b = 10;
decltype(a+b) result;

add(a, b, result);
```

