# Calculator

#### 2024-03-17

Today, I created a program to *add numbers*. It works like a calculator. If you type in two numbers separated by a space, it adds them.

I used [ChatGPT](https://chat.openai.com/) to debug it.

### Code

#### Python

```python
# 1. **Sum of Two Numbers** ⭐⭐
#    - Write a Python program to find the sum of two numbers entered by the user.
#    - Input: Two integers separated by a space.
#    - Output: The sum of the two numbers.
#    - Hint: Use the `input()` function to take user input and convert the input string to integers before adding.
#    - Related Python Concepts: Input/Output, Type Conversion, Arithmetic Operations.

print("First number and second number")
typed_in = input()
numbers = typed_in.split()
results = float(numbers[0]) + float(numbers[1])
print(results)
```

#### Execution Results
```
First number and second number
35 46
81.0
```