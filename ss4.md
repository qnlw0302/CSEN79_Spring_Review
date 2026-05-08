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
- Making too many nested function calls
  