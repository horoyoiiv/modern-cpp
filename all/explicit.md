

# explict  

* 의도치 않은 `암시적 형변환`을 막을 수 있다.  

### 1. 형 변환  
* type casting : 하나의 자료형을 다른 자료형으로 바꾼다.  

* **1.1. 명시적 형변환** : 개발자에 의해 코드 상에서 명시적으로 형변환시키는 경우  
방법 : c-style casting, static_cast, dynamic_cast, reinterpreted_cast  

* **1.2. 암시적 형변환** : 컴파일러에 의해 자동으로 형변환되는 경우   
더 큰 자료형으로의 변환은 **안전**하다. int -> long / float -> double  
```c++
int i = 10;

// 암시적 형변환
char ch = i;    // int타입은 컴파일러에 의해 char로 변환되어, 초기화 값으로 사용된다.  

// 명시적 형변환
char ch = (char)i;
char ch = static_cast<char>(i);
```

### 2. explicit  
* 암시적 형변환을 통해 생성자가 호출되는 것을 막아준다.  

```c++
class User{
  int n;
public:
  User(int n) : n(n){}
};
```

* 아래의 경우 정수 120은 User(120)이라는 생성자를 호출하여 대입된다.  
* INT 타입이 USER 타입으로 **암시적 형변환**이 되는 것.  

```c++
User u = 120;
```

```c++
class User{
  int n;
public:
  explict User(int n) : n(n){}
};

User u = 120; // 컴파일 에러
User u = User(120);  // 이렇게 사용해야 함.
```

### 3. 다른 예제  

```c++

class User{
public:
    int n;
    User(int n): n(n){
        cout<<"생성자"<<endl;
    }

    bool operator==(const User& rhs) const{
        return n == rhs.n;
    }
};


int main(void){
    User u = 10;
    
    if(u == 10){            // u.operator==(10) | const User& rhs = 10 | 암시적 캐스팅이 발생.
        cout<<"same"<<endl;
    }
   
    return 0;
}
```

