Chapter 12. Introduction to Pointers
====================================
# So, What are pointers?
pointer: Variables that "point" to locations in memory
The word pointer can refer either to
1) A memory address itself
2) A Variable that stores a memory address

A pointer stores an address, so when you use the bare pointer, you get that address back. You have to add sth exta, *, inoder
to retrieve or modify the value stored at the address.

A variable stores a value, so when you use the variable, you get its value. You have to add some extra, &, in order to retrieve
the address of that variable.

      # include <iostream>
      using namespace std;
  
      int main() {
          int x;
          int *p_int;
    
          p_int = &x;
          cout << "Please enter a number: ";
          cin >> x;
          cout << *p_int << endl;
          *p_int = 10;
          cout << x << endl;
      }
      
When pointer is uninitialized, then it can point anything; we use the value NULL to notice that the pointer is uninitialized.

    #include <iostream>
    using namespace std;
    
    int main() {
        int *p_int = NULL;
      //code that might or might not set p_int
        if (p_int != NULL) {
            *p_int = 2;
        }
    }


    #include <iostream>
    using namespace std;

    void swap1 (int left, int right) {
        int temp;
        temp = left;
        left = right;
        right = temp;
    }

    void swap2 (int *p_left, int *p_right) {
        int temp = *p_left;
        *p_left = *p_right;
        *p_right = temp;
    }

    int main() {
        int x = 1, y = 2;
        swap1(x, y);
        cout << x << " " << y << endl;
        swap2(&x, &y);
        cout << x << " " << y << endl;
    }

# References

Reference: A variable that refers to another variable, sharing the same basking memory.

    //References must always be initialized.
     int x = 5;
     int &ref = x;
     
     //swap function with reference
     void swap(int &left, int &right) {
        int temp = right;
        right = left;
        left = temp;
     }
     





