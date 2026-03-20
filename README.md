#define BLYNK_TEMPLATE_ID "TMPL6TW0sV4Nb"
#define BLYNK_TEMPLATE_NAME "Motion Detection System"
#define BLYNK_AUTH_TOKEN "Wwz23rsxyT0CVGffgCBxHcg9Izb6RIIO"

#include <WiFi.h>
#include <WiFiClient.h>
#include <BlynkSimpleEsp32.h>

char auth[] = BLYNK_AUTH_TOKEN;
char ssid[] = "Wokwi-GUEST";
char pass[] = "";

int pirPin = 27;
int greenLED = 26;
int redLED = 25;

bool manualGreen = false;
bool manualRed = false;

BLYNK_WRITE(V0) {
  manualGreen = param.asInt();
  digitalWrite(greenLED, manualGreen);
}

BLYNK_WRITE(V1) {
  manualRed = param.asInt();
  digitalWrite(redLED, manualRed);
}

void setup() {
  Serial.begin(115200);

  pinMode(pirPin, INPUT);
  pinMode(greenLED, OUTPUT);
  pinMode(redLED, OUTPUT);

  digitalWrite(greenLED, HIGH);
  digitalWrite(redLED, LOW);

  Blynk.begin(auth, ssid, pass);
}

void loop() {
  Blynk.run();

  int motion = digitalRead(pirPin);

  if (!manualGreen && !manualRed) {
    if (motion == HIGH) {
      digitalWrite(redLED, HIGH);
      digitalWrite(greenLED, LOW);
      Blynk.virtualWrite(V2, "Motion Detected");
    } else {
      digitalWrite(redLED, LOW);
      digitalWrite(greenLED, HIGH);
      Blynk.virtualWrite(V2, "No Motion");
    }
  }
}
