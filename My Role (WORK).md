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
| **Raspberry Pi**     | Main controller (Remote device in vehicle)   |
| **RC522 RFID Reader**| Reads encrypted driving license cards        |
| **Fingerprint Sensor (R305)** | Verifies biometric identity         |
| **GPS Module**       | Sends location in case of emergency          |
| **GSM Module (SIM800L)** | Sends alerts (SMS)                        |
| **Relay Module**     | Controls vehicle ignition                    |
| **LCD 16x2 Display** | Shows status & messages                      |
| **Power Supply (12V to 5V)** | Provides regulated logic level        |

---

## 🔗 Pin Connections

### Raspberry Pi GPIO Mapping

| Device              | Connected To Raspberry Pi GPIO Pins                 |
|---------------------|----------------------------------------------------|
| **RC522 RFID Module** |  
| ├ SDA               | GPIO 8 (SPI_CE0)  
| ├ SCK               | GPIO 11 (SPI_SCK)  
| ├ MOSI              | GPIO 10 (SPI_MOSI)  
| ├ MISO              | GPIO 9 (SPI_MISO)  
| └ RST               | GPIO 25 (Reset)  

| **Fingerprint Sensor (R305)** |  
| ├ TX                | GPIO 15 (UART_RX)  
| └ RX                | GPIO 14 (UART_TX)  

| **GPS Module** |  
| ├ TX                | GPIO 16 (UART_RX – Software UART)  
| └ RX                | GPIO 20 (UART_TX – Software UART)  

| **GSM Module (SIM800L)** |  
| ├ TX                | GPIO 15 (UART_RX)  
| └ RX                | GPIO 14 (UART_TX)  

| **Relay (for ignition)** |  
| └ IN1               | GPIO 21 (Output)  

| **LCD Display (16x2, I2C)** |  
| ├ SDA               | GPIO 2 (I2C_SDA)  
| └ SCL               | GPIO 3 (I2C_SCL)  

| **Buzzer / Alert Pin (Optional)** |  
| └ Signal Pin        | GPIO 18 (PWM / Output)  

---

## ⚡ Power Supply

- All modules receive **regulated 5V** from a **buck converter** connected to the car's 12V battery.
- Common GND used across all modules for stable communication.
- Fuse added to power input for protection.
- Relay module isolated to avoid reverse current into Raspberry Pi.
- SIM800L given a separate regulated 4V supply to prevent Raspberry Pi brownouts.

---

## 🔄 System Interaction (From Hardware POV)

1. User unlocks vehicle → System powers on  
2. Raspberry Pi waits for:  
   - RFID Scan (via RC522)  
   - Fingerprint match (via UART)  
3. On success:  
   - Relay triggers → Engine ON  
4. On impact detected:  
   - GPS data fetched  
   - GSM sends emergency alert SMS  



---

## ✅ Summary of My Work

- 📌 Assembled and wired entire Raspberry Pi–based hardware system  
- 📌 Mapped and verified all communication interfaces (SPI/UART/I2C)  
- 📌 Ensured safe power design with voltage regulators and fuse  
- 📌 Built the backbone that makes authentication logic possible  

> This hardware infrastructure ensures the **SafeDrive system can run securely, accurately, and reliably**.
