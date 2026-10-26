# Seven-Segment Display Using Arduino Uno

## 📌 Project Overview

This project demonstrates how to interface a **Common Cathode Seven-Segment Display with Arduino Uno** using the Proteus Design Suite.

The project uses a one-dimensional array to store Arduino pin numbers and binary codes to control individual display segments. The display shows the number sequence **23211102**, displaying each digit one after another.

## 🎯 Objectives

- Interface a seven-segment display with Arduino Uno.
- Understand the working principle of a common cathode display.
- Use a one-dimensional array in Arduino programming.
- Control display segments using binary codes.
- Display a sequence of numbers using a single seven-segment display.
- Simulate the circuit using Proteus.

## 🛠️ Required Components

| Component | Quantity |
|---|---:|
| Arduino Uno | 1 |
| Common Cathode Seven-Segment Display | 1 |
| Resistors (220Ω–330Ω) | 7 |
| Connecting Wires | As required |
| Proteus Design Suite | 1 |

## 🔌 Circuit Connections

The seven display segments are connected to Arduino digital pins as follows.

| Display Segment | Arduino Pin |
|---|---|
| a | D13 |
| b | D12 |
| c | D11 |
| d | D10 |
| e | D9 |
| f | D8 |
| g | D7 |
| COM | GND |

**Note:** Connect each segment through a current-limiting resistor. Connect the common cathode pin(s) to GND.

## 💻 Arduino Source Code

```cpp
byte pin[] = {13, 12, 11, 10, 9, 8, 7};

byte code[] = {
  0b1101101,  // 2
  0b1111001,  // 3
  0b1101101,  // 2
  0b0110000,  // 1
  0b0110000,  // 1
  0b0110000,  // 1
  0b1111110,  // 0
  0b1101101   // 2
};

void setup() {
  for (int i = 0; i < 7; i++) {
    pinMode(pin[i], OUTPUT);
  }
}

void loop() {
  for (int j = 0; j < 8; j++) {
    for (int i = 0; i < 7; i++) {
      digitalWrite(pin[i], bitRead(code[j], 6 - i));
    }
    delay(1000);
  }
}
```

## 🧠 Code Explanation

### 1. Declare the Pin Array

```cpp
byte pin[] = {13, 12, 11, 10, 9, 8, 7};
```

This one-dimensional array stores the Arduino pins connected to segments a through g.

### 2. Define the Binary Codes

```cpp
byte code[] = {
  0b1101101,  // 2
  0b1111001,  // 3
  0b1101101,  // 2
  0b0110000,  // 1
  0b0110000,  // 1
  0b0110000,  // 1
  0b1111110,  // 0
  0b1101101   // 2
};
```

Each binary code specifies which segments should be ON or OFF to display a particular digit.

For a common cathode display:

- `1` means the segment is ON.
- `0` means the segment is OFF.

### 3. Configure the Output Pins

```cpp
void setup() {
  for (int i = 0; i < 7; i++) {
    pinMode(pin[i], OUTPUT);
  }
}
```

The `for` loop configures all seven segment pins as OUTPUT pins.

### 4. Display the Number Sequence

```cpp
for (int j = 0; j < 8; j++) {
  for (int i = 0; i < 7; i++) {
    digitalWrite(pin[i], bitRead(code[j], 6 - i));
  }
  delay(1000);
}
```

- The outer loop selects each digit from the array.
- The inner loop reads the binary bits and controls the seven segments.
- `bitRead(code[j], 6 - i)` reads the required bit.
- `digitalWrite()` switches each segment ON or OFF.
- `delay(1000)` keeps each digit displayed for one second.

## 🔢 Display Sequence

The program displays the following digits in order:

**2 → 3 → 2 → 1 → 1 → 1 → 0 → 2**

| Step | Digit | Binary Code |
|---:|---:|---|
| 1 | 2 | `1101101` |
| 2 | 3 | `1111001` |
| 3 | 2 | `1101101` |
| 4 | 1 | `0110000` |
| 5 | 1 | `0110000` |
| 6 | 1 | `0110000` |
| 7 | 0 | `1111110` |
| 8 | 2 | `1101101` |

Each digit is displayed for approximately one second. After the last digit, the sequence repeats automatically.

## ▶️ How to Run the Project in Proteus

1. Open Proteus Design Suite.
2. Add an Arduino Uno and a common cathode seven-segment display.
3. Connect segments a–g to Arduino pins D13–D7 according to the connection table.
4. Connect the common cathode pin(s) to GND.
5. Add current-limiting resistors to the segment connections.
6. Compile the Arduino sketch and obtain its HEX file if required by your Proteus setup.
7. Load the HEX file into the Arduino Uno component.
8. Run the simulation and observe the displayed sequence.

## ✅ Expected Output

The seven-segment display repeatedly shows:

**23211102**

Because only one digit is displayed at a time, the digits appear sequentially rather than simultaneously.

## 📚 Learning Outcomes

Through this project, I learned how to:

- Interface a seven-segment display with Arduino Uno.
- Understand common cathode display operation.
- Use one-dimensional arrays in Arduino programming.
- Represent digits using binary codes.
- Use `bitRead()` and `digitalWrite()` to control display segments.
- Implement loops to display a sequence of numbers.
- Simulate an Arduino circuit in Proteus.

## 🚀 Future Improvements

- Display digits from 0 to 9.
- Create an automatic digital counter.
- Control the displayed digit using push buttons.
- Interface multiple seven-segment displays.
- Build a digital clock using Arduino.

## 👩‍💻 Author

**Farjana Akter Mim**

GitHub: [@Farjana02mim](https://github.com/Farjana02mim)

## 🔗 Repository

[Seven-Segment-Arduino-Uno](https://github.com/Farjana02mim/Seven-Segment-Arduino-Uno)

---

⭐ If you find this project useful, please consider giving the repository a star!
