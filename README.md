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

## 📁 CODE

#include <Wire.h>
#include <LiquidCrystal.h> // LCD display library
#define BACKLIGHT_PIN 13

// LCD configuration
const int rs = 12, en = 11, d4 = 5, d5 = 4, d6 = 7, d7 = 6;
LiquidCrystal lcd(rs, en, d4, d5, d6, d7);

#include <SoftwareSerial.h>
#define TxD 3 
#define RxD 2 
#define LED_PIN 13

SoftwareSerial bluetoothSerial(TxD, RxD); // Bluetooth serial

char c;

void setup() {
  bluetoothSerial.begin(9600); // Bluetooth communication
  lcd.begin(20, 4);            // 20x4 LCD
  Serial.begin(9600);          // Serial Monitor
}

void loop() {
  if (bluetoothSerial.available() > 0) {
    c = bluetoothSerial.read();
    lcd.print(c); 

    if (c == '0') {
      lcd.clear(); // Clear screen on receiving '0'
    }

    Serial.print(c); // Also print to Serial Monitor
  } 
}




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

