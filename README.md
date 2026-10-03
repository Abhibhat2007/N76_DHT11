//Sample code 
#include <Arduino.h>
#include <N76_DHT11.h>   // <-- Conflict-free, dedicated header

N76_DHT11 dht;
const int dhtPin = 3;    // Pin 3 is P1.7 on N76E003

void setup(void) {
    Serial.begin(115200);
    delay(200);
    N76_DHT11_init(&dht, dhtPin);
}

void loop(void) {
    if (N76_DHT11_read(&dht) == DHT11_OK) {
        Serial.print("Humidity: ");
        Serial.print_num(dht.humidity);
        Serial.print(" %  |  Temperature: ");
        Serial.print_num(dht.temperature);
        Serial.println(" C");
    }
    delay(2000);
}
