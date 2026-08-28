# 🔐 Digital Locking System with Unauthorized Access Alert

A hardware-based digital locking system designed using **discrete digital logic ICs**, without using a microcontroller. The system allows a user-defined password to be stored, verifies the entered password using digital logic, and provides visual and audible alerts for unauthorized access attempts.

---

## 📌 Overview

This project implements a secure electronic locking system using fundamental digital electronics concepts.

The system operates in two modes:

- **Client Mode** – Used to set or update the saved password.
- **User Mode** – Used to enter a password for authentication.

The entered password is converted into binary, stored using shift registers, and compared with the saved password using XNOR logic.

- ✅ Correct password → Green LED indicates successful authentication.
- ❌ Incorrect password → Red LED and buzzer indicate unauthorized access.

---

## 🏗️ System Architecture

```text
                    ┌─────────┐
                    │  Reset  │
                    └────┬────┘
                         │
                ┌────────▼────────┐
                │ Mode Selection  │
                │ Client / User   │
                └────────┬────────┘
                         │
                    ┌────▼────┐
                    │ Keypad  │
                    └────┬────┘
                         │
                    ┌────▼─────┐
                    │ Encoder  │
                    └────┬─────┘
                         │
              ┌──────────┴──────────┐
              │                     │
      ┌───────▼────────┐   ┌────────▼───────┐
      │ Saved Password │   │ User Password  │
      │ Shift Registers│   │ Shift Registers│
      └───────┬────────┘   └────────┬───────┘
              │                     │
              └──────────┬──────────┘
                         │
                   ┌─────▼─────┐
                   │ Password  │
                   │ Comparison│
                   └─────┬─────┘
                         │
              ┌──────────┴──────────┐
              │                     │
        ┌─────▼─────┐         ┌─────▼─────┐
        │ Correct   │         │ Incorrect │
        │ Password  │         │ Password  │
        └─────┬─────┘         └─────┬─────┘
              │                     │
         Green LED              Red LED +
          Unlock                 Buzzer
