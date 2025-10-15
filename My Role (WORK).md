### My Contribution to Driving Licence Controlled Smart Vehicle – Multi-Factor Driver Authentication System (MFDAS)
As part of the SafeDrive system, my responsibility was to plan, wire, and assemble the physical hardware that enables driver authentication inside the vehicle.

---

## 🧰 My Role

I worked on the **hardware integration and physical wiring** of the embedded system. This includes:

- Planning connection layout between modules and the controller
- Assembling and testing each component
- Ensuring reliable communication (I2C, SPI, UART)
- Power supply management and pin protection

---

## 🔌 Hardware Used

| Component            | Purpose                                      |
|----------------------|----------------------------------------------|
| **STM32 Controller** | Main controller (Remote device in vehicle)   |
| **RC522 RFID Reader**| Reads encrypted driving license cards        |
| **Fingerprint Sensor (R305)** | Verifies biometric identity         |
| **GPS Module**       | Sends location in case of emergency          |
| **GSM Module (SIM800L)** | Sends alerts (SMS)                        |
| **Relay Module**     | Controls vehicle ignition                    |
| **LCD 16x2 Display** | Shows status & messages                      |
| **Power Supply (12V to 5V)** | For regulated logic level            |

---

## 🔗 Pin Connections

### STM32 GPIO Mapping

| Device              | Connected To STM32 GPIO Pins                 |
|---------------------|----------------------------------------------|
| **RC522 RFID Module** |  
| ├ SDA               | SPI_NSS  
| ├ SCK               | SPI_SCK  
| ├ MOSI              | SPI_MOSI  
| ├ MISO              | SPI_MISO  
| └ RST               | GPIO (Reset)  

| **Fingerprint Sensor (R305)** |  
| ├ TX                | UART_RX  
| └ RX                | UART_TX  

| **GPS Module** |  
| ├ TX                | UART_RX  
| └ RX                | UART_TX  

| **GSM Module (SIM800L)** |  
| ├ TX                | UART_RX  
| └ RX                | UART_TX  

| **Relay (for ignition)** |  
| └ IN1               | GPIO Output  

| **LCD Display (16x2, I2C)** |  
| ├ SDA               | I2C_SDA  
| └ SCL               | I2C_SCL  

| **Buzzer / Alert Pin (Optional)** |  
| └ Signal Pin        | GPIO Output  

---

## ⚡ Power Supply

- All modules receive **regulated 5V** from a **buck converter** connected to the car's 12V battery.
- Used common GND rail for stable communication.
- Fuse added to power input for protection.
- Relay module isolated to avoid reverse current into STM32.

---

## 🔄 System Interaction (From Hardware POV)

1. User unlocks vehicle → System powers on
2. STM32 waits for:
   - RFID Scan (via RC522)
   - Fingerprint match (via UART)
3. On success:
   - Relay triggers → Engine ON
4. On impact detected:
   - GPS data fetched
   - GSM sends emergency alert SMS

---

## 🧠 Notes on Integration

- Signal noise avoided by separating UART lines across GPS, GSM, and fingerprint
- All UART devices tested one-by-one before final assembly
- Used jumper cables + pin headers + breadboard for testing
- Final setup prepared for vehicle dashboard fitting

---

## ✅ Summary of My Work

- 📌 Assembled and wired entire hardware system
- 📌 Mapped and verified all communication interfaces (SPI/UART/I2C)
- 📌 Ensured safe power design with voltage regulators and fuse
- 📌 Built the backbone that makes authentication logic possible

> This hardware infrastructure ensures the **SafeDrive software can run securely, accurately, and reliably**.
