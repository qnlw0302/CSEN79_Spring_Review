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
- ss6 P52