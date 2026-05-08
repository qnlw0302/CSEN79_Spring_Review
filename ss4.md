# Pointers and Arrays
## Pointers and Dynamic Arrays
- Pointer is the memory address of a variable
**How to declare a pointer?**
- Pointer variable must be declared by placing an asterisk before the pointer variable's name.
```cpp
double *my_first_ptr;
```
**It's stored on stack**
**& opeartor** is called the **address operator**, and provides the address of a variable.

For example:
```cpp
int *example_prt;
int i;
i = 42;
example_ptr = &i;
cout << &i << endl;
cout << example_ptr << endl;
cout << i << endl;
cout << *example_ptr << endl;
```
Output:
    1. address
    2. address
    3. 42
    4. 42

- Dynamic memory stored on the heap
Sample for try catch
```cpp
int main(){
    int input:
    cout << "what's the input?" << endl;
    cin >> input;
    try{
        if(input < 20)
            cout << "nice" << endl;
        else
            throw 20;
    }
    catch (int e){
        cout << "An exception occurred. Exception#: " << e << endl;
    }
    return 0;
}
```
**Stack Overflow* is the result of:
- Allocating too mant variables on the stack
- Making too many nested function calls\
```cpp
bool is_3(const int* i_ptr);
```
- const keyword indicates that the pointer is pointing to a constant integer
```cpp
double average(const double data[], size_t n);
```
- const keyword indicates that the function can't change the array entries
### Parameter types
- Value parameter: `void function(double p);`
- Reference parameter: `void function(double &p);`
- Const reference parameter: `void function(const double &p);`
- Value parameter that is pointer: `void function(const *p);`
- Const value parameter that is pointer: `void function(const double *p);`
- Reference parameter that is pointer: `void function(double *&p);`
  