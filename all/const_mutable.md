

## 1. const 멤버 변수 
* `const 멤버 변수`는 한번 초기화된 후 그 값을 수정하지 못 하는 변수  
* `초기화`를 위하여 `이니셜라이져 리스트`를 통해 초기화해야 한다.  

```c++
class User{
public:
    const int age;  // const 변수
    User(int age) : age(age){   // 이니셜라이져 리스트
      
      //age = age // 
    }
};
```

## 2. const 멤버 함수  

* `const 멤버 함수` 내에서는 `멤버 변수`에 대한 `수정`이 불가.  
* 또한 내부에서 `const 멤버 함수`만을 호출할 수 있다.  

```c++
class User{
public:
    int age;  // const 변수
    
    void hello() const{
      age++;    // const 멤버 함수 내에서는 멤버 변수에 대한 수정이 불가하다.
      bye();    // const 함수가 아닌 것도 호출이 불가하다.
    }
    
    void bye(){ }
};
```

* 또한 `멤버 변수`가 `객체`인 경우 그 객체의 `메서드` 역시 const가 아니면 호출 불가  
```c++
class Dog{
public:
    Dog(){}
    
    void hello(){
        cout<<"hello"<<endl;
    }
};

class User{
public:
    int age; 
    Dog dog;
    User(int age) : age(age){ }
    void hello() const{
        dog.hello();      // 멤버 변수가 객체인 경우 해당 객체의 메서드도 const가 아니면 불가
    }
```


## 3. mutable  

* **mutable** 키워드 : const함수 내에서 수정 가능하도록 허용하는 키워드  
```c++
class Dog{
public:
    Dog(){}
    
    void hello(){
        cout<<"hello"<<endl;
    }
};

class User{
public:
    int age; 
    mutable Dog dog;              // mutable을 추가한다.
    User(int age) : age(age){ }
    
    void hello() const{
        dog.hello();      // 호출가능해진다.
    }
```






