# Linked Lists
## Singly Linked Lists
**Definition:** linear data structure where each node contains a data & link field. 

**Pros, surmised:** allows efficient insertion and deletion without needing to shift elements.
Tail node (last node): points to null.
```
+-------+    +-------+    +-------+    +-------+
| Data  |--->| Data  |--->| Data  |--->| Data  |---> null
| Link  |    | Link  |    | Link  |    | Link  |
+-------+    +-------+    +-------+    +-------+
```
### How to implement
Basic operations.
**Insert**
```java
public Node insertNode(Node head, int data, int position) {
    Node newNode = new Node(data); // creates a new node that stores 'data'. 
    if (position == 0) {
        newNode.next = head; // Initially newNode was null upon creation because it was fresh. 
        return newNode;
    }
    Node current = head;
    for (int i = 0; i < position - 1; i++) { // traverses the list until you reach the node just before where the new one should go (e.g., for position 3, stop at position 2).
        if (current.next == null) return head; // Position out of bounds
        current = current.next; //if you reach the end before getting there, that means position is invalid (too big), so method returns the original list unchanged. 
    }
    newNode.next = current.next; // insert the new node between current and current.next. New node's 'next' points to what current used to point to.
    current.next = newNode; // current.next is updated to point to the new node.

// before: current -> [nextNode]
// after: current -> newNode -> nextNode]

    return head; //head of the list remains the same unless you inserted at position 0.
}
```

**Delete**
```java
public Node deleteNode(Node head, int position) {
    if (head == null) return null;
    if (position == 0) {
        return head.next;
    }
    Node current = head;
    for (int i = 0; i < position - 1; i++) { // iterate through the list  
        if (current.next == null) return head; // Position out of bounds // 
        current = current.next;
    }
    current.next = current.next.next;
    return head;
}
```
