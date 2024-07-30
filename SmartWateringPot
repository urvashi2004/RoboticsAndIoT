#define BLYNK_PRINT Serial
#define BLYNK_TEMPLATE_ID "TMPL3VFIWAiSE"
#define BLYNK_TEMPLATE_NAME "Irrigation"
#define BLYNK_AUTH_TOKEN "LPez6z-1lm217wWOka9ZebAARlIG5Mdp"

#include <ESP8266WiFi.h>
#include <BlynkSimpleEsp8266.h>

const char* ssid = "Athena";
const char* pass = "hello123";

// Pin definitions
const int moistureSensorPin = A0; // Soil moisture sensor connected to A0
const int motorPin = 4; // GPIO2, D2 in NodeMCU (adjust as needed)

// Moisture sensor calibration values
const int dry = 1; // Value for dry sensor
const int wet = 400; // Value for wet sensor

// Variables
int moistureValue = 0;

void setup() {
  Serial.begin(9600);
  Serial.println("Starting setup...");

  // Pin mode setup
  pinMode(moistureSensorPin, INPUT);
  pinMode(motorPin, OUTPUT);

  // Blynk setup
  Serial.println("Connecting to WiFi...");
  Blynk.begin(BLYNK_AUTH_TOKEN, ssid, pass);
}

void loop() {
  // Run Blynk
  Blynk.run();
  
  // Read soil moisture value
  moistureValue = analogRead(moistureSensorPin);
  
  // Map the sensor value to percentage
  int moisturePercentage = map(moistureValue, wet, dry, 100, 0);
  
  // Print sensor value to serial monitor
  Serial.print("Moisture Value: ");
  Serial.println(moistureValue);
  
  // Send moisture level to Blynk
  Blynk.virtualWrite(V6, moisturePercentage);
  
  // Control motor based on Blynk button state
  // Motor state is controlled by the button on V2
  // The motorPin will be controlled by the BLYNK_WRITE(V2) function

  // Delay to avoid flooding the serial monitor
  delay(1000);
}

// Blynk Button handler to control motor
BLYNK_WRITE(V2) {
  int pinValue = param.asInt();
  Serial.print("Motor control pin value: ");
  Serial.println(pinValue);
  if (pinValue == 1) {
    Serial.println("Turning motor ON");
    digitalWrite(motorPin, HIGH); // Turn motor on
  } else {
    Serial.println("Turning motor OFF");
    digitalWrite(motorPin, LOW); // Turn motor off
  }
}
