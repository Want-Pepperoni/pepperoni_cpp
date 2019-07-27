Chapter 8. 프로그램에 임의성 부여하기
===============================

컴퓨터에서 pseudo-random numbers를 만들어 내도 실제 random number를 대체하기에 모자르지 않다.

### C++ 에서 난수(Random number) 얻기
~~~
void srand (int seed);
~~~
-srand는 어떤 수를 받아 이를 시드로 설정
-srand는 프로그램 시작 시 한번만 호출
-일반적으로는 현재 시간을 어떤 수로 바꿔 리턴하는 형식으로 사용

~~~
#include <iostream>
#include <cstdlib>
#include <ctime>

int main() {
  srand( time( NULL)); //시작할 때 한번만 호출
  cout << rand() << endl;
}
~~~

-rand() 함수를 통해 난수를 호출할 수 있음

하지만 rand()를 통해 출력한 결과는 0에서 RAND_MAX사이의 값이다. 다음 코드를 통해 원하는 범위 안쪽의 결과를 만들 수 있다.
~~~
#include <iostream>
#include <cstdlib>
#include <ctime>

using namespace std;

int randRange( int low, int high) {
    return rand() % (high - low + 1) +low;    // % : modulus operator,, 나머지를 반환
}

int main() {
    srand( time( NULL));
    for (int i = 0; i < 1000; i++) {
        cout << randRange( 4, 10) << endl;
    }
}
~~~

### 버그와 임의성
프로그램에 버그가 있을 때에는 언제나 동일한 동작을 보여야 파악하기 쉽다. 이 떄는 srand호출 부분을 주석으로 처리한다.

srand를 호출했을 때 버그가 생기면 프로그램이 실행도리 때마다 다음처럼 시드 값을 저장하는 것도 생각해 볼 수 있다.
~~~
int srand_seed = time( NULL);
cout << srand_seed << endl;
srand( srand_seed);
~~~
