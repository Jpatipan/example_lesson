# 🚀 Python Learning Summary — Day 1 
## 🔍 Topics: Python Core (พื้นฐานการเขียนโปรแกรมด้วยภาษา Python)

## ✅ Data Types, Conditions, Loops, Functions, Modules
- เข้าใจชนิดข้อมูลพื้นฐานและโครงสร้างข้อมูลใน Python
- ใช้คำสั่งเงื่อนไข (`if-else`) และลูป (`for`, `while`) ได้
- เขียนฟังก์ชันเพื่อเพิ่มความสามารถในการจัดระเบียบโค้ด
- นำเข้าและสร้างโมดูล Python ได้


# 🚀 Python Learning Summary — Day 2  
## 🔍 Topics: List Comprehensions & Generators

---

## ✅ List Comprehensions

### 📌 สิ่งที่เรียนรู้:
- การใช้ List Comprehension เพื่อสร้าง list ใหม่ในรูปแบบที่กระชับและอ่านง่าย
- Syntax: `[expression for item in iterable if condition]`

### 🧪 แบบฝึกหัดที่ทำ:
1. เพิ่มค่าทุกตัวใน list `[1, 2, 3, 4, 5]` ให้มากขึ้น 10 เท่า  
    ```python
    new_lists = [x * 10 for x in [1, 2, 3, 4, 5]]
    ```

2. สร้าง list ของเลขยกกำลังสองที่เป็นเลขคี่ตั้งแต่ 1 ถึง 20  
    ```python
    odd_squares = [x**2 for x in range(21) if x % 2 == 1]
    ```

3. แปลงคำทั้งหมดใน list ให้เป็นตัวพิมพ์ใหญ่  
    ```python
    upper_words = [word.upper() for word in ["apple", "banana", "cherry"]]
    ```

---

## 🔄 Generators

### 📌 สิ่งที่เรียนรู้:
- Generator expressions: `(expression for item in iterable if condition)`
- ฟังก์ชันแบบ `yield` สำหรับสร้าง generator ที่คืนค่าทีละตัว (lazy evaluation)
- เปรียบเทียบ Memory ระหว่าง list และ generator

### 🧪 แบบฝึกหัดที่ทำ:

1. สร้าง generator ที่คืนค่าตัวเลขคู่ตั้งแต่ 0 ถึง 19  
    ```python
    even_gen = (x for x in range(20) if x % 2 == 0)
    ```

2. สร้าง generator ที่รับ list ของคำ แล้วคืนค่าคำที่ยาวเกิน 5 ตัวอักษร  
    ```python
    long_words = (word for word in words if len(word) > 5)

    # หรือใช้ yield
    def long_words_generator(word_list):
        for word in word_list:
            if len(word) > 5:
                yield word
    ```

3. เปรียบเทียบ memory ที่ใช้ระหว่าง list กับ generator  
    ```python
    import sys
    squares_list = [x**2 for x in range(1_000_000)]
    squares_gen = (x**2 for x in range(1_000_000))

    print(sys.getsizeof(squares_list))  # memory สูง
    print(sys.getsizeof(squares_gen))   # memory ต่ำมาก
    ```

---

## 🌟 Advanced Practice:

- ✅ Generator ที่คืนค่าเลขเฉพาะ (Prime Numbers)
- ✅ Generator ที่คืนค่าเลข Fibonacci

```python
# Prime Generator
def is_prime(n):
    if n <= 1:
        return False
    for i in range(2, int(n**0.5) + 1):
        if n % i == 0:
            return False
    return True

def prime_generator(limit):
    for num in range(2, limit + 1):
        if is_prime(num):
            yield num

# Fibonacci Generator
def fibonacci_generator(n):
    a, b = 0, 1
    for _ in range(n):
        yield a
        a, b = b, a + b

# ตัวอย่างการใช้งาน
fib_numbers = fibonacci_generator(10)  # หาตัวเลข Fibonacci 10 ตัวแรก
for num in fib_numbers:
    print(num)