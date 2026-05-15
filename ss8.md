# Queues
- A queue is a data structure of ordered entries such that entries can only be inserted at oen ned and removed at the other end
- the entry at the fornt end of the queue is called the first entry
- FIFO

## Implementations of the queue class
Example for review
```cpp
size_t counter()
{
    queue<char> q;
    char ch;
    char last;
    size_t count = 0;

    while (cin.get(ch) && ch != '\n')
    {
        q.push(ch);
        last = ch;
    }

    while (!q.empty())
    {
        if (q.front() == last)
            ++count;

        q.pop();
    }

    return count;
}
```
- In order to add item in a linked list:
  `list_insert(rear_ptr, entry);` `rear_ptr = rear_ptr -> link();`
