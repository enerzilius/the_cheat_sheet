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

// Can be true or false
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

### Stack

## References and pointers

## Templates

## Exception handling

## Smart pointers

## References

- [cplusplus Reference](https://cplusplus.com/reference/)
- [Cpp Reference](https://www.cppreference.com/)
- [Microsoft Ignite](https://learn.microsoft.com/pt-br/cpp/cpp/smart-pointers-modern-cpp?view=msvc-170)
