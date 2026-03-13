# 🐍 Python Programming Tasks

A collection of Python utility functions covering bitwise operations, string manipulation, and algorithmic problem-solving.

---

## 📋 Table of Contents

- [Task 1 – XOR Pair Finder](#task-1--xor-pair-finder)
- [Task 2 – Palindrome Checker](#task-2--palindrome-checker)
- [Task 3 – Anagram Detector](#task-3--anagram-detector)
- [Task 4 – Reverse Letters In-Place](#task-4--reverse-letters-in-place)

---

## Task 1 – XOR Pair Finder

Finds all pairs `(i, j)` in a list whose XOR equals a user-specified target value.

### Code

```python
def xor(l):
    l2 = []
    target = int(input("enter the target: "))
    for i in l:
        for j in l:
            if i ^ j == target:
                l2.append((i, j))
    print(l2)

xor([1, 2, 3, 4, 5, 6])
```

### Sample Output

```
enter the target: 3
[(1, 2), (2, 1), (5, 6), (6, 5)]
```

> With input list `[1, 2, 3, 4, 5, 6]` and target `3`:
```
enter the target: 4
[(1, 5), (2, 6), (5, 1), (6, 2)]
```

**Example run with target `7`:**
```
enter the target: 7
[(1, 6), (2, 5), (3, 4), (4, 3), (5, 2), (6, 1)]

```

### Notes

- Uses a brute-force O(n²) approach iterating over all pairs.
- XOR (`^`) returns a value where bits differ between two numbers.
- Includes both `(i, j)` and `(j, i)` as separate results (unordered pairs are not deduplicated).

---

## Task 2 – Palindrome Checker

Checks whether a given string reads the same forwards and backwards.

### Code

```python
def ispalindrome(s):
    rev = (s[::-1])
    if rev == s:
        return 0
    return 1

stri = input("enter the string: ")
pal = ispalindrome(stri)
if pal == 0:
    print(stri, 'is palindrome')
else:
    print(stri, 'not palindrome')
```

### Sample Output

```
enter the string: racecar
racecar is palindrome
```

```
enter the string: hello
hello not palindrome
```

```
enter the string: madam
madam is palindrome
```

### Notes

- Uses Python's slice notation `[::-1]` to reverse the string.
- Case-sensitive: `"Racecar"` would **not** be detected as a palindrome.
- Returns `0` for palindrome and `1` for non-palindrome (convention: `0` = True match).

---

## Task 3 – Anagram Detector

Determines whether two strings are anagrams of each other (contain the same characters, regardless of order or case).

### Code

```python
def angrams(str1, str2):
    return print(sorted(str1.lower()) == sorted(str2.lower()))

angrams("hello", "HELLO")
```

### Sample Output

```python
angrams("hello", "HELLO")
# True

angrams("listen", "silent")
# True

angrams("hello", "world")
# False
```

### Notes

- **Case-insensitive**: both strings are lowercased before comparison.
- Sorts characters alphabetically and compares — an elegant O(n log n) solution.
- `"hello"` and ``"HELLO"` are anagrams since they contain identical characters.

---

## Task 4 – Reverse Letters In-Place

Reverses only the alphanumeric characters in a string while keeping non-alphanumeric characters (e.g. `$`, spaces, punctuation) in their original positions.

### Code

```python
def revlet(text):
    letters = []
    for ch in text:
        if ch.isalnum():
            letters.append(ch)

    result = ""
    for ch in text:
        if ch.isalnum():
            result += letters.pop()
        else:
            result += ch
    return result

print(revlet("a2$mrita"))
```

### Sample Output

```
a2$mrita  →  at$irm2a
```

```python
print(revlet("a2$mrita"))
# Output: at$irm2a

print(revlet("ab$cd"))
# Output: dc$ba

print(revlet("hello world"))
# Output: dlrow olleh
```


```bash
python task1_xor.py
python task2_palindrome.py
python task3_anagram.py
python task4_reverse_letters.py
```

---

## 📁 Project Structure

```
python-tasks/
│
├── Python_tasks.ipynb     # All tasks in a single Jupyter Notebook
└── README.md              # Project documentation
```

---

## 🛠️ Built With

- **Python 3** — Core language
- **Jupyter Notebook** — Interactive development environment

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
