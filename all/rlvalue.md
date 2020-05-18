
# lvalue 와 rvalue  


## C  
* c언어에서는 **대입 연산자** 좌측에 오는 값을 lvalue, 우측에 오는 값을 **rvalue**라고 말한다.  


## C++  

1. **lvalue** : expression이 끝나도 유지되며, 메모리 상에 위치하기에 주소값을 가지고 &(ampersand) 연산자로 접근할 수 있는 객체.  
2. **rvalue** : 그렇지 않는 객체, expression이 끝나면 소멸되는 임시객체.  


## 1. Rvalue Reference  
* rvalue를 가르킬 수 있는 참조자이다.  

```c++
int a = 5;    // 5는 rvalue이고, a는 lvalue
int& b = a;   // b는 lvalue reference이다. lvalue를 가르키기에.
```
```c++
int x = 30;
int y = 20;

int&& rr0 = (x+y);    // 임시 객체인 rvalue를 참조할 수 있게 된다.
int&& rr1 = 123;      // 123이라는 숫자 리터럴은 해당 expression 종료 후 사라지게 되는데 이를 잡고 있다.
int&& rr2 = (10+20);
```

## 2. lvalue와 rvalue의 함수  
* **std::move()** : lvalue를 rvalue로 캐스팅한다.  

```c++
void print(int& v){

}

void print(int&& v){

}

int main(void){ 
    int a = 123;
    print(a);       // print(int& v) lvalue 호출
   
    print(321);    // print(int&& v) rvalue 호출
  
    print(move(a)); // print(int&& v) rvalue 호출
 
  return 0;
}

```




