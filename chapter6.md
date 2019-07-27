Chapter 6. 함수 (Functions)
=====================

지금까지 우리는 변수를 선언하고, 입력을 받고 결과를 출력하며, 조건문과 루프를 이용해 간단한 프로그램을 만드는 방법을 배웠다. 다만, 프로그램이 main 함수 안에서만 동작
하도록 진행된다면 프로그램이 복잡하면 복잡해 질수록 우리가 코드를 이해하기가 어려워 질 것이다. 함수는 이러한 문제를 해결하기 위해 전체 코드를 조각조각 나누어 구성할 수
있게 해 놓았다.

쉽게 말해, 함수는 코드를 좀 더 쉽게 읽을 수 있도록, 그래서 코드를 다른 곳에 쉽게 재사용 할 수 있도록 코드를 조직적으로 구성한 결과물이다.

### 함수의 문법
다음 코드를 한번 살펴보자.

  ~~~
#include <iostream>

using namespace std;
    
int add( int x, int y) {
    return x + y;
}
    
int main() {
    int result = add( 1, 2);
        
    cout << "The result is: " << result << endl;
    cout << "Adding 3 and 4 gives us: " << add( 3, 4) << endl;
}
  ~~~

### 지역 변수(local variable)와 전역 변수(globla variable)
- 프로그래머가 선언한 변수는 영역(scope)를 가지고 있다

#### 지역 변수(local variable)
- 중괄호{} 안에서 선언된 변수는 {} 안쪽에서만 사용될 수 있다.
  #include <iostream>
  
  using namespace std;
  
  void changeArgument( int x) {
      x = x + 5;
  }
  
  int main() {
      int y = 4;
      changeArgument(y); // y는 함수 호출에 아무런 영향을 받지 않는다.
      
      cout << y << endl; // 값은 여전히 4다.
  }

- 위 코드에서 x는 changeArgument의 인수에 해당하기 때문에 그 안에서 이루어진 연산은 외부에서 정의된 y에 영향을 끼치지 않는다.
- if/while/for 등에서 사용되는 {}안의 변수들의 영역도 똑같이 {}안에서만 연산이 이루어진다.

#### 전역 변수(global variable)
함수 밖에서 선언된 변수를 전역 변수라고 한다. 전역 변수는 선언 시점이 지나면 프로그램 어디에서든지 사용할 수 있다.

    #include <iostream>
    
    using namespace std;
    
    int doStuff() {
        return 2 + 3;
    }
    
    // 전역 변수도 다른 변수들처럼 초기화한다.
    
    int count_of_function_calls = 0;
    
    void fun() {
        count_of_function_calls++;
    }
    
    int main() {
        fun();
        fun();
        fun();
        cout << "Function is called " << count_of_function_calls << "times\n";
    }

### 함수 사용하기

#### 함수의 정의와 선언
-함수의 정의: 함수의 모든 정보를 구성
-함수의 선언: 콜러가 필요로 하는 기본적인 정보(함수의 이름, 리턴 타입, 인수)만 제공

함수 원형(function prototype)을 이용해 함수를 선언

    Return_type function_name (arg_type arg1, ..., arg_type argN);
    

    #include <iostream>
    
    using namespace std;
        
    // function prototype
    int add( int x, int y);
    
    int main() {
        int result = add( 1, 2);
        cout << "The result is: " << result << endl;
    }
    
    int add( int x, int y) {
        return x + y;
    }

- 함수를 선언할 때에는 ;을 마지막에 붙여줘야 한다.

### 함수 단위로 프로그램 쪼개기

함수를 사용해야 하는 경우는 다음과 같다.
- 코드를 반복해서 사용하는 경우
- 코드를 좀 더 읽기 쉽게 작성하고 싶은 경우

### 함수 이름 짓기와 함수 오버로드하기
- C++에서는 오버로드(Overload)라는 개념을 지원하여 이름이 같더라도 인수가 다른 함수들은 서로 다른 함수로 인식한다.
- but 오버로드 기능을 남용하면 코드를 이해하기 어려워질 수 있다.











