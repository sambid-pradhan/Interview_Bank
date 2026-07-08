**Source:** Python Fundamentals · Coding Interview Question

## Question

1. Given a list of numbers, write a Python function to find the **second highest** number.

## Answer

```python
def second_highest(numbers):
    numbers = list(set(numbers))
    numbers.sort()
    return numbers[-2]


numbers = [1, 3, 2, 4, 4, 5, 6, 6]
print(second_highest(numbers))
```

**Output**

```python
5
```

**Time Complexity:** O(n log n)

---

**Source:** Python Fundamentals · Coding Interview Question

## Question

2. Write a function to compute the **factorial** of a number using recursion.

## Answer

```python
def factorial(n):
    if n == 0:
        return 1
    return n * factorial(n - 1)


print(factorial(5))
```

**Output**

```python
120
```

**Time Complexity:** O(n)

---

**Source:** Python Fundamentals · Coding Interview Question

## Question

3. Given a list of strings, write a function to filter out all strings that are **palindromes**.

## Answer

```python
def filter_palindromes(words):
    return [word for word in words if word == word[::-1]]


words = ["radar", "python", "level", "world"]
print(filter_palindromes(words))
```

**Output**

```python
['radar', 'level']
```

**Time Complexity:** O(n * m)

where:

- `n` = number of strings
- `m` = average string length

---

**Source:** Python Fundamentals · Coding Interview Question

## Question

4. Given a string, write a function to check if it is an **anagram** of another string.

## Answer

```python
def are_anagrams(s1, s2):
    return sorted(s1) == sorted(s2)


print(are_anagrams("listen", "silent"))
```

**Output**

```python
True
```

**Time Complexity:** O(n log n)

---

**Source:** Python Fundamentals · Coding Interview Question

## Question

5. Write a function to **flatten a nested list**.

## Answer

```python
def flatten(lst):
    result = []
    for item in lst:
        if isinstance(item, list):
            result.extend(flatten(item))
        else:
            result.append(item)
    return result


nested = [1, [2, 3, [4, 5]], 6]
print(flatten(nested))
```

**Output**

```python
[1, 2, 3, 4, 5, 6]
```

**Time Complexity:** O(n), where `n` is the total number of elements.
