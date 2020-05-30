

# std::bind  

* `함수`와 미리 결정된 `함수에 넘겨줄 인자`를 묶는 역할  


```c++

int foo(int a, int b, int c){
    printf("%d %d %d\n", a, b, c); 
    
    return a + b;
}

int main(void){     
    auto b_foo = std::bind(foo, std::placeholders::_1, 100, std::placeholders::_2);
   
    b_foo(10, 20);

    return 0;
}
```

* `함수`에 넘겨줄 `인자`가 미리 결정되어 있다면, 이를 아래와 같이 binding 시켜준다.
```c++
auto b_foo = std::bind(foo, std::placeholders::_1, 100, std::placeholders::_2);
                                    a               b         c
b_foo(10, 20);
      p1, p2
```

* std::bind는 가변길이 인자를 받아 나열된 순서대로 인자에 들어간다.  
* std::placeholders는 실제 `binding된 함수`를 호출할 때 넘겨주는 `인자`의 순서를 의미.  













