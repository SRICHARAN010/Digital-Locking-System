#  Digital Locking System with Unauthorized Access Alert

A hardware-based digital security system designed using **discrete combinational and sequential logic ICs**. The system provides password authentication and unauthorized access indication without using a microcontroller.

This project was developed as part of an academic hardware design project.

---

## 📌 Features

-  Password input using a numeric keypad
-  Hardware-based password authentication
-  Password storage using **74194 universal shift registers**
-  Separate password setting and user authentication modes
-  Binary encoding and bitwise password comparison
- 🟢 Correct password → Successful authentication indication
- 🔴 Incorrect password → Unauthorized access indication
-  Buzzer-based alert for invalid password entry
-  Reset functionality
-  Complete circuit design, PCB implementation, simulation, and hardware testing
- No microcontroller used

---

## 🧩 System Architecture

```text
                   ┌───────────────┐
                   │    Keypad     │
                   │ Password Input│
                   └───────┬───────┘
                           │
                           ▼
                   ┌───────────────┐
                   │     74147     │
                   │ Priority      │
                   │ Encoder       │
                   └───────┬───────┘
                           │
                           ▼
                   ┌───────────────┐
                   │    74HC04     │
                   │  NOT Gates    │
                   └───────┬───────┘
                           │
              ┌────────────┴────────────┐
              │                         │
              ▼                         ▼
     ┌─────────────────┐       ┌─────────────────┐
     │ Saved Password  │       │ User Password   │
     │ 74194 Registers │       │ 74194 Registers │
     └────────┬────────┘       └────────┬────────┘
              │                         │
              └────────────┬────────────┘
                           │
                           ▼
                   ┌───────────────┐
                   │    CD4077     │
                   │ XNOR Comparison│
                   └───────┬───────┘
                           │
                           ▼
                   ┌───────────────┐
                   │ Authentication│
                   │     Logic     │
                   └───────┬───────┘
                           │
              ┌────────────┴────────────┐
              │                         │
              ▼                         ▼
       ┌─────────────┐            ┌─────────────┐
       │   Correct   │            │  Incorrect  │
       │  Password   │            │  Password   │
       └──────┬──────┘            └──────┬──────┘
              │                          │
              ▼                          ▼
        🟢 Green LED                🔴 Red LED
        Access Granted              + 🔊 Buzzer
