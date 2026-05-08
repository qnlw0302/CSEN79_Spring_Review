# Container Classes
## The Bag Class
- can be initialized
- numbers can be inserted
- can check how many occurrences of a certain number are in the bag
- can check how many numbers are in the bag

## Class
```cpp
class bag{
public:
    bag();
    void insert()...
    void remove()...
private:

};
```
- the class has a default constructor to initialized the bag
- the default constructor can only do simple task, so it's necessary to create a constructor

**we can define the data type at first**
```cpp
typedef int value_tyep;
typedef size_t size_type;
```
- size_t can only treate positive list
- **The overloaded += will allow us to add the contents of one bag to th existing contents of another bag**
```cpp
void operator +=(const bag& addend):
```
**The static keyword specific that one copy of the member is shared by all instances of the class**

## Array
- need to define the array in the private part first 
- the length of the array will be determined by the constant CAPACITY
- **used** is also defined in the private
  
**The rules that dictate how the member variable of a class represent a value are called the invariant of the class**
**The invariant of a class is a condition that is an implicit part of every function's postcondition and it's also an implicit part of every function's precondition**

### The copy function from the standard library
```cpp
copy(<begining location>, <ending location>, <destination>);
```
