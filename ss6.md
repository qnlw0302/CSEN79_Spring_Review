# Templates and Iterators
## Template Functions
- template functions ca help to write reusable codes
- the definition of a template function can depend on an underlying data type
Here are two different example for using typedef and template"
```cpp
typedef int Item;
Item maximum(Item a, Item b){
    ....
}


template <class Item>
Item maximum(Item a, Item b){
    ...
}
```
Libraries may use
```cpp
#include <iostream> //std::cout
#include <algorithm>//std::swap
#include <vector>//std::vector

for (vector<int>::iterator it = foo.begin(), it != foo.end(), it++){

}
```
## Template Classes
- in the namespace we can still use value_type and size_type, but outside the namespace or that assignment operator is not a member function, we should add a typename before. Ex1 for the template class`bag<Item> operator+(const bag<Item> &b1, const bag<Item> &b2)`; Ex2, for the non member function `typename bag<Item>::size_type bag<Item>(const Item& target) const`

**Implementation**
```cpp
template <class Item>
bag<Item>::bag(size_type initial_capacity){
    data = new Item[initial_capacity];
    capacity = initial_capacity;
    used = 0;
}

bag<Item>::bag(const bag<Item>& source){
    data = new Item[source.capacity];
    capacity = source.capacity;
    used = source.used;
    copy(source.data, source.data+used, data);
}

bag<Item>::~bag(){
    delete [] data;
}

//Modification member functions
typename bag<Item>::size_type bag<Item>::erase(const Item& target){
    size_type index = 0;
    size_type many_removed = 0;
    while (index < used){
        if(data[index] == target){
            --used;
            data[index] = data[used];
            ++many_remved;
        }
        else
            --index;
    }
    return many_removed;
}
```
## The Node Template Class
same as bag class
It used to be `void list_insert(node* previous_ptr, const node::value_type& entry);`, but after using template, it becomes `void list_insert(node<Item>* previous_ptr, const Item& entry);`

- **toolkit function list_locate**
  originally, we have two bersions
  ```cpp
  node* list_locate(node* head_ptr, std::size_t position);
  const node* list_locat(const node* head_ptr, std::size_t position);
  ```
  now, we can combine these two lines of code
  ```cpp
  template<class NodePtr, class SizeType>
  NnodePtr list_locate(NodePtr head_ptr, SizeType position);
  ```

## The STL's Algorithms and Use of Iterators
- An iterator is any object:
  1. Pointing to some element in a range of elements, such as an array or a containrer
  2. Has the ability to iteratr through the elements of that range using a set of operators.
### Input Iterator
- Produced by: `istream_iterator`
```cpp
#include <iostream>
#include <iterator>
int main(){
    double value1, value2;
    cout << "Insert two values: ";
    istream_iterator<double> eos;//end of stream
    istream_iterator<double> iit(cin);
    if(iit != eos) value1 = *iit;
    ++iit;
    if(iit != eos) value2 = *iit;
    cout << value1 << "+" << value2 << "=" << (value1 + value2) << '\n';
    return 0;

}
```

### Output Iterator
**The output operator itself can't be used to retrieve elements**
- produced by: `ostream_iterator`, `inserter()`, `front_inserter()`, `back_inserter()`
```cpp
#include <iostream>
#include <iterator>
#include <vector>
#include<algorithm>
int main(){
    vector<int> myvector;
    for(int i = 0; i < 10; i++) myvector.pushback(i);
    ostream_iterator<int> out_it(cout);
    copy(myvector.begin(), myvector.end(), out_it);
    return 0;

}
```

### Forward Iterator
- have all the functionality of input iterators
- if they are not constant iterator, then they also have the functionality of output iterators
- are limited to one direction in which to iterate through a range
- All std containers support at least forward iterator types
```cpp
#include <iostream>
#include <forward_list>

int main(){
    forward_list<int> mylist(4);
    for(forward_list<int>::iterator it = mylist.begin(); it != mylist.end(); ++i){
        *it = rand();
    }
}
```

### Bidirectional Iterator
- has all the abilities of a forward iterator, puls it can move backward with the -- operator
- produced by list, set , map

### Random Access Iterator
- has all the abilities of bidirectional iterators
- the term random access refers to the ability to quickly access any random selected location in a container
- produces by ordinary pointers, vector, deque
  

## Iterator for linked list
- hAs two constructors:
  1. attaches the iterator to a specified node in a linked list
  2. creates a special iterator that marks the position that is beyond the end of the a linked list
- tags provided bu STL: input_iterator_tag, output_iterator_tag, forward_iterator_tag, bidirectional_iterator_tag, random_access_iterator_tag,for example`public std::iterator<std::forward_iterator_tag, Item>`, it allows iterator to pick up some features of the STL

```cpp
template <class Item>
class node_iterator : public std::iterator<std::forward_iterator_tag, Item>{
public:
    node_iterator(node<Item>* initial = NULL){
        current = initial;
    }
    Item& operator*(){
        return current -> data();
    }
    node_iterator& operator ++(){
        current = current -> link();
        return *this;
    }
    node_iterator operator ++(int){
        node_iterator original(current);
        current = current -> link();
        return original;
    }
    bool operator ==(const node_iterator other) const{
        return current == other.current;
    }
    bool operator !=(const node_iterator other) const {
        return current != other.current;
    }
private:
    node<Item>* current;
}
```

## STL vector VS List
- vectors: use dynamic array
- list: use doubly linked list
- deque: TBD
