### 문제 3. 동명이인 찾기 1

~~~
#include <iostream>
#include <string>

using namespace std;



int main() {
    string list_of_names[4];
    list_of_names[0] = "Tom";
    list_of_names[1] = "Jerry";
    list_of_names[2] = "Mike";
    list_of_names[3] = "Tom";
    
    int size = 0;
    for (int i = 0; i < 4; i++) {
        for ( int j = i + 1; j < 4; j++) {
            if (list_of_names[i] == list_of_names[j]) {
                size ++;
            }
        }
    }
    string list_of_same_names[size];
    
    for (int i = 0; i < 4; i++) {
        for ( int j = i + 1; j < 4; j++) {
            int k = 0;
            while (list_of_names[i] == list_of_names[j]) {
                list_of_same_names[k] = list_of_names[i];
                k++;
                break;
            }
        }
    }
    
    for (int i = 0; i < size; i++) {
        cout << list_of_same_names[i] << " ";
        cout << endl;
    }
}
~~~
