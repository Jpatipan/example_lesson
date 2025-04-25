# 🚀 Python Learning Summary — Day 3
## 🔍 Topics: Error Handling & Logging

## 📘 หัวข้อที่เรียนวันนี้

- Error Handling ด้วย `try-except`
- Logging ข้อมูลด้วย `logging` module

---

## 🔸 Error Handling (try-except)

### ✅ แนวคิดพื้นฐาน

การใช้ `try-except` ช่วยให้โปรแกรมของคุณไม่พังเมื่อเกิดข้อผิดพลาด โดยคุณสามารถจัดการกับข้อผิดพลาดที่คาดไว้ได้อย่างปลอดภัย

### 🔧 ตัวอย่าง:
```python
try:
    number = int(input("ป้อนตัวเลข: "))
    result = 10 / number
    print("ผลลัพธ์:", result)
except ValueError:
    print("ป้อนค่าที่ไม่ใช่ตัวเลข")
except ZeroDivisionError:
    print("หารด้วยศูนย์ไม่ได้")
except Exception as e:
    print("เกิดข้อผิดพลาด:", e)

## 🔸 Logging
### ✅ แนวคิดพื้นฐาน
Logging คือการบันทึกข้อความหรือเหตุการณ์ต่าง ๆ ที่เกิดขึ้นในโปรแกรม ซึ่งช่วยให้เราตรวจสอบปัญหาย้อนหลังได้

🔧 เริ่มต้นการใช้ Logging:

```python
import logging

logging.basicConfig(
    filename='app.log',
    level=logging.ERROR,
    format='%(asctime)s - %(levelname)s - %(message)s'
)

🔧 ตัวอย่าง Logging ข้อผิดพลาด:

```python
try:
    result = 10 / 0
except ZeroDivisionError:
    logging.error("หารด้วยศูนย์ไม่ได้")


🧪 แบบฝึกหัดที่ทำ
1. อ่านไฟล์ด้วย try-except

```python
try:
    with open('data.txt', 'r') as file:
        print(file.read())
except FileNotFoundError:
    print("ไฟล์ไม่พบ")