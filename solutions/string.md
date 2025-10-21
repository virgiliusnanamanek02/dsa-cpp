# String Data Structure


### Super Reduced String


```cpp
string superReducedString(string s)
{
  string r;

  for (char c : s)
  {
    if (!r.empty() && r.back() == c)
    {
      r.pop_back();
    }
    else
    {
      r.push_back(c);
    }
  }

  if (!r.empty())
  {
    return r;
  }

  return "Empty String";
}
```

### Camel Case

```cpp
int camelcase(string s)
{
  int counter;
  if (!isupper(s[0]))
  {
    counter = 1;
  }

  for (char c : s)
  {
    if (isupper(c))
    {
      counter++;
    }
  }

  return counter;
}
```

## Minimum Number of Password

```cpp
int minimumNumber(int n, string password)
{
  map<string, bool> m{{"numbers", false},
          {"lower_case", false},
          {"upper_case", false},
          {"special_characters", false}};

  for (char c : password)
  {
    if (isdigit(c))
    {
      m["numbers"] = true;
    }
    else if (islower(c))
    {
      m["lower_case"] = true;
    }
    else if (isupper(c))
    {
      m["upper_case"] = true;
    }
    else
    {
      m["special_characters"] = true;
    }
  }

  int missing_types = 0;

  for (auto& pair : m)
  {
    if (pair.second == false)
    {
      missing_types++;
    }
  }

  return max(max(0, 6 - n), missing_types);
}
```
