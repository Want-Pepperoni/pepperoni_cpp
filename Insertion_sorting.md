Insertion sorting

~~~
#include <iostream>
using namespace std;

int main() {
    int vector[10];
    for (int i = 0; i < 10; i++) {
        cout << i + 1 << "th element: ";
        cin >> vector[i];
    }
    cout << "Before sorted: ";
    for (int i = 0; i < 10; i++) {
        cout << vector[i] << " ";
    }
    cout << endl;
    
    for (int j = 1; j < 10; j++) {
        int key = vector[j];
        int i = j -1;
        while (i >=0 && vector[i] > key) {
            vector[i + 1] = vector[i];
            i = i-1;
        }
        vector[i+1] = key;
    }
    cout << "After sorted: ";
    for (int i = 0; i < 10; i++) {
        cout << vector[i] << " ";
    }
    cout << endl;
}
~~~
