# Diagnosis-system-for-animals

## DHT11 Sensor

![image](https://github.com/Ravikrishnan05/Diagnosis-system-for-animals-/assets/134152503/10317a80-e946-4803-b032-24462a46992a)
Operating Voltage: 3.5V to 5.5V
Operating current: 0.3mA (measuring) 60uA (standby)

#include "DHT.h"
#define DHT11_PIN 2

DHT dht11(DHT11_PIN, DHT11);

void setup() {
  Serial.begin(9600);
  dht11.begin(); // initialize the sensor
}

void loop() {
  // wait a few seconds between measurements.
  delay(2000);

  // read humidity
  float humi  = dht11.readHumidity();
  // read temperature as Celsius
  float tempC = dht11.readTemperature();
  // read temperature as Fahrenheit
  float tempF = dht11.readTemperature(true);

  // check if any reads failed
  if (isnan(humi) || isnan(tempC) || isnan(tempF)) {
    Serial.println("Failed to read from DHT11 sensor!");
  } else {
    Serial.print("DHT11# Humidity: ");
    Serial.print(humi);
    Serial.print("%");

    Serial.print("  |  "); 

    Serial.print("Temperature: ");
    Serial.print(tempC);
    Serial.print("°C ~ ");
    Serial.print(tempF);
    Serial.println("°F");
  }
}
