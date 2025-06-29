# bluetooth_lcd_display.ino
# 📲 Bluetooth LCD Serial Display – Arduino Project

This project allows you to display characters received via **Bluetooth** onto a **20x4 LCD display** using Arduino UNO.

---

## 🧰 Components Used

- Arduino UNO  
- HC-05 / HC-06 Bluetooth module  
- 20x4 LCD display (HD44780-compatible)  
- Jumper Wires  
- Breadboard  

---

## 🔌 Wiring Summary

| Component         | Arduino Pin |
|------------------|-------------|
| LCD RS           | D12         |
| LCD Enable       | D11         |
| LCD D4           | D5          |
| LCD D5           | D4          |
| LCD D6           | D7          |
| LCD D7           | D6          |
| Bluetooth Tx     | D2 (RxD)    |
| Bluetooth Rx     | D3 (TxD)    |
| LCD VCC/GND      | 5V / GND    |
| Bluetooth VCC    | 3.3V / 5V*  |
| Bluetooth GND    | GND         |

\*Use a voltage divider if your Bluetooth module doesn’t accept 5V.

---

## 💡 How It Works

- Connect a Bluetooth terminal app (like **Serial Bluetooth Terminal**) to your HC-05 module.
- Start typing – characters appear on the LCD.
- Sending character `0` will **clear the LCD display**.
- Useful for **chat displays**, **status updates**, or **Bluetooth terminal experiments**.

---

## 📁 Project Files

- `code/bluetooth_lcd_display.ino` – Arduino sketch

---

## 🧪 Sample Output


- Send: `Hello` → LCD shows: `Hello`
- Send: `0` → LCD clears

---

## 🧠 Suggested Enhancements

- Add scrolling text logic
- Display only when full line is received
- Add visual LED indicators
- Store received messages in EEPROM

---

