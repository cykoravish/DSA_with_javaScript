# DSA WITH JAVASCRIPT NOTES

![Project Screenshot](./assets/dsa.png)

## Data Structure

A data structure is a specific way of organizing, storing, and managing data. or structuring the data in optimized way is called data structure.

## Algorithm

An algorithm is a set of well-defined instructions or a step-by-step procedure for solving a problem or performing a task.

## Big O notation

Big O notation consists of Time complexity and Space complexity.

### Time complexity

It helps us to know how long an algorithm will take to run.

### Space complexity

It helps us to know how much memory an algorithm will consume.

### What is O(n) ?

O(n) is a way to describe how long an algorithm takes to run as the size of the input (n) grows.
example: -

```javascript
function printElements(arr) {
  for (let i = 0; i < arr.length; i++) {
    console.log(arr[i]);
  }
}
```

- In this example, if the array has 5 elements, it will take 5 steps; if it has 10 elements, it will take 10 steps.

- O(n) means that if the input size doubles, the time taken will also double. It's straightforward and scales linearly with the input size.

### What is O(1) ?

O(1) describes an algorithm that takes a constant amount of time to complete, regardless of the size of the input. This means that the execution time remains the same no matter how much the input size increases.
example: -

```javascript
function getFirstElement(arr) {
  return arr[0]; // Accessing the first element
}
```

- In this example, accessing the first element of the array takes the same amount of time whether the array has 5 elements or 5 million elements.

- O(1) means that the algorithm's runtime is constant and does not change with the size of the input.

### What is O(n^2) ?

O(n^2) describes an algorithm whose time complexity grows quadratically with the size of the input (n). It's less efficient than O(n) and O(1) for large inputs because the time required increases rapidly as the input size increases.
example: -

```javascript
function printPairs(arr) {
  for (let i = 0; i < arr.length; i++) {
    for (let j = 0; j < arr.length; j++) {
      console.log(arr[i], arr[j]);
    }
  }
}
```

- In this example, if the array has 5 elements, the function will perform 5 _ 5 = 25 operations. If the array has 10 elements, it will perform 10 _ 10 = 100 operations.

```javascript
function print(n) {
  for (let i = 1; i <= n; i++) {
    for (let j = 1; j <= n; j++) {
      for (let k = 1; k <= n; k++) {
        console.log(i, j, k);
      }
    }
  }
}
```

- In the above code the number of operations will be the number of times the loop will run so there are three nested loops. If n=3, then the total number of operations would be 3^3 = 27

### What is O(log n)?

O(log n) describes an algorithm whose time complexity grows logarithmically with the size of the input (n). This means that the time it takes to complete the algorithm increases slowly as the input size grows. Logarithmic time complexity is highly efficient, especially for large input sizes.

- Logarithmic Time: The time it takes to complete the task increases logarithmically as the input size increases.
- Example: A common example is binary search, where the input size is halved at each step.

## Understanding Output After Performing Operations on a Custom JavaScript Array Class

```javascript
class MyArray {
  constructor(length, data) {
    this.length = 0;
    this.data = {};
  }
  push(item) {
    this.data[this.length] = item;
    this.length++;
    return this.length;
  }
  get(index) {
    return this.data[index];
  }
  pop() {
    const lastElement = this.data[this.length - 1];
    delete this.data[this.length - 1];
    this.length--;
    return lastElement;
  }
  shift() {
    const firstElem = this.data[0];
    for (let i = 0; i < this.length; i++) {
      this.data[i] = this.data[i + 1];
    }
    delete this.data[this.length - 1];
    this.length--;
    return firstElem;
  }
  delete(index) {
    const item = this.data[index];

    for (let i = index; i < this.length - 1; i++) {
      this.data[i] = this.data[i + 1];
    }
    delete this.data[this.length - 1];
    this.length--;
    return item;
  }
}
const newArr = new MyArray();
newArr.push("orange");
newArr.push("mango");
newArr.push("banana");
// console.log(newArr.get(3));
// newArr.pop();
// newArr.shift();
// newArr.delete(1);
console.log(newArr);
```

### Reversing string

```javascript
const str = "hello";
const reverseStr = str.split("").reverse().join("");
console.log(reverseStr); //olleh
```

- Palindromes: If the reverse string is equal to the original one then that word is a palindrome. For example - pop, level, noon, wow

### checking if the word is palindrome

```javascript
//checking if the string is palindrome or not
const checkStr = (str) => str === str.split("").reverse().join("");
console.log(checkStr("level")); //true if it's palindrome or else false if it's not palindrome

//checking if the number is palindrome or not
const checkNum = (str) => str === str.split("").reverse().join("");
console.log(checkNum("level")); //true if it's palindrome or else false if it's not palindrome
```

### Capitalize first letter of each word.

```javascript
let string = "raVish iS a gOod boy";

const capitalize = (str) => {
  return str
    .toLowerCase()
    .split(" ")
    .map((word) => word[0].toUpperCase() + word.slice(1))
    .join(" ");
};

console.log(capitalize(string));
```

**Problem -> Imagine you have a array of numbers and a target number. Your job is to find two numbers from that array and the sum of those two number must be equal to the target number. You also need to tell which index those two numbers are in the array.**
**example - if the array of number is [2, 7, 11, 15] and the target number is 0, then the answer would be [0, 1] because 2 (at index 0) plus 7 (at index 1) equals to 9**

```javascript
function twoSum(arr, targetNo) {
  for (let i = 0; i < arr.length; i++) {
    for (let j = i + 1; j < arr.length; j++) {
      if (arr[i] + arr[j] === targetNo) {
        return [i, j];
      }
    }
  }
  return [];
}
console.log(twoSum([2, 4, 6, 8, 10], 10));
```

