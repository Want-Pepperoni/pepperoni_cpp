chapter 14. 동적 메모리 할당
========================

### Introduction
다른 언어( ex. Python)과 달리 포인터라는 개념은 C++에서만 사용하는 개념이다. 이를 통해 한정된 메모리 환경 아래에서 프로그램을 실행해도 메모리를 원하는 만큼 확보하는게
가능하도록 만들어 줄 수 있는데, 이 방법이 바로 동적 메모리 할당에 해당한다.

### new로 더 많은 메모리 확보하기
new 키워드를 이용해 자유 저장소(사용되지 않은 메모리 집합소)의 메모리로 포인터를 초기화 할 수 있다.
~~~
int *p_int = new int;
~~~
- p_int를 사용하는 코드는 메모리를 사용한 뒤 이를 반드시 자유 저장소로 반환해야 한다: 메모리 반환 연산
- 메모리 반환 연산을 하는 동안에는 다른 곳으로 할당 되지 않는다.
- delete 키워드를 이용해 메모리를 자유 저장소로 반환한다.
~~~
delete p_int;
p_int = NULL;
~~~

#### 메모리 부족
할당한 메모리를 제대로 반환하면 메모리가 부족한 상황은 크게 발생하지 않는다. (뒤의 챕터에서 예외 상황에 대해 다룸)

#### 레퍼런스와 동적 할당
일반적으로, 할당한 메모리를 레퍼런스에 저장하면 안 된다. 레퍼런스는 변수에 이름 하나를 더 제공하는 것이지 동적으로 할당된 메모리에 저장 공가을 제공하는 것이 아니다.

### 포인터와 배열
~~~
int numbers[8];
int *p_numbers = numbers;
// 배열이 포인터에 대입되면 포인터처럼 동작한다.

for ( int i = 0; i < 8; i++) {
  p_numbers[i] = i;
}
~~~
메모리를 동적으로 할당하면,
~~~
int *p_numbers = new int[8];
//반환
delete[] p_numbers;
~~~

example 1. resize_array.cpp
~~~
#include <iostream>

using namespace std;

int *growArray( int *p_values, int *size);
void printArray ( int *p_values, int size, int elements_set);

int main() {
    int next_element = 0;
    int size = 10;
    int *p_values = new int[size];
    int val;
    cout << "Please enter a number: ";
    cin >> val;
    while (val > 0) {
        if (size == next_element + 1) {
            p_values = growArray(p_values, &size);
        }
        p_values[ next_element] = val;
        next_element++;
        cout << "Current array values are: " << endl;
        printArray( p_values, size, next_element);
        cout << "Please enter a number (or 0 to exit): ";
        cin >> val;
    }
     delete[] p_values;
}
void printArray ( int *p_values, int size, int elements_set) {
    cout << "The total size of the array is: " << size << endl;
    cout << "Number of slots set so far: " << elements_set << endl;
    cout << "Values in the array: " << endl;
    for (int i = 0; i < elements_set; ++i) {
        cout << "p_values[" << i << "] = " << p_values[i] << endl;
    }
}

int *growArray (int *p_values, int *size) {
    *size *= 2;
    int *p_new_values = new int[ *size];
    for (int i = 0; i < *size; ++i) {
        p_new_values[i] = p_values[i];
    }
    delete[] p_values;
    return p_new_values;
}
~~~

#### 다차원 배열


#### 연습문제 2. Write a function that takes 3 arguments, a length. width and height, dynamically allocates a 3 - dim'l array with those values and fills the 3 - dim'l array with multiplication tables. Make sure to free the array when you are done.

~~~
#include <iostream>
using namespace std;

int main() {
    int size_length;
    int size_width;
    int size_height;
    
    cout << "Size of length: ";
    cin >> size_length;
    cout << "Size of width: ";
    cin >> size_width;
    cout << "Size of height: ";
    cin >> size_height;
    
    // declaring the board
    int *** p_p_p_table;
    p_p_p_table = new int**[size_length];
    for (int i = 0; i < size_length; i++) {
        p_p_p_table[i] = new int*[size_width];
        for (int j = 0; j < size_width; j ++) {
            p_p_p_table[i][j] = new int[size_height];
        }
    }
    
    // fill in the board and print
    for (int i = 0; i < size_length; i++) {
        for (int j = 0; j < size_width; j++) {
            for (int k = 0; k < size_height; k++) {
                p_p_p_table[i][j][k] = (i + 1) * (j + 1) * (k + 1);
                cout << i + 1 << " * " << j + 1 << " * " << k + 1 << " = " << p_p_p_table[i][j][k] << endl;
            }
            cout << endl;
        }
        cout << endl;
    }
    
    // freeing the memory
    for (int i = 0; i < size_length; i++) {
        for (int j = 0; j < size_width; j++) {
            delete[] p_p_p_table[i][j];
        }
        delete[] p_p_p_table[i];
    }
    delete[] p_p_p_table;
}
~~~
