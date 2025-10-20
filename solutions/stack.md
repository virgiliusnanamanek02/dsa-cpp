## Basic Stack

```cpp
class Stack
{
    private:
        static const int MAX_SIZE = 5;
        int top;
        int arr[MAX_SIZE];

    public:
        Stack() : top(-1) {}

        bool isEmpty() { return top == -1; }

        bool isFull() { return top == MAX_SIZE - 1; }

        void push(int value)
        {
            if (isFull())
            {
                cout << "stack overflow" << endl;
            }
            arr[++top] = value;
        }

        void pop() { top--; }

        int count() { return top + 1; }

        void peak()
        {
            if (isEmpty())
            {
                cout << "stack is undeflow" << endl;
            }
            cout << "Peek: " << arr[top] << endl;
        }

        void change(int pos, int value)
        {
            if (pos < 0 || pos > top)
            {
                cout << "Invalid position!" << endl;
                return;
            }
            arr[pos] = value;
            cout << "Changed position " << pos << " to " << value << endl;
        }

        void display()
        {
            if (isEmpty())
            {
                cout << "Stack is empty!" << endl;
                return;
            }

            cout << "Stack elements (top to bottom):" << endl;
            for (int i = top; i >= 0; i--)
            {
                cout << arr[i] << endl;
            }
        }
};
```

### Reverse String

```cpp
string reverseString(const string& input)
{
  stack<char> s;
  string reversed = "";
  for (char ch : input)
  {
    s.push(ch);
  }

  while (!s.empty())
  {
    reversed += s.top(); // ambil paling atas
    s.pop(); // buang paling atas dari stack
  }

  return reversed;
}
```
