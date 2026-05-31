# smart home automation_project
Smart Home Automation using ESP32 and Blynk IoT is an Internet of Things (IoT) based project designed to remotely control household appliances through a smartphone application. The system uses the ESP32 microcontroller, which provides built-in Wi-Fi connectivity, enabling seamless communication between the hardware and the Blynk cloud platform. In this project, two LEDs are used to represent home appliances such as a light bulb and a fan. Through the Blynk mobile application, users can switch these appliances ON or OFF from anywhere with an internet connection. The project was developed and tested using the Wokwi online simulator, eliminating the need for physical hardware during the development phase. The ESP32 receives commands from virtual buttons configured in the Blynk dashboard using virtual pins V0 and V1. Based on the received command, the corresponding GPIO pins are activated, turning the connected devices ON or OFF. This project demonstrates the practical implementation of IoT concepts such as cloud connectivity, remote monitoring, wireless communication, and real-time device control. The use of ESP32 makes the system cost-effective, energy-efficient, and highly scalable for future enhancements. Additional sensors and actuators can be integrated to support advanced smart home features such as temperature monitoring, motion detection, energy management, voice control, and automated scheduling. The project highlights the importance of IoT in modern home automation systems by providing convenience, improved accessibility, and efficient device management. It also serves as an educational platform for learning embedded systems, IoT communication protocols, cloud-based device control, and mobile application integration. The successful simulation and testing of this project demonstrate how smart technologies can be used to create intelligent and user-friendly home environments. This project is suitable for students, beginners in IoT, and researchers interested in developing smart home applications using ESP32, Blynk Cloud, and wireless communication technologies. The implementation showcases the integration of hardware, software, and cloud services to build a reliable and efficient smart automation system.
# code used in this project
#define BLYNK_TEMPLATE_ID "TMPL3GVIkXrVg"
#define BLYNK_TEMPLATE_NAME "Smart Home Automation"
#define BLYNK_AUTH_TOKEN "qbw7eVsw66nlYY3spfo_12Fzs5El3mma"

#define BLYNK_PRINT Serial

#include <WiFi.h>
#include <WiFiClient.h>
#include <BlynkSimpleEsp32.h>

char ssid[] = "Wokwi-GUEST";
char pass[] = "";

int led1 = 2;
int led2 = 4;

BLYNK_WRITE(V0)
{
  int value = param.asInt();

  digitalWrite(led1, value);
}

BLYNK_WRITE(V1)
{
  int value = param.asInt();

  digitalWrite(led2, value);
}

void setup()
{
  Serial.begin(115200);

  pinMode(led1, OUTPUT);
  pinMode(led2, OUTPUT);

  Blynk.begin(BLYNK_AUTH_TOKEN, ssid, pass);
}

void loop()
{
  Blynk.run();
}