### Linked List:

A linked list is a linear data structure where each element, called a node, contains a value and a reference (or link) to the next node in the sequence.

- singly Linked List: A singly linked list is a data structure consisting of a sequence of elements, each containing a data value and a reference (or pointer) to the next element in the sequence. It allows for efficient insertion and deletion of elements but only provides unidirectional traversal from the head (the first element) to the tail (the last element).

```javascript
class Node {
  constructor(value) {
    this.head = value;
    this.next = null;
  }
}

class LinkedList {
  constructor(value) {
    this.head = new Node(value);
    this.tail = this.head;
    this.length = 1;
  }

  push(value) {
    let newNode = new Node(value);

    if (!this.head) {
      this.head = newNode;
      this.tail = newNode;
    }

    this.tail.next = newNode;
    this.tail = newNode;
    this.length++;
  }

  reverse() {
    let temp = this.head;
    this.head = this.tail;
    this.tail = temp;
    let next = temp;
    let prev = null;

    for (let i = 0; i < this.length; i++) {
      next = temp.next;
      temp.next = prev;
      prev = temp;
      temp = next;
    }

    return this;
  }
}

const myLinkedList = new LinkedList(1);
myLinkedList.push(2);
myLinkedList.push(3);
myLinkedList.push(4);
console.log(myLinkedList.reverse());
```

- Doubly Linked List: A doubly linked list is a data structure consisting of a sequence of elements, each containing a data value and two references (or pointers): one pointing to the next element in the sequence and the other pointing to the previous element. This bidirectional linkage allows traversal in both forward and backward directions, facilitating more efficient insertions and deletions compared to a singly linked list, especially when the operations involve elements near the end of the list.

```javascript
class Node {
  constructor(value) {
    this.value = value;
    this.next = null;
    this.prev = null;
  }
}

class DoublyLinkedList {
  constructor(value) {
    const newNode = new Node(value);
    this.head = newNode;
    this.tail = this.head;
    this.length = 1;
  }

  push(value) {
    const newNode = new Node(value);

    if (!this.head) {
      this.head = newNode;
      this.tail = newNode;
    } else {
      this.tail.next = newNode;
      newNode.prev = this.tail;
      this.tail = newNode;
    }

    this.length++;
    return this;
  }

  pop() {
    if (this.length === 0) {
      return undefined;
    }

    let temp = this.tail;

    if (this.length === 1) {
      this.head = null;
      this.tail = null;
    } else {
      this.tail = this.tail.prev;
      this.tail.next = null;
      temp.prev = null;
    }

    this.length--;
    return temp;
  }

  unshift(value) {
    const newNode = new Node(value);

    if (this.length === 0) {
      this.head = newNode;
      this.tail = newNode;
    } else {
      newNode.next = this.head;
      this.head.prev = newNode;
      this.head = newNode;
    }

    this.length++;
    return this;
  }

  shift() {
    if (this.length === 0) {
      return undefined;
    }

    let temp = this.head;

    if (this.length === 1) {
      this.head = null;
      this.tail = null;
    } else {
      this.head = this.head.next;
      this.head.prev = null;
      temp.next = null;
    }
    this.length--;
    return temp;
  }
}

let myDoublyLinkedList = new DoublyLinkedList(0);
myDoublyLinkedList.push(1);
// myDoublyLinkedList.pop();
// myDoublyLinkedList.shift();
console.log(myDoublyLinkedList);
```

## stack

A stack is a linear data structure that follows LIFO (Last In First Out) principle.

```javascript
class Node {
  constructor(value) {
    this.value = value;
    this.next = null;
  }
}

class Stack {
  constructor(value) {
    const newNode = new Node(value);
    this.first = newNode;
    this.length = 1;
  }

  push(value) {
    const newNode = new Node(value);

    if (this.length === 0) {
      this.first = newNode;
    } else {
      newNode.next = this.first;
      this.first = newNode;
      this.length++;
      return this;
    }
  }

  pop() {
    if (this.length === 0) {
      return undefined;
    }

    let temp = this.first;
    this.first = this.first.next;
    temp.next = null;
    this.length--;
    return temp;
  }

  top() {
    if (this.length === 0) {
      return undefined;
    }
    return this.first;
  }
}

let theStack = new Stack(0);
theStack.push(1);
theStack.push(2);
// theStack.pop();
console.log(theStack);
```

### Queue

A Queue is a linear data structure that functions like a waiting line. It follows the FIFO (First In First Out) principle, meaning the element that enters the queue first will be the first one to be removed.

```javascript
class Node {
  constructor(value) {
    this.value = value;
    this.next = null;
  }
}

class Queue {
  constructor(value) {
    const newNode = new Node(value);
    this.first = newNode;
    this.last = newNode;
    this.length = 1;
  }

  enqueue(value) {
    const newNode = new Node(value);
    if (this.length === 0) {
      this.first = newNode;
      this.last = newNode;
    }

    this.last.next = newNode;
    this.last = newNode;
    this.length++;
    return this;
  }

  dequeue() {
    if (this.length === 0) {
      return undefined;
    }

    let temp = this.first;

    if (this.length === 1) {
      this.first = null;
      this.last = null;
    }

    this.first = this.first.next;
    temp.next = null;
    this.length--;
    return temp;
  }
}

let myQueue = new Queue(0);
myQueue.enqueue(1);
myQueue.enqueue(2);
myQueue.dequeue();
console.log(myQueue);
```
