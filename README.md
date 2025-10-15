# 🚗 Driving Licence Controlled Smart Vehicle – Multi-Factor Driver Authentication System (MFDAS)

## 📌 Overview

**SafeDrive** is an advanced driver verification system aimed at preventing **underage and unauthorized driving**, a major contributor to road accidents in India.
This system authenticates a driver’s license using RFID, biometric data, and facial recognition **before** allowing a vehicle to start.

The project consists of two major components:

- 🖥️ **Central Device** (Database Server)
- 🚘 **Remote Device** (Installed in Vehicle - Smart Media Player)

---

## 🧠 Problem Statement

> Underage and unauthorized driving are significant issues leading to road accidents and fatalities.
> SafeDrive ensures that **only valid, licensed individuals** can operate vehicles by verifying driver credentials in real-time.

---

## 🧩 System Architecture

### 1. 🖥️ Central Device – License Creation & Management

Used by authorized personnel (e.g., RTO officials) to issue and manage licenses.

#### License Creation Process:
- 📄 Input Driver Details:
  - Name, Date of Birth, Mobile Number, License Number
  - Approval Date, Expiry Date
- 🆔 RFID Card Scanning: Assigns a unique encrypted RFID card to each user.
- 🧬 Biometric Scan: Captures **right-hand index fingerprint**.
- 📸 Face Capture: Takes a high-resolution photo of the driver.
- 📦 Data Handling:
  - Stores all data in a centralized **MySQL** database.
  - Writes encrypted personal info onto the RFID card.

---

### 2. 🚘 Remote Device – In-Vehicle Authentication System

Installed inside the vehicle, functions as a secure **smart media player** with added safety logic.

#### Authentication Workflow:
- On vehicle unlock, system powers on and prompts for driver validation.
- 🆔 Scan RFID card OR 🧬 fingerprint input.
- ✅ If match is successful:
  - Vehicle engine starts
  - Interface switches to standard media player
- ❌ If validation fails:
  - Engine remains disabled

#### 👁️ Continuous Monitoring:
- Monitors the driver's face during the drive.
- If face does not match the authenticated profile → alerts or disables vehicle.

#### 👤 Profile Management Interface:
Accessible from the top-right profile icon.

| Action           | Description                                                                 |
|------------------|-----------------------------------------------------------------------------|
| **Logout**        | Ends session and powers off engine                                          |
| **Delete Profile**| Removes current user data from the device                                   |
| **Add New Profile**| Requires internet + central database access to verify and download profile |

---

## 🛠️ Technologies Used

| Area                | Technology         |
|---------------------|--------------------|
| Programming Language| **Python 3.x**      |
| Database            | **MySQL** (via `PyMySQL`) |
| UI & Media Layer    | Custom Python UI / Media controls |
| Hardware            | Raspberry Pi / Embedded Linux-based Player |
| RFID                | RC522 / MFRC522 Modules |
| Biometric           | Fingerprint Sensor (e.g., R305) |
| Face Recognition    | OpenCV / dlib / face_recognition library |

---

## 🔐 Security & Validation

- All RFID data is **encrypted** before writing.
- Fingerprints are **hashed** and stored securely.
- Facial recognition ensures continuous, real-time validation.

---

## 🎯 Impact & Vision

By integrating **SafeDrive**, authorities and vehicle manufacturers can:

- ✅ Ensure **only licensed drivers** operate vehicles
- 🚫 Prevent **underage driving**
- 📉 Significantly reduce **road accidents and fatalities**
- 💡 Set the foundation for **digitized, centralized driver verification**

---

## 📦 Future Enhancements

- Cloud sync for license updates
- AI-based distraction monitoring
- Integration with law enforcement for violation alerts
- Mobile app for license management

---

## 👨‍💻 Developed By

Team of passionate innovators building smart embedded systems for **social safety and automation**.

---

## 📜 License

This project is intended for educational and governmental pilot use. Further commercial or production deployment requires appropriate licenses and certifications.

