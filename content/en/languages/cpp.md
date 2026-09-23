---
title: C++
description: Core C++ syntax for variables, classes, STL, pointers, templates and exception handling.
---

## Variables

```c++
// Integer types
int number = -10;
unsigned int age = 22;
short shortInt = 6000; // 16 bits
long longInt = 1000000; // 32 bits

cpp// Can be true or false
bool isOverage = age >= 18;

// Floating-point types
float weightKg = 77.8;
double doubleNumber = -9998.0;

char character = 'a';
std::string name = "Anderson Silva"; // needs #include <string>
```

## Classes

```c++
class BaseClass {
  protected:
    int width, height;
  public:
    void set_values (int a, int b)
      { width=a; height=b;}
};

class DerivedClass: public Polygon {
  public:
    int area ()
      { return width * height; }
};
```

- `private`: only accessible whitin its defined class.
- `protected`: accessible to derived classes.
- `public`: openly accessible.

## STL containers

### Array

```c++
#include <array>
#include <algorithm>
#include <iostream>

int main() {
    std::array<int, 5> arr = {65, 12, 31};
    std::sort(arr.begin(), arr.end());

    for(int number : arr) {
        std::cout<<number<<" ";
    }
}
```

- `std::array` will be stored on stack.

### Vector

```c++
#include <iostream>
#include <vector>

int main() {
    std::vector<int> v = {8, 4, 5, 9};
 
    v.push_back(6);
    v.push_back(9);
    
    for (int i = 0; i < v.size(); i++) {
        std::cout << "["<<i<<"] = " << v[i]<<" ";
    }
}
```

- `std::vector` is heap allocated and can change size dinamically.

### Map

```c++
#include <iostream>
#include <map>
#include <string>

void printMap(const std::map<std::string, float>& map) { // pass by reference to avoid a copy
    for(const auto&[key, value] : map) {
        std::cout<<key<<": "<<value<<"\n";
    }
}

int main() {
    std::map<std::string, float> storageMap;

    storageMap["banana"] = 5.0;
    storageMap["rice"] = 10.5;

    printMap(storageMap);
}
```

### Set

```c++
#include <iostream>
#include <map>
#include <string>

void printMap(const std::map<std::string, float>& map) { // pass by reference to avoid a copy
    for(const auto&[key, value] : map) {
        std::cout<<key<<": "<<value<<"\n";
    }
}

int main() {
    std::map<std::string, float> storageMap;

    storageMap["banana"] = 5.0;
    storageMap["rice"] = 10.5;

    printMap(storageMap);
}
```

### Queue

```c++
#include <iostream>
#include <queue>

int main() {
    std::queue<int> q;
    for(int i = 0; i < 5;i++) {
        q.push(i); // back pushes i
    }
    
    q.pop(); // removes the first element

    // will keep looping until queue is emptied
    for (; !q.empty(); q.pop()) {
        std::cout << q.front() << ' ';
    }
    // will print: 1 2 3 4
}
```

### Stack

```c++
#include <iostream>
#include <stack>

void printTopElement(const stack<int>& stack) {
    std::cout<<"Top element: "<<s.top() << "\n";
}

int main() {
    std::stack<int> s;

    s.push(1);
    s.push(2);

    // will print: 'Top element: 2'
    printTopElement(s);    

    s.pop(); // removes from the top
    // will print: 'Top element: 1'
    printTopElement(s);
}
```

## References and pointers

```c++
#include <cstdlib>
#include <iostream>;

void printArray(const int *array, int size) {
  std::cout << "Array: ";
  for (int i = 0; i < size; i++)
    std::cout << array[i] << " "; // pointers values can be accessed like arrays
  std::cout << "\n";
}

int main() {
    int value = 3;
    int *intPointer =
        &value; // pointer stores the reference (memory address) of 'value'
    std::cout << "Pointer address: " << intPointer << "\n"; // prints the address
    
    // prints the pointer's value: 3
    std::cout << "Pointer value: " << *intPointer << "\n"; 

    // changing the pointer's value also changes the original value
    *intPointer = 5; 
    std::cout << "Value: " << value << "\n"; // prints 'Value: 5'

    int simpleArray[4] = {0, 1, 2, 3};
    // will print: 'Array: 0 1 2 3'
    printArray(simpleArray, 4);
    
    // this will allocate 4 chunks of 4 bytes and return the address for the
    // pointer
    int *pointerArray = (int *)malloc(4 * sizeof(int));
    for (int i = 0; i < 4; i++)
      pointerArray[i] = i;
    
    // will print: 'Array: 0 1 2 3'
    printArray(pointerArray, 4);
    
    // memory that is manually allocated HAS to be deallocated
    free(pointerArray);
}

```

```c++
#include <iostream>
#include <vector>

// the reference makes it so the function doesn't have to make a copy of the
// vector to print it out
// const indicates the contents of the vector aren't changed here
void printVector(const std::vector<int> &vec) {
    std::cout << "Vector: ";
    for (const int x : vec)
      std::cout << x << " ";
    std::cout << "\n";
}

int main() {
    int a = 5;
    // ref's memory address is the same as a's without it explicitly being
    // passed like with a pointer
    int &ref = a;
    // changing the value of the address also doesn't need a explicit symbol like
    // the pointer's '*' symbol
    ref = 10; // this chenges a's value to 10

    std::vector<int> v = {8, 4, 5, 9};
    // a reference doens't have to be explicitly passed to a function
    printVector(v);
}

```

## Smart pointers

## Templates

## Exception handling

## References

- [cplusplus Reference](https://cplusplus.com/reference/)
- [Cpp Reference](https://www.cppreference.com/)
- [Microsoft Ignite](https://learn.microsoft.com/pt-br/cpp/cpp/smart-pointers-modern-cpp?view=msvc-170)
