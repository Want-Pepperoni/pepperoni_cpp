문제 1. 1부터 n까지 합 구하기
========================
예제코드 1. 1부터 n까지 숫자를 하나씩 더해가면서 구하는 알고리즘
~~~
// 예제코드 1. 1부터 n까지 연속된 숫자의 합을 하나씩 더해가면서 구하시오.

#include <iostream>
using namespace std;

int sum( int n) {
    int sum_temp = 0;
    for (int i = 1; i <= n; i++) {
        sum_temp += i;
    }
    return sum_temp;
}

int main() {
  cout << sum(100) << endl;
}
~~~

예제코드 2. 1부터 n까지 숫자의 합을 공식을 이용해 구하시오.
~~~
// 예제코드 2. 1부터 n까지의 합을 공식을 이용하여 구하시오.

#include <iostream>
using namespace std;

int sum( int n) {
    return n * (n + 1) / 2;
}

int main() {
    cout << sum(100) << endl;
}
~~~

연습문제 1. 1부터 n까지 연속된 숫자의 제곱의 합을 구하는 프로그램을 작성하시오.
~~~
// 연습문제 1. 1부터 n까지 연속된 숫자의 제곱의 합을 구하는 프로그램을 작성하시오.

#include <iostream>
using namespace std;

int square_sum1( int n) {
    int sum_temp = 0;
    for (int i = 1; i < n + 1; i++) {
        sum_temp += i*i;
    }
    return sum_temp;
}

int square_sum2( int n) {
    return n * (n + 1) * (2 * n + 1) / 6;
}

int main() {
    cout << square_sum1(10) << endl;    // gives 385
    cout << square_sum2(10) << endl;    // gives 385
}
~~~
