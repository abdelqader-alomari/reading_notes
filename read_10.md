# Read: Stacks & Queues

## Stacks

In programming, a stack is an abstract, linear data type with a predefined capacity (or boundary). It follows a particular order for adding or removing elements. Linear data structures organize their components in a straight line, so if we we add or remove an element, they will grow or shrink respectively.

![](https://cdn.codegym.cc/images/article/80a1decb-1b17-4501-a32a-8cd46c4fec07/800.webp)

- Imagine this simple situation: you're staying at a hotel, and over the course of the day you received some business letters. You were not in your room at the time, so the hotel clerk simply placed the incoming letters on your desk.
- First, he placed the first letter on the desk. Then a second letter arrived, and he placed it on top of the first.
  He put the third letter on top of the second, and the fourth on top of the third.
- Data structures: stack and queue - 3And now, answer a simple question: what letter will you read first when you come back to your room and see the stack on the table? Right, you will read the topmost letter.
- That is, the one that arrived most recently. This is exactly how a stack works.
- This principle is called **"last in first out" (LIFO)**.

### methods of the Stack class:

- push() — adds an item to the top of the stack. When we send a card to the discard pile, it goes to the top of the pile
- pop() — removes the top element from the stack and returns it. This method is perfect for implementing actions in which the player draws a card.
- peek() — returns the top element of the stack, but does not remove it from the stack

![](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-10/resources/images/stack1.PNG)

- Push O(1)
  Pushing a Node onto a stack will always be an O(1) operation. This is because it takes the same amount of time no matter how many Nodes (n) you have in the stack.

- Pop O(1)
  Popping a Node off a stack is the action of removing a Node from the top. When conducting a pop, the top Node will be re-assigned to the Node that lives below and the top Node is returned to the user.

- Peek O(1)
  When conducting a peek, you will only be inspecting the top Node of the stack.

---

## Queues

A queue is a lot like a stack. A Queue is also a linear structure that follows a First In First Out (FIFO) order, but they differ in how elements are removed. Queues are open from both ends: one end for inserting data (enqueue), and the other end for removing data (dequeue).A stack is only open from one end.

![](https://cdn.codegym.cc/images/article/8ec2bdb3-6288-49d4-991e-e573ca7c8fdd/800.webp)

- This principle is easy to understand by considering, for example, an ordinary line, or queue, in real life! For example, a line at the grocery store.

- If there are five people in line, the first one to be served will be the one who entered the line first. If another person (in addition to five already in line) wants to buy something and gets in line, then he gets served last, that is, sixth.

- When working with a queue, new elements are added to the tail (back), and if you want to get an element, it will be taken from the head (front).

![](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-10/resources/images/Queue.PNG)

- Enqueue O(1)
  When you add an item to a queue, you use the enqueue action. This is done with an O(1) operation in time because it does not matter how many other items live in the queue (n); it takes the same amount of time to perform the operation.

- Dequeue O(1)
  When you remove an item from a queue, you use the dequeue action. This is done with an O(1) operation in time because it doesn’t matter how many other items are in the queue, you are always just removing the front Node of the queue.

- Peek O(1)
  When conducting a peek, you will only be inspecting the front Node of the queue.

**Simple difference: For a stack we remove the most recently added element, but for a queue, we remove the “oldest” element.**

### Pros and Cons of Stack and Queues

#### Pros

| Stacks(Pros)                                      | Stacks(Cons)                                              |
| ------------------------------------------------- | --------------------------------------------------------- |
| It is easy to implement and logical for beginners | Random access to elements in a stack is nearly impossible |
| It allows you to control how memory is allocated  | Neither flexible nor scalable                             |
| Easier to use than queues                         | Variables cannot be resized.                              |

| Queue(Pros)                         | Queue(Cons)                                                  |
| ----------------------------------- | ------------------------------------------------------------ |
| flexible.                           | Inserting/ removing elements from the middle is complex.     |
| They can handle multiple data types | Queues are not readily searchable                            |
| Data queues are fast and optimized  | Classical queues don’t have any space for element priorities |

---

Resources :

1. https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-10/resources/stacks_and_queues.html
2. https://www.educative.io/blog/data-structures-stack-queue-java-tutorial
3. https://codegym.cc/groups/posts/291-data-structures-stack-and-queue
4. https://www.quora.com/What-are-the-advantages-and-disadvantages-of-queue-and-stack (only of part of pros and cons)

---
