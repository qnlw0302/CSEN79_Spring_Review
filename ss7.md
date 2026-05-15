# Stacks
- stacks follow LIFO
- add called push, delete called pop
- don't require that the entries can be compared using the < operator

## Inplementations of the stack class
data[0] is at the bottom of the stack
data[used - 1] is at the top of the stack
if the value of used is 0, than it should be an empty stack
```cpp
//template class
#include <cassert>
template <class Item>
const typename stack<Item>::size_type stack<Item>::CAPACITY;
void stack<Item>::push(const Item& entry){
    assert(size() < CAPACITY);
    data[used] = entry;
    ++used;
}
void stack<Item>::pop(){
    assert(!empty())
    return --used;
}

Item stack<Item>::top() const{
    assert(!empty());
    return data[used - 1];
}
```
**The head of the linked list serves as the top of the stack**

## Stack Class
- Stack underflow: if a program attempts to pop an item off an empty stack
- Stack overflow: if a program attempts to push an item on to a full stack
```cpp
#include <stack>
int main(){
    stack<int> myStack;
    mystack.push(1);
    mystacl.top()+=10;
    //output is 11
}
```
## Stack Applications
- Stack is used to analyze the syntax of a program
- used to keep track of locak variables when a program is run
- used to search a maze or a family tree or other type of brandhing structures
```cpp
#include <cstdlib>
#include <iostream>
#include <stack>
#include <string>
using namespace std;
bool is_balanced(const string& expression){
    const char left_parenthesis = '(';
    const char right_parenthesis = ')';
    stack<char> store;
    string::size_type i;
    char next;
    bool failed = false;
    for (i = 0; !failed && (i < expression.length()); ++i){
        next = expression[i];
        if(next == left_parenthesis)
            store.push(next);
        else if ((next == right_parenthesis) && (!store.empty()))
            store.pop();
        else if ((next == right_parenthesis) && (store.empty()))
            failed = true;
    }
    return (store.empty() && !failed);
}

int main(){
    string user_input
    cout << "type a string"
    getline(cin, user_input);
    if(is_balanced(user_input))
        cout << "balanced\n";
    else
        cout << "not balanced\n";
    return EXIT_SUCCES;
}
```
