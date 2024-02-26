# Finding All Divisors

#### 2024-02-18

Today, I created a program to find all divisors of an integer.

We used [ChatGPT](https://chat.openai.com/) to debug it.

### Code

#### Python

```python
K=24
for i in range (1,K+1):
  if K/i - int(K/i)==0:
    print (i)
```

#### Execution Results
```
1
2
3
4
6
8
12
24
```