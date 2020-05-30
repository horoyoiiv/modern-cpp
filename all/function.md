

# C++ std::function  

## 1. 기존 방식  
* `함수` 역시 메모리 영역에 위치하기에 그 시작주소를 다룰 수 있다.  
* `함수의 주소`를 가지는 변수가 **함수 포인터형 변수**  

* 함수 포인터형 변수 선언  
```c++
반환값 (*변수명)(인자...) = 실제함수
```

```c++
int add(int a, int b){
  return a + b;
}

int main(void){
  
  // 둘 다 가능
  int (*fptr)(int, int) = add;    // 암묵적으로 함수의 주소
  int (*fptr)(int, int) = &add;
  
  // 둘 다 가능.
  fptr(10, 20);
  (*fptr)(10, 20);
  
  return 0;
}
```


## 2. 함수 포인터를 매개변수로 넘기기  

```c++
int foo(int a, int b, void (*fptr)(int, int)){

  fptr(a, b);
}
```

## 3. typedef로 이쁘게 하기  

```c++
typedef void (*my_function)(int, int);

int foo(int a, int b, my_function myf){

}
```

# std::function  

* `함수 포인터` + `callable`을 저장할 수 있는 객체 변수  

```c++
#include<functional>

int foo(int a, int b);

int main(void){
  
  std::function<int(int, int)> myF = foo;
  
  myF(10, 20);
  return 0;
}
```


