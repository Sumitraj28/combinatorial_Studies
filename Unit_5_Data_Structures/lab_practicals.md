# Unit V: Data Structures - Lab Practicals

This guide contains complete, compile-ready C++ implementations, detailed inline comments, and execution walkthroughs for **Practical 8: Arrays & Linked Lists**, **Practical 9: Stacks & Queues**, and **Practical 10: Trees & Binary Search Trees**.

---

## 💻 Practical 8: Singly Linked List

### Task: Implement a Singly Linked List in C++ supporting insertion, deletion, and display operations.

```cpp
#include <iostream>
using namespace std;

// Define a Node structure
struct Node {
    int data;
    Node* next;
    
    // Constructor to initialize a node
    Node(int val) {
        data = val;
        next = nullptr;
    }
};

class SinglyLinkedList {
private:
    Node* head;

public:
    SinglyLinkedList() {
        head = nullptr;
    }

    // 1. Insert at the end of the list
    void insertAtEnd(int val) {
        Node* newNode = new Node(val);
        if (head == nullptr) {
            head = newNode;
            return;
        }
        Node* temp = head;
        while (temp->next != nullptr) {
            temp = temp->next;
        }
        temp->next = newNode;
    }

    // 2. Delete a node by value
    void deleteValue(int val) {
        if (head == nullptr) {
            cout << "List is empty. Deletion failed.\n";
            return;
        }

        // If head node itself holds the value to be deleted
        if (head->data == val) {
            Node* temp = head;
            head = head->next;
            delete temp;
            cout << "Deleted " << val << " from list.\n";
            return;
        }

        Node* curr = head;
        Node* prev = nullptr;

        while (curr != nullptr && curr->data != val) {
            prev = curr;
            curr = curr->next;
        }

        // Value not found
        if (curr == nullptr) {
            cout << "Value " << val << " not found in the list.\n";
            return;
        }

        // Unlink the node from the list
        prev->next = curr->next;
        delete curr;
        cout << "Deleted " << val << " from list.\n";
    }

    // 3. Display the list elements
    void display() {
        if (head == nullptr) {
            cout << "List is empty.\n";
            return;
        }
        Node* temp = head;
        while (temp != nullptr) {
            cout << temp->data << " -> ";
            temp = temp->next;
        }
        cout << "NULL\n";
    }
};

int main() {
    SinglyLinkedList list;
    
    cout << "Inserting elements: 10, 20, 30\n";
    list.insertAtEnd(10);
    list.insertAtEnd(20);
    list.insertAtEnd(30);
    
    cout << "Current List: ";
    list.display();

    cout << "Deleting 20:\n";
    list.deleteValue(20);
    
    cout << "Current List: ";
    list.display();
    
    return 0;
}
```

---

## 💻 Practical 9: Stacks & Queues (Array-Based)

### Task: Implement a Stack and a Queue in C++ using static arrays.

```cpp
#include <iostream>
#define MAX 5 // Max size of stack/queue
using namespace std;

// 1. Stack Implementation (LIFO)
class Stack {
private:
    int top;
    int arr[MAX];

public:
    Stack() {
        top = -1; // Stack is initially empty
    }

    bool push(int val) {
        if (top >= (MAX - 1)) {
            cout << "Stack Overflow! Cannot push " << val << "\n";
            return false;
        }
        arr[++top] = val;
        cout << "Pushed " << val << " onto stack.\n";
        return true;
    }

    int pop() {
        if (top < 0) {
            cout << "Stack Underflow! Stack is empty.\n";
            return -1;
        }
        return arr[top--];
    }

    void display() {
        if (top < 0) {
            cout << "Stack is empty.\n";
            return;
        }
        cout << "Stack (Top to Bottom): ";
        for (int i = top; i >= 0; i--) {
            cout << arr[i] << " ";
        }
        cout << "\n";
    }
};

// 2. Queue Implementation (FIFO)
class Queue {
private:
    int front, rear;
    int arr[MAX];

public:
    Queue() {
        front = -1;
        rear = -1;
    }

    void enqueue(int val) {
        if (rear == MAX - 1) {
            cout << "Queue Overflow! Cannot enqueue " << val << "\n";
            return;
        }
        if (front == -1) front = 0; // Initialize front
        arr[++rear] = val;
        cout << "Enqueued " << val << " in queue.\n";
    }

    int dequeue() {
        if (front == -1 || front > rear) {
            cout << "Queue Underflow! Queue is empty.\n";
            return -1;
        }
        int val = arr[front++];
        // Reset queue pointers if queue becomes empty
        if (front > rear) {
            front = -1;
            rear = -1;
        }
        return val;
    }

    void display() {
        if (front == -1) {
            cout << "Queue is empty.\n";
            return;
        }
        cout << "Queue (Front to Rear): ";
        for (int i = front; i <= rear; i++) {
            cout << arr[i] << " ";
        }
        cout << "\n";
    }
};

int main() {
    cout << "=== Stack Demo ===\n";
    Stack s;
    s.push(10);
    s.push(20);
    s.display();
    cout << "Popped: " << s.pop() << "\n";
    s.display();

    cout << "\n=== Queue Demo ===\n";
    Queue q;
    q.enqueue(100);
    q.enqueue(200);
    q.display();
    cout << "Dequeued: " << q.dequeue() << "\n";
    q.display();

    return 0;
}
```

