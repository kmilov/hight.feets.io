+++
+++

This document shows the difference between Arrays and link lists.

when we create arrays we ensure that the data is next to each other
in memory, if at runtime we adding a new element, we can not. because the
memory taken to allocate the elements is a fixed size. 

This can be fixed using Linked List, because they are not next to each other, 
randomly scattered in the memory, and, each element has a POINTER/ADDRESS of the
next element.
 
There are cons of using one or the other. 
If I use a Linked List and want to know how many elements there are, I need to go thru 
each element, follow the POINTERS/ADDRESS of each element and count one by one until I reach the last element.
Arrays instead are fixed size, so we know how many items there are.

But! on the benefits side,  when inserting an element in a Linked List, I just need to insert in the memory and append the address of the previous elmeent, plus it can grow at run time.

So.... for Arrays, Reading based on index: takes O[1] and Linked List takes O[n] (because we dont know at what position where the element is in the memory and need to go and look for it one by one). 

On the other hand, when inserting in a Linked List, I just put it randomly and link with the prev element, and for arrays, i need to check if an element exists at that index, if exists

I need to insert at position + 1 and so on until I find a free positon. 
worst case scenario, if im inserting at positon 0 I need to go thru each of the elements and change their position.
this is why inserting is an O(n) operation
 
 |   | Array  | LinkedList
 |---|---|---|
 | Reading runtime  | O(1)  | O(n)
 | Inserting runtime  | O(n)  | O(1)

```
// Example of inserting an element in an array
fn insert(elements: &mut [u32], element:u32, index: usize) {
    // Check that the index is greater than 0 and bellow the elements.length - 1
    // Save a reference to the current element at index,
    // Insert the element at the reference index
    // if the saved reference is different than 0,
    // call this function again.
    //
    let aux = elements[index]; // Always returns a number.
    elements[index] = element;
    if aux > 0 {
        println!("Calling insert again.");
        insert(elements, aux, index + 1);
    }
}


fn main() {
    let mut array:[u32; 6] = [20, 30, 40, 50, 60, 0];
    println!("Array  before insertion: {:?}", array);

    insert(&mut array, 10, 0 as usize);

    println!("Array after inserction: {:?}", array);

}
```
