#include<iostream>
using namespace std;

template <typename T>
class Stack {
    T* array;//指向T的指针变量，此时不知道数组大小，所以用动态数组
    int top;
    int capacity;
public:
    Stack(int size) {
        top = 0;
        capacity = size;
        array = new T[capacity];//大小为capacity的动态数组
    }//构造函数

    bool isFull() {
        return (top == capacity);
    }//是否满载

    bool isEmpty() {
        return (top == 0);
    }//是否为空

    void push(T item) {
        if (isFull()) {
            cout << "Stack is full. Can't push " << item << endl;
            return;
        }
        array[top++] = item;
        cout << item << " pushed to stack\n";
    }//压入元素

    T pop() {
        if (isEmpty()) {
            cout << "Stack is empty. Can't pop\n";
            return 0;
        }
        return array[--top];
    }//弹出元素

    T peek() {
        if (isEmpty()) {
            cout << "Stack is empty. Can't peek\n";
            return 0;
        }
        return array[top-1];//top不变，只是引用了top的值
    }//获取栈顶
};

int main() {
    Stack<int> stack(5);
    stack.push(10);
    stack.push(20);
    stack.push(30);
    cout << stack.pop() << " popped from stack" << endl;
    return 0;
}
