## Gas Leakage Detection:
### Problem Statement:
To design a circuit using Arduino which alerts us if gas concentration is greater than the threshold value.

### Components Used:
1. Arduino Development Board
2. LED RGB
3. Gas Sensor
4. Piezo buzzer
5. Two 220ohm resistance(for LED RGB)
6. One 1kilo-ohm resistance(for gas sensor)

### Optional 

[How does a Gas sensor work ?](https://lastminuteengineers.com/mq2-gas-senser-arduino-tutorial/#:~:text=Using%20a%20simple%20voltage%20divider,anywhere%20from%20200%20to%2010000ppm)

### Schematic:
![image](https://user-images.githubusercontent.com/85028192/147688019-e1c45e80-100a-4db0-921f-df84517cfb89.png)

### Code Blocks:

<img width="240" alt="image" src="https://user-images.githubusercontent.com/85028192/147727809-41ea4461-55bb-4e4a-b4c6-3353ea4ffd34.png">

### Code:
```cpp
int gas = 0;

void setup()
{
  pinMode(A0, INPUT);
  pinMode(12, OUTPUT);
  pinMode(11, OUTPUT);
  pinMode(7, OUTPUT);
}

void loop()
{
  gas = analogRead(A0);         // Reading gas concentration value 
  if (gas >= 200) {             // Threshold value is 200
    digitalWrite(12, HIGH);     // RED color will glow
    digitalWrite(11, LOW);      // GREEN color will not glow
    tone(7, 5274, 500);         // play tone 100 (E8 = 5274 Hz)
  } else {
    digitalWrite(12, LOW);      // RED color will not glow
    digitalWrite(11, HIGH);     // GREEN color will glow
    noTone(7);                  // no tone
  }
  delay(250);                   // Wait for 250 millisecond(s)

  gas;
}
```
### Tinkercad Link:
https://www.tinkercad.com/things/3d45fg0TqXi