---

## 💻 Practical 10: Binary Search Tree (BST)

### Task: Implement a BST in C++ with Insertion, Search, and Inorder/Preorder/Postorder traversals.

```cpp
#include <iostream>
using namespace std;

// Define BST Node structure
struct BSTNode {
    int data;
    BSTNode* left;
    BSTNode* right;

    BSTNode(int val) {
        data = val;
        left = nullptr;
        right = nullptr;
    }
};

class BinarySearchTree {
private:
    BSTNode* root;

    // Helper functions for recursion
    BSTNode* insertHelper(BSTNode* node, int val) {
        if (node == nullptr) {
            return new BSTNode(val);
        }
        if (val < node->data) {
            node->left = insertHelper(node->left, val);
        } else if (val > node->data) {
            node->right = insertHelper(node->right, val);
        }
        return node;
    }

    bool searchHelper(BSTNode* node, int val) {
        if (node == nullptr) return false;
        if (node->data == val) return true;
        if (val < node->data) return searchHelper(node->left, val);
        return searchHelper(node->right, val);
    }

    void inorderHelper(BSTNode* node) {
        if (node == nullptr) return;
        inorderHelper(node->left);
        cout << node->data << " ";
        inorderHelper(node->right);
    }

    void preorderHelper(BSTNode* node) {
        if (node == nullptr) return;
        cout << node->data << " ";
        preorderHelper(node->left);
        preorderHelper(node->right);
    }

    void postorderHelper(BSTNode* node) {
        if (node == nullptr) return;
        postorderHelper(node->left);
        postorderHelper(node->right);
        cout << node->data << " ";
    }

public:
    BinarySearchTree() {
        root = nullptr;
    }

    void insert(int val) {
        root = insertHelper(root, val);
    }

    bool search(int val) {
        return searchHelper(root, val);
    }

    void inorder() {
        inorderHelper(root);
        cout << "\n";
    }

    void preorder() {
        preorderHelper(root);
        cout << "\n";
    }

    void postorder() {
        postorderHelper(root);
        cout << "\n";
    }
};

int main() {
    BinarySearchTree bst;
    
    // Insert nodes
    // BST Root will be 50. Left subtree will contain 30, 20, 40. Right will contain 70, 60, 80.
    bst.insert(50);
    bst.insert(30);
    bst.insert(20);
    bst.insert(40);
    bst.insert(70);
    bst.insert(60);
    bst.insert(80);

    cout << "Inorder Traversal (Sorted): ";
    bst.inorder(); // Output: 20 30 40 50 60 70 80

    cout << "Preorder Traversal (Root first): ";
    bst.preorder(); // Output: 50 30 20 40 70 60 80

    cout << "Postorder Traversal (Leaves first): ";
    bst.postorder(); // Output: 20 40 30 60 80 70 50

    int searchKey = 60;
    if (bst.search(searchKey)) {
        cout << "Element " << searchKey << " found in the BST.\n";
    } else {
        cout << "Element " << searchKey << " not found in the BST.\n";
    }

    return 0;
}
```
