#Задание 1
```
def convert_types(data):
    result = []
    for item in data:
        if type(item) in (int, float):
            result.append(str(item))
        elif type(item) == str:
            try:
                result.append(int(item))
            except ValueError:
                try:
                    result.append(float(item))
                except ValueError:
                    result.append(item)
        else:
            result.append(str(item))
    return result
```
#Задание 2
```
def swap_values(a, b):
    a, b = b, a
    return a, b
```
#Задание 3
```
def bool_transform(value):
    if value:
        return True
    return False
```
#Задание 4
```
def compound_operations(a, b):
    results = []
    val = a
    val += b
    results.append(val)
    val = a
    val -= b
    results.append(val)
    val = a
    val *= b
    results.append(val)
    val = a
    val /= b
    results.append(val)
    val = a
    val //= b
    results.append(val)
    val = a
    val %= b
    results.append(val)
    val = a
    val **= b
    results.append(val)
    return results
```

#Задание 5
```
def check_type(value, expected_type):
    return type(value).__name__ == expected_type
```
#Задание 6
```
def logical_and(a, b, c):
    if a:
        if b:
            if c:
                return True
    return False
```
#Задание 7
```
def logical_or(a, b, c):
    if a:
        return True
    if b:
        return True
    if c:
        return True
    return False
```
#Задание 8
```
def is_between(value, low, high):
    if value >= low and value <= high:
        return True
    else:
        return False
```
#Задание 9
```
def print_even_numbers(n):
    for i in range(2, n + 1, 2):
        print(i)
```
#Задание 10
```
def countdown_while(n):
    while n >= 1:
        print(n)
        n -= 1
```
#Задание 11
```
def skip_multiples(n, multiple):
    for i in range(1, n + 1):
        if i % multiple == 0:
            continue
        print(i)
```
#Задание 12
```
def if_elif_else_chain(x):
    if x > 0:
        return "positive"
    elif x < 0:
        return "negative"
    else:
        return "zero"
```
#Задание 13
```
def abs_value(x):
    if x < 0:
        return -x
    return x
```
#Задание 14
```
def binary_representation(n):
    if n == 0:
        return "0"
    res = ""
    num = n
    while num > 0:
        res = str(num % 2) + res
        num //= 2
    return res
```
#Задание 15
```
def custom_round(number, ndigits):
    multiplier = 10 ** ndigits
    if number >= 0:
        return int(number * multiplier + 0.5) / multiplier
    else:
        return int(number * multiplier - 0.5) / multiplier
```
#Задание 16
```
def find_max_min(numbers):
    if not numbers:
        return None
    max_val = numbers[0]
    min_val = numbers[0]
    for num in numbers[1:]:
        if num > max_val:
            max_val = num
        if num < min_val:
            min_val = num
    return max_val, min_val
```
#Задание 17
```
def all_true(iterable):
    for item in iterable:
        if not item:
            return False
    return True
```
#Задание 18
```
def any_true(iterable):
    for item in iterable:
        if item:
            return True
    return False
```
#Задание 19
```
def custom_enumerate(sequence, start=0):
    result = []
    index = start
    for item in sequence:
        result.append((index, item))
        index += 1
    return result
```
#Задание 20
```
def custom_filter(func, iterable):
    result = []
    for item in iterable:
        if func(item):
            result.append(item)
    return result
```
#Задание 21
```
def custom_map(func, iterable):
    result = []
    for item in iterable:
        result.append(func(item))
    return result
```
#Задание 22
```
def custom_zip(list1, list2):
    result = []
    length = len(list1) if len(list1) < len(list2) else len(list2)
    for i in range(length):
        result.append((list1[i], list2[i]))
    return result
```
#Задание 23
```
def custom_reversed(sequence):
    result = []
    for i in range(len(sequence) - 1, -1, -1):
        result.append(sequence[i])
    return result
```
#Задание 24
```
def custom_sorted(iterable, reverse=False):
    arr = list(iterable)
    n = len(arr)
    for i in range(n):
        for j in range(0, n - i - 1):
            if reverse:
                if arr[j] < arr[j + 1]:
                    arr[j], arr[j + 1] = arr[j + 1], arr[j]
            else:
                if arr[j] > arr[j + 1]:
                    arr[j], arr[j + 1] = arr[j + 1], arr[j]
    return arr
```
#Задание 25
```
def sum_digits(n):
    n = abs(n)
    total = 0
    while n > 0:
        total += n % 10
        n //= 10
    return total
```
#Задание 26
```
def count_vowels(text):
    vowels = "aeiouAEIOU"
    count = 0
    for char in text:
        if char in vowels:
            count += 1
    return count
```
#Задание 27
```
def power(base, exp):
    if exp < 0:
        return 1 / power(base, -exp)
    result = 1
    for _ in range(exp):
        result *= base
    return result
```
#Задание 28
```
def is_prime(n):
    if n <= 1:
        return False
    for i in range(2, int(n**0.5) + 1):
        if n % i == 0:
            return False
    return True
```
#Задание 29
```
def factorial(n):
    if n < 0:
        return None
    result = 1
    for i in range(1, n + 1):
        result *= i
    return result
```
#Задание 30
```
def fibonacci(n):
    if n <= 0:
        return 0
    if n == 1:
        return 1
    a, b = 0, 1
    for _ in range(2, n + 1):
        a, b = b, a + b
    return b
```
