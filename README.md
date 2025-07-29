# Keylogger เพื่อการศึกษา (Educational Keylogger)

![Python](https://img.shields.io/badge/python-3.8+-blue.svg)
![Keylogger](https://img.shields.io/badge/Keylogger-8A2BE2)

โปรเจกต์นี้เป็น Keylogger พื้นฐานที่สร้างขึ้นด้วยภาษา Python เพื่อสาธิตวิธีการดักจับและบันทึกการกดแป้นพิมพ์ โปรเจกต์นี้มีวัตถุประสงค์เพื่อการศึกษาและทำความเข้าใจหลักการทำงานของซอฟต์แวร์ประเภทนี้เท่านั้น

## ⚠️ คำเตือนและข้อจำกัดความรับผิดชอบ

โปรเจกต์นี้สร้างขึ้นเพื่อ **วัตถุประสงค์ทางการศึกษาเท่านั้น** **ห้าม** นำไปใช้ในทางที่ผิดกฎหมายหรือละเมิดความเป็นส่วนตัวของผู้อื่นโดยเด็ดขาด ผู้พัฒนาไม่มีส่วนรับผิดชอบต่อความเสียหายใด ๆ ที่เกิดจากการนำโค้ดนี้ไปใช้งานในทางที่ผิด

---

## เกี่ยวกับโปรเจกต์

โปรเจกต์นี้ประกอบด้วย 2 ส่วนหลัก:
1.  **`keylogger.py`**: สคริปต์หลักที่ทำงานเบื้องหลัง ทำหน้าที่ดักจับการกดแป้นพิมพ์ทั้งหมด (Keystroke) และบันทึกลงในไฟล์ `key_log.txt`
2.  **`keylogger_gui.py`**: โปรแกรมส่วนหน้า (GUI) ที่ใช้ `Tkinter` สำหรับควบคุมการทำงานของ Keylogger ทำให้ผู้ใช้สามารถสั่ง เริ่ม, หยุด และดูสถานะได้อย่างง่ายดาย

## ✨ คุณสมบัติหลัก

-   **บันทึกการกดปุ่ม**: สามารถบันทึกการกดปุ่มตัวอักษร, ตัวเลข, และปุ่มพิเศษ (เช่น Enter, Shift, Backspace) ได้
-   **รองรับภาษาไทย**: บันทึกตัวอักษรภาษาไทยได้อย่างถูกต้อง
-   **GUI สำหรับควบคุม**: มีหน้าต่างสำหรับสั่งเริ่ม/หยุดการทำงานของ Keylogger
-   **แสดงสถานะ**: บอกสถานะการทำงานปัจจุบัน (กำลังทำงาน / ไม่ทำงาน) พร้อม Process ID (PID)
-   **ทำงานใน System Tray**: สามารถย่อหน้าต่างโปรแกรมลงไปเก็บไว้ใน System Tray ได้ เพื่อไม่ให้รบกวนการทำงานบนหน้าจอหลัก

## 🖼️ ภาพหน้าจอ (Screenshots)

นี่คือตัวอย่างหน้าตาของโปรแกรมและผลลัพธ์การทำงาน

| หน้าต่างควบคุม (สถานะ: หยุดทำงาน) | หน้าต่างควบคุม (สถานะ: กำลังทำงาน) |
| :------------------------------: | :--------------------------------: |
| <!-- Placeholder for image 1: GUI stopped --> <img src="https://img5.pic.in.th/file/secure-sv1/Screenshot-2025-07-29-003251.png" alt="GUI Stopped" width="350"> | <!-- Placeholder for image 2: GUI running --> <img src="https://img2.pic.in.th/pic/Screenshot-2025-07-29-003347.png" alt="GUI Running" width="350"> |

| ตัวอย่างไฟล์ Log | ไอคอนใน System Tray | กล่องข้อความแจ้งเตือน |
| :---------------------------: | :-----------------: | :-----------------: |
| <!-- Placeholder for image 3: Log file example --> <img src="https://img2.pic.in.th/pic/Screenshot-2025-07-29-003530.png" alt="Log File Example" width="350"> | <!-- Placeholder for image 4: Tray icon --> <img src="https://cdn-icons-png.flaticon.com/128/4616/4616403.png" alt="System Tray Icon" width="350"> | <!-- Placeholder for image 5: Message box --> <img src="https://img5.pic.in.th/file/secure-sv1/Screenshot-2025-07-29-003557.png" alt="Message Box" width="350"> |

## 🚀 การติดตั้งและใช้งาน

1.  **Clone repository นี้:**
    ```bash
    Run kryloggerapp.exe
    ```
2.  ใช้ปุ่มในหน้าต่างโปรแกรมเพื่อควบคุมการทำงาน:
    -   **เริ่ม Keylogger**: เพื่อเริ่มการบันทึก
    -   **หยุด Keylogger**: เพื่อหยุดการบันทึก
    -   **บันทึก Log**: จะมีข้อความยืนยันว่าไฟล์ `key_log.txt` ถูกสร้างขึ้นแล้ว และคุณสามารถเปิดดูได้ในโฟลเดอร์เดียวกับโปรแกรม

## 📝 โค้ด

### `keylogger_gui.py` (หน้าต่างควบคุม GUI)
สคริปต์นี้สร้างหน้าต่างควบคุมด้วย `Tkinter` และใช้ `psutil` ในการจัดการ Process ของ `keylogger.py` รวมถึงใช้ `pystray` เพื่อสร้างไอคอนใน System Tray

```python
import tkinter as tk
from tkinter import messagebox
import psutil, shutil, subprocess, os, signal
from PIL import Image, ImageDraw
import pystray
import threading
import requests
from io import BytesIO
import keyboard

LOG_FILE = "key_log.txt"
keylogger_thread = None
keylogger_running = False

# ---------------- Keylogger Core ----------------
...
# ---------------- Tray Icon ----------------
...
# ---------------- GUI ----------------
...
```
