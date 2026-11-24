## LR32_ESP32_Demo 示例教程

```
#include <HardwareSerial.h>

HardwareSerial LR32Serial(2);

void setup() {
  Serial.begin(115200);

  // ESP32 RX=GPIO16，TX=GPIO17
  // 9600 是示例值，需与 LR32 的 UART 波特率一致
  LR32Serial.begin(9600, SERIAL_8N1, 16, 17);

  Serial.println("LR32 UART test ready");
}

void loop() {
  // 电脑 -> ESP32 -> LR32
  while (Serial.available()) {
    LR32Serial.write(Serial.read());
  }

  // LR32 -> ESP32 -> 电脑
  while (LR32Serial.available()) {
    Serial.write(LR32Serial.read());
  }
}
```
<img width="1920" height="1017" alt="ESP32-lr32" src="https://github.com/user-attachments/assets/d411b034-887a-4c77-8293-01835d3a5fc4" />

