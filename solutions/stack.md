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


### Match Pairing

```cpp
bool isMatchingPair(char open, char close)
{
  return (open == '(' && close == ')') || (open == '[' && close == ']') ||
         (open == '{' && close == '}');
}

bool isBalanced(const string& expr)
{
  stack<char> s;

  for (char ch : expr)
  {
    if (ch == '(' || ch == '{' || ch == '[')
    {
      s.push(ch); // Kurung buka → push
    }
    else if (ch == ')' || ch == '}' || ch == ']')
    {
      if (s.empty() || !isMatchingPair(s.top(), ch))
      {
        return false;
      }
      s.pop();
    }
  }

  return s.empty();
}
```


### Cow Signal

```cpp
void solve()
{
  // 1. Membaca input M, N, dan K
  int M, N, K;
  if (!(cin >> M >> N >> K))
  {
    return;
  }

  // 2. Membaca sinyal asli
  // Kita simpan sinyal asli sebagai vektor dari string
  vector<string> sinyal_asli(M);
  for (int i = 0; i < M; ++i)
  {
    cin >> sinyal_asli[i];
  }

  // 3. Memproses dan Mencetak sinyal yang diperbesar

  // Iterasi melalui setiap baris (row) dari sinyal asli (M baris)
  for (int i = 0; i < M; ++i)
  {

    // Baris asli yang sedang diproses
    const string& baris_asli = sinyal_asli[i];

    // String untuk menyimpan baris yang telah diperbesar secara horizontal
    string baris_diperbesar_horizontal = "";

    // a. Perbesaran Horizontal (N -> K*N)
    // Iterasi melalui setiap karakter dalam baris asli
    for (char karakter : baris_asli)
    {
      // Gandakan setiap karakter K kali
      for (int k = 0; k < K; ++k)
      {
        baris_diperbesar_horizontal += karakter;
      }
    }

    // b. Perbesaran Vertikal (M -> K*M)
    // Cetak baris yang telah diperbesar secara horizontal sebanyak K kali
    for (int k = 0; k < K; ++k)
    {
      cout << baris_diperbesar_horizontal << endl;
    }
  }
}
```
