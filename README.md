
```python

def main(number):
    n = int(number, 16)
    return [
        ('01', (n & 1)),
        ('03', ((n >> 5) & 0b11111)),
        ('04', ((n >> 10) & 0b111))
    ]

```


