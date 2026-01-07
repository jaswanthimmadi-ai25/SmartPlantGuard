# SmartPlantGuard
Industry 4.0-based Smart Irrigation System using ESP32 and sensors
// SmartPlantGuard - ESP32/Arduino Smart Irrigation
// Sensors: Soil Moisture
// Actuators: Water Pump (Relay)

const int soilPin = A0;       // Analog pin for soil moisture sensor
const int pumpPin = 5;        // Digital pin for water pump relay
const int threshold = 400;    // Soil moisture threshold (adjust based on calibration)

void setup() {
  Serial.begin(115200);
  pinMode(pumpPin, OUTPUT);
  digitalWrite(pumpPin, LOW); // Pump OFF initially
}

void loop() {
  int soilValue = analogRead(soilPin); // Read soil moisture
  Serial.print("Soil Moisture: ");
  Serial.println(soilValue);

  if (soilValue < threshold) {
    digitalWrite(pumpPin, HIGH);  // Turn pump ON
    Serial.println("Pump ON - Soil is dry");
  } else {
    digitalWrite(pumpPin, LOW);   // Turn pump OFF
    Serial.println("Pump OFF - Soil is wet");
  }

  delay(2000); // Delay 2 seconds
}
