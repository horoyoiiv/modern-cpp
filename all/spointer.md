

# smart pointer(C++11)  

* **smart pointer** 에는 크게 다음과 같은 세 가지가 있다.  

1. **unique_ptr**  
2. **shared_ptr**  
3. **weak_ptr**  


# 1. unique_ptr  
* memory 헤더에 포함  
* **하나의 소유권자만 허용**된다.  

#### 1. 새 소유권자(unique_ptr 객체)로 `자원`의 **이동**은 가능하지만, **복사**는 안된다.  
#### 2. 스마트 포인터 객체 변수의 스코프를 벗어나면 자동으로 소멸자가 호출된다.  

* `스코프` : 변수가 생성되어, 그것이 유효한 범위  
```c++
void foo(){
    unique_ptr<User> uptr = make_unique<User>("horoyoii", 23);
    uptr->hello();
    
    auto uptr2 = std::move(uptr);   // move함수를 통한 소유권 이전.
                                    // rvalue 래퍼런스를 매개변수로 가지는 이동 생성자가 호출될 것...
    uptr2->hello();

    uptr->hello();                // segment fault 가 발생한다.  
}
```

# 2. shared_ptr  
* 하나의 `객체`를 여러 `스마트 포인터 객체`가 공유한다.  
* `shared_ptr 객체`들은 동일한 `객체`를 포인팅한다.  

#### 1. 참조 횟수가 0이되면 delete가 호출되어, 그 안에서 할당된 객체의 자원을 반납한다.  

# 3. weak_ptr  













