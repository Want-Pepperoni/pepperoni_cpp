문제 2. 최댓값 찾기
===============
예제코드 1. 배열을 입력받고 최댓값과 최댓값의 인덱스를 출력하시오.
~~~
// 예제코드 1. 리스트에서 최댓값과 최댓값의 인덱스를 찾아 리턴

#include <iostream>
using namespace std;

int find_max (int *array, int size){
    int i = 0;
    int max_val = array[0];
    while (i < size -1) {
        if (max_val < array[i]) max_val = array[i];
        i++;
    }
    return max_val;
}
int find_max_index (int *array, int size) {
    int max_idx = 0;
    for (int i = 1; i < size; i++) {
        if (array[i] > array[max_idx]) max_idx = i;
    }
    return max_idx;
}

int main() {
    int size;
    cout << "Enter array size: ";
    cin >> size;
    int *array = new int[size];
    
    for (int i = 0; i < size; i++) {
        cout << "Enter the " << i + 1 <<"th numeber: ";
        cin >> array[i];
    }
    cout << "The maximun value is: " << find_max(array, size) << endl;
    cout << "The index of the maximum value is: " << find_max_index(array, size) << endl;
}
~~~

