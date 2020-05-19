 
 
 # static_cast<new type>(expression);  
 ```c++
 float f = 3.4;
 int a = static_cast<int>(f);
 ```
 
* **안전장치**  
 * **컴파일 시점**에서, 유효하지 않는 캐스팅을 잡아준다.  

#### 1. C 스타일의 캐스팅  
* 안전하지 않지만, 컴파일이 통과되어 개발자의 실수를 잡아줄 수 없다.  

```c++
int* i = new int(10);
char* ch = (char*)i;    // 이는 허용되어버린다...!
```
#### 2. 안전하게 캐스팅하여, 컴파일 시점에 잡기  
* 아래와 같이 static_cast<T> 로 캐스팅하면, 해당 캐스팅이 invalid인 경우 컴파일에러...!  
```c++
int* i = new int(10);
char* ch = static_cast<char*>(i)    // 컴파일 에러뜬다.
```


# dynamic_cast<>()  
* 그래서 `다이나믹`  
* 런타임에 안전한 케스팅인지 확인해준다.  
* 주로 **다운캐스팅** 시, 안전성을 확인해준다.  

```c++

class Parent{
public:    
    Parent(){ cout<<"Parent cons"<<endl;}
    virtual ~Parent(){ cout<<"Parent destr"<<endl;}
    
    void show() { cout<<"parent show"<<endl;}
};

class Child : public Parent{
public:
    
    Child(int val): val(val) {cout<<"Child const"<<endl; }
    ~Child(){ cout<<"Child des"<<endl;}
    void show(){ cout<<"child show : "+val<<endl;}
    
    int val;
};
```

* 아래의 다운캐스팅은 invalid하다.   
* 하지만 컴파일되어, 사용될 수 있다.  
```c++
Parent* pptr = new Parent;
Child* cptr = (Child*)pptr; 
cptr->show(); // 동작한다. 하지만 여기서 Child의 맴버필드가 사용된다면? 그 플드는 초기화되지 않았다.
```
#### dynamic_cast<>() 사용  
* 아래를 봐라, invalid한 캐스팅이기에, dcast의 반환값은 **null**이 된다.  
```c++
Parent* pptr = new Parent;
Child* cptr = dynamic_cast<Child*>(pptr); 
```

* 킹치만, 아래와 같이 **유효한** 캐스팅은 정상적으로 동작한다.  
```c++
Parent* pptr = new Child(10);
Child* cptr = dynamic_cast<Child*>(pptr); 
```

## reinterpret_cast<>()  
* 서로 다른 타입 간의 캐스팅에서 사용된다.  

```c++
int* iptr = new int(65);

char* cptr = reinterpret_cast<char*>(iptr);
cout<<cptr<<endl; // A
```









 
