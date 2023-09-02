# Home Voltage Sensor

An AC voltage meter to detect and notify under or over voltage in the house

## Materials

- ESP8266 (or ESP32)
- ZMPT101B module

## Wiring

| ZMPT101B | ESP8266 | ESP32     |
| -------- | ------- | --------- |
| vcc      | 3.3v    | 3.3v      |
| gnd      | gnd     | gnd       |
| out      | A0      | D32 - D34 |

## ZMPT101B module calibration

To calibrate the ZMPT101B module you can use the Arduino IDE to load the following code into the ESP replacing _A0_ with the ESP pin connected to the _out_ pin of the ZMPT101B module.

```c++
void setup() {
  Serial.begin(115200);
  pinMode(A0, INPUT);
}

void loop() {
  Serial.println(analogRead(A0));
}
```

Once running use the Serial Plotter (tools -> Serial Plotter) to see the curve, if the curve is clipping use the potentiometer to fix it.

## Readings calibration

To calibrate the voltage reported by the sensor disable the _throttle_ and _debounce_ filters and use the _calibrate_linear_ filter to map the adc reported value to the actual voltage.
