# 🔐 Linux Keylogger (Educational & Ethical Use Only)

A lightweight Linux keylogger written in **C**, created purely for **educational**, **research**, and **system programming** learning.  
It demonstrates how Linux captures keyboard input at a low level using `/dev/input` devices and how to build a daemonized monitoring tool.

---

## 📘 Overview

This keylogger listens to keyboard events from the Linux input subsystem (`/dev/input/event*`), translates raw keycodes into readable characters using a full keymap, and logs them to a file. It is ideal for understanding:

- Linux device file interaction  
- Low-level input event handling  
- Daemon creation (`fork()`, `setsid()`)  
- Continuous event-driven logging  
- System-level programming concepts  

---

## ⚙️ Features

- Captures keystrokes directly from the kernel input event system  
- Maps raw keycodes to human-readable text  
- Runs silently as a background daemon  
- Logs events to a configurable text file  
- Designed for Linux (root access required)

---

## 🛠️ Installation

### **1. Clone the file **


   Copy the keylogger.c file and open terminal 


### **2. Compile the Keylogger**

```sh
gcc -o keylogger keylogger.c
```

If you get errors, install the required development packages:

```sh
sudo apt install build-essential linux-headers-$(uname -r)
```

---

## 🚀 How to Use the Keylogger

### **Step 1: Identify Your Keyboard Event File**

Run:

```sh
ls /dev/input/
use evtest by installing it
Ex: sudo apt install evtest //for debian based distros 
```

Most systems use something like:

```
/dev/input/event3
```

You can verify by checking:

```sh
sudo cat /dev/input/event3
```

Press any key — if binary garbage appears, that's your keyboard.

If your event number differs, update this line in the code:

```c
#define KEYBOARD_DEVICE "/dev/input/event3"
```

---

### **Step 2: Edit Log File Location (Optional)**

Inside the code:

```c
#define LOG_FILE "log_file_location"
```

You can change this to any writable path.

---

### **Step 3: Run the Keylogger as Root**

```sh
sudo ./keylogger
```

The program daemonizes, so you won’t see any output.

---

### **Step 4: Verify It Is Running**

Run:

```sh
ps aux | grep keylogger
```

If it shows a running process, the keylogger is active.

---

### **Step 5: View Logged Keystrokes**

```sh
cat /home/sunil/Downloads/keystrokes.txt
```

You will see entries like:

```
A
B
SPACE
ENTER
H
E
L
L
O
```

---

### **Step 6: Stop the Keylogger**

```sh
sudo pkill keylogger
```

---

## 🧠 How It Works (Technical Summary)

1. Opens `/dev/input/eventX` to read keyboard events
2. Listens for `EV_KEY` events where `value == 1` (key press)
3. Looks up each keycode in a large keymap
4. Daemonizes and redirects I/O to `/dev/null`
5. Writes all recognized keys to a log file

This demonstrates real Linux internals: event devices, system calls, daemon processes, and file logging.

---

## 📚 Educational Purpose

This project teaches:

* Input event handling
* Device interfacing in Linux
* Daemon programming
* Low-level C programming
* System monitoring techniques

It is NOT meant for malicious use.

---

## ⚠️ Ethical & Legal Disclaimer

This keylogger is strictly for **authorized**, **ethical**, and **educational** use.

You must only run it on:

* Your own system
* A system where you have explicit permission
* A lab/testing environment

Unauthorized keylogging is illegal and violates privacy laws.

By using this program, you agree to operate responsibly.

---

## 📌 Future Enhancements

* Add timestamps to logs
* Support multiple input devices
* Encrypt log files
* Create a monitoring dashboard
* Implement log rotation

---

## 📝 License

Released for **learning and research only**.
You may use, modify, and distribute ethically.
The author is not responsible for misuse.

---

## 🤝 Contributing

Contributions, improvements, and educational extensions are welcome. Ensure code follows ethical standards.

```


Just tell me!
```
