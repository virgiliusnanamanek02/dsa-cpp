
### Basic Array

```cpp
void arr()
{
    int number[4] = {10, 20, 30, 40};

    for (int i = 0; i < std::size(number); i++)
    {
        cout << number[i] << endl;
    }
}
```

### Iterate Array

```cpp
int main()
{
  vector<int> v{1, 2, 3, 4, 5};
  for (int i = 0; i < int(size(v)); i++)
  {
    cout << v[i] << " ";
  }

  cout << endl;

  vector<int> w{1, 7, 4, 5, 2};

  for (auto it = begin(w); it != end(w); it = next(it))
  {
    cout << *it << " ";
  }

  cout << endl;
  vector<int> x{3, 8, 9, 0, 1};
  for (int element : x)
  {
    cout << element << " ";
  }
}
```


## Two Pointers

### reverse array without create new array

```cpp
int main()
{
  int arr[] = {1, 2, 3, 4, 5};
  int n = 5;

  int left = 0;
  int right = n - 1;

  while (left < right)
  {
    swap(arr[left], arr[right]);
    left++;
    right--;
  }

  for (int i = 0; i < n; i++)
  {
    cout << arr[i] << " ";
  }

  return 0;
}
```

### Pair Sum Problem

```cpp
int main()
{
  int arr[] = {1, 3, 4, 5, 7, 10, 11};
  int n = 7;
  int target = 9;

  int left = 0;
  int right = n - 1;
  bool found = false;
  while (left < right)
  {
    int sum = arr[left] + arr[right];

    if (sum == target)
    {
      found = true;
      break;
    }

    if (sum < target)
    {
      left++;
    }
    else
    {
      right--;
    }
  }

  if (found)
  {
    cout << "YES" << endl;
  }
  else
  {
    cout << "NO" << endl;
  }

  return 0;
}
```
