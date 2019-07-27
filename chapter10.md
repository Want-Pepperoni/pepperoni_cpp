Chapter 10. 배열(Arrays)
=======================

### 기본적인 배열 문법
~~~
int my_array[6];
~~~
- my_array -> val0|val1|val2|val3|val4|val5 로 선언됨
- i번쨰 요소는 my_array[i-1]에 저장된다. (0부터 시작)

### 다차원 배열로 그리드 나타내기
- 2차원 배열 선언
~~~
int tic_tac_toe_board[3][3];
~~~

### 배열 사용하기
#### 배열과 for 루프

example 1. multidimensional_array.cpp
~~~
#include <iostream>

using namespace std;

int main() {
    int array[8][8];
    
    for ( int i = 0; i < 8; i++) {
        for (int j = 0; j < 8; j++) {
            array[i][j] = (i + 1) * (j + 1);
        }
    }
    cout << "Multiplication table:\n";
    for ( int i = 0; i < 8; i++) {
        for ( int j = 0; j < 8; j++) {
            cout << "[ " << i + 1 << " ][  " << j + 1 << " ] = ";
            cout << array[i][j] << " ";
        }
        cout << endl;
    }
}
~~~

#### 함수에 배열 전달하기
example 2. sum_array.cpp
~~~
#include <iostream>

using namespace std;

// 함수를 선언할 때 배열의 크기는 지정하지 않아도 된다.
// 배열의 크기가 필요할 땐 새로운 input으로
int sumArray( int values[], int size){
    int sum = 0;
    for ( int i = 0; i < size; i++) sum += values[i];
    return sum;
}

int main() {
    int values[10];
    for( int i = 0; i < 10; i++) {
        cout << "Enter value " << i << ": ";
        cin >> values[i];
    }
    cout << sumArray( values, 10) << endl;
}
~~~
- 함수를 선언할 때는 배열의 이름만 지정하면 된다.
- 다차원 배열을 전달할 떄는 첫 번째를 제외한 나머지 크기를 꼬박꼬박 알려주어야 한다.
~~~
int check_tic_tac_toe( int board[][3]);
~~~

### 배열 정렬하기
10개의 값을 받아 이를 정렬하는 문제를 생각해 보자.
~~~
#include <cstdlib>
#include <ctime>
#include <iostream>

using namespace std;

int findSmallestRemainingElement( int array[], int size, int index);
void swap( int array[], int first_index, int second_index);

void sort(int array[], int size) {
    for( int i = 0; i < size; i++) {
        int index = findSmallestRemainingElement(array, size, i);
        swap( array, i, index);
    }
}

int findSmallestRemainingElement ( int array[], int size, int index) {
    int index_of_smallest_value = index;
    for( int i = index + 1; i < size; i++) {
        if ( array[i] < array[index_of_smallest_value]) {
            index_of_smallest_value = i;
        }
    }
    return index_of_smallest_value;
}

void swap( int array[], int first_index, int second_index) {
    int temp = array[ first_index];
    array[first_index] = array[second_index];
    array[second_index] = temp;
}
          
// 배열 전과 후를 표시하는 도우미 함수
void displayArray( int array[], int size) {
          cout << "{";
    for( int i = 0; i < size; i++) {
        if (i != 0) cout << ", ";
        cout << array [i];
    }
    cout << "}";
}

int main() {
    int array[10];
    srand( time( NULL));
    for (int i = 0; i < 10; i++) {
        array[i] = rand() % 100;
    }
    cout << "Original array: ";
    displayArray( array, 10);
    cout << endl;
    
    sort (array, 10);
    
    cout << "Sorted array: ";
    displayArray( array, 10);
    cout << endl;
}
~~~
