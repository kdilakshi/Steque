# Steque
Steque implementation using Array 
class Steque {
    private int[] arr;
    private int front, rear, size, capacity;

    // Constructor
    public Steque(int capacity) {
        this.capacity = capacity;
        this.arr = new int[capacity];
        this.front = -1;
        this.rear = -1;
        this.size = 0;
    }

    // Check if Steque is empty
    public boolean isEmpty() {
        return size == 0;
    }

    // Check if Steque is full
    public boolean isFull() {
        return size == capacity;
    }

    // Push operation (Insert at front)
    public void push(int data) {
        if (isFull()) {
            System.out.println("Steque Overflow! Cannot push " + data);
            return;
        }
        if (isEmpty()) {
            front = rear = 0;
        } else {
            front = (front - 1 + capacity) % capacity;
        }
        arr[front] = data;
        size++;
        System.out.println("Pushed: " + data);
    }

    // Enqueue operation (Insert at rear)
    public void enqueue(int data) {
        if (isFull()) {
            System.out.println("Steque Overflow! Cannot enqueue " + data);
            return;
        }
        if (isEmpty()) {
            front = rear = 0;
        } else {
            rear = (rear + 1) % capacity;
        }
        arr[rear] = data;
        size++;
        System.out.println("Enqueued: " + data);
    }

    // Pop operation (Remove from front)
    public int pop() {
        if (isEmpty()) {
            System.out.println("Steque Underflow! Cannot pop.");
            return -1;
        }
        int poppedValue = arr[front];
        front = (front + 1) % capacity;
        size--;
        System.out.println("Popped: " + poppedValue);
        return poppedValue;
    }

    // Display Steque elements
    public void display() {
        if (isEmpty()) {
            System.out.println("Steque is empty.");
            return;
        }
        System.out.print("Steque Elements: ");
        for (int i = 0; i < size; i++) {
            System.out.print(arr[(front + i) % capacity] + " ");
        }
        System.out.println();
    }
}

// Main class
public class StequeArray {
    public static void main(String[] args) {
        Steque steque = new Steque(5);

        steque.push(10);
        steque.push(20);
        steque.enqueue(30);
        steque.enqueue(40);
        steque.display();

        steque.pop();
        steque.display();

        steque.enqueue(50);
        steque.enqueue(60); // Overflow case
    }
}
