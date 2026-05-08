# The STL's Algorithms and Use of Iterators
## Ramdomm Access Iterator
- C++ allows any pointers to an element in an array to be used.

## insertion
- **Vecter** : all iterators and references before the point of insertion are unaffected, unless the new container size is greater than the previous capacity
-  **List** : all iterators and references unaffected
  

## Erasure
- **Vector**: every iterators and reference after the point of erase is invalidated
- **List**: only the iterator and reference to the erased elements is invalidated

## Node iterator
1. A constructer
2. ...


```cpp
node_iterator<int> start(head_ptr);
node_iterator<int> finish;
node_iterator<int> position;

for (position = start; position != finish; ++position){
    ...
}
```

## Header file for the new code
- Should Inlude
    code class definition
    functions to manipulate a linked list
    node iterator
    const node iterator


```cpp
template <class Item>
class node_ieterator{
    public:
        ...
    private:
        node<Item>* current;

}
```

### The difference between post and pre increment
- ++p, first increase and then read p
- p++, first read p and then ++
- don't worry about the difference unless there are other operators


## STL Vectors vs. STL Lists
- STL includes three similiar containers classes:
  1. ...
  2. ...
  3. ...
- Similiar to arrarys
  1. **vectors uses contiguous storage locations for their elements**
  2. Elements can also be accessed using offsets on regular pointers to its elements, and just as efficiently as in array

- std::vector::begin
```cpp
iterator begin();
const_iterator begin() const;
```
