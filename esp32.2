 
//#include <Arduino_ESP32_OTA.h>
#define BLYNK_TEMPLATE_ID "TMPL6wgFCcwXK"  // khai báo kết nối với web sever
#define BLYNK_TEMPLATE_NAME "BATTAT" // khai báo kết nối với web sever
#define BLYNK_AUTH_TOKEN "7nhKOGaEnAqPugstwJnf01e2MtQBs2xT"// khai báo kết nối với web sever
#define BLYNK_PRINT Serial // khai báo kết nối với web sever
#define CB_UV 33 // khai báo chân 34 sẽ là chân cảm biến UV

#include <WiFi.h>
#include <WiFiClient.h>
#include <BlynkSimpleEsp32.h>
#include <Wire.h>
#include <SHT3x.h>
#define BLYNK_PRINT Serial

char auth[] = BLYNK_AUTH_TOKEN;
char ssid[] = "C0_UTEHY";
char pass[] = "hoang12345";

SimpleTimer timer;
////////mua
#define INTERVAL 20                         

const byte rainPin = 17;

unsigned int raincnt = 0;
unsigned long lastSend;
// khai báo đọc cảm biến nhiệt độ + độ ẩm
SHT3x Sensor;
/////tia UV
int UVOUT = 32; 
int REF_3V3 = 33; 
///huong gio 
WidgetLCD hienthi(V2);

void setup()
{
 Serial.begin(9600);
 Blynk.begin(auth, ssid, pass);
 timer.setInterval(2000, tocdogio);
 pinMode(UVOUT, INPUT);
 pinMode(REF_3V3, INPUT);
 pinMode(rainPin, INPUT_PULLUP);
 attachInterrupt(digitalPinToInterrupt(rainPin), cntRain, RISING);
 delay(10);
 lastSend = millis() - INTERVAL*100;

}
int averageAnalogRead(int pinToRead)
{
 byte numberOfReadings = 8;
 unsigned int runningValue = 0; 

 for(int x = 0 ; x < numberOfReadings ; x++)
 runningValue += analogRead(pinToRead);
 runningValue /= numberOfReadings;

 return(runningValue);
}

void loop()
{
 Blynk.run();
 timer.run();

 doctiaUV();
 tocdogio();
 huonggio();
 donhietdodoam();

 if ( millis() - lastSend > INTERVAL*1000 ) { 
  luongmua();  
 }
}

void huonggio()
{

int sensorValue = analogRead(35);
 float voltage1 = sensorValue*33/4095.0;
 float voltage= voltage1/10;
 int direction = map(sensorValue, 0, 1023, 0, 360);
 delay(500); 
 if(voltage >= 0&&voltage<=0.14)
 { 
  Serial.println("Hướng Bắc");
  delay(200);
  hienthi.print(0,0,"Hướng Bắc    ");

  }
  
else if(voltage >=0.15&&voltage<=0.52)
 {
  Serial.println("Hướng Đông Bắc");
  delay(200);
  hienthi.print(0,0,"Hướng Đông Bắc   ");
  }

  else if(voltage >=0.53&&voltage<=0.97)
 {
  Serial.println("Hướng Gió Đông");
  delay(200);
  hienthi.print(0,0,"Hướng Đông   ");

  } 

   else if(voltage >=0.98 &&voltage<=1.42)
 {
  Serial.println("Hướng Gió Đông Nam");
  delay(200);
  hienthi.print(0,0,"Hướng Đông Nam  ");
  }
  
 else if(
 voltage >=1.43 &&voltage<=1.88)
 {
  Serial.println("Hướng Gió Nam");
  delay(200);
  hienthi.print(0,0,"Hướng Nam   ");
 }
 
 else if(voltage >=1.89 &&voltage<=2.34)
 {
  Serial.println("Hướng Gió Tây Nam");
  delay(200);
  hienthi.print(0,0,"Hướng Tây Nam   ");

  }
  
   else if(voltage >=2.35 &&voltage<=2.85)
 {
  Serial.println("Hướng Gió Tây");
  delay(200);
   hienthi.print(0,0,"Hướng Tây   ");
  }
  
 else if (voltage >=2.86 &&voltage<=3.3)
  {
  Serial.println("Hướng Gió Tây Bắc");
  delay(200);
  hienthi.print(0,0,"Hướng Tây Bắc  ");

  }
 
}
 

void tocdogio()
{

 int sensorValue = analogRead(34);
 float outvoltage = sensorValue * (3.3 / 1023.0);
 int Level = 6 * outvoltage;
 Serial.print("Toc do gio ");
 Serial.print(Level);
 Serial.println();
 delay(200);
 Blynk.virtualWrite(V5, Level);

  }



void doctiaUV()
{
int uvLevel = averageAnalogRead(UVOUT);
 int refLevel = averageAnalogRead(REF_3V3);
 float dienappp = 3.3 / refLevel * uvLevel;
 float uvIntensity = mapfloat(dienappp , 0.99, 2.8, 0.0, 15.0); //Convert the voltage to a UV intensity level

 Serial.print(" / UV Intensity (mW/cm^2): ");
 Serial.print(uvIntensity);
 Serial.println(); 
 delay(200);
Blynk.virtualWrite(V1,uvIntensity);
}

void donhietdodoam()
{
 // chương trình đọc cảm biến nhiệt độ + độ ẩm
 Serial.println("Do am Nhiet do");
 Sensor.UpdateData();

 // Serial.print("Temperature: ");
 //Serial.println(Sensor.GetTemperature());
  float nhietdo = Sensor.GetTemperature();
 Serial.print(nhietdo);
 // Serial.write("\xC2\xB0");
 Serial.println("C");

 //Serial.print("Humidity: ");
 //Serial.print(Sensor.GetRelHumidity());
 float doam = Sensor.GetRelHumidity();
 Serial.print(doam);
 Serial.println("%");
 Blynk.virtualWrite(V3, nhietdo);
 Blynk.virtualWrite(V4, doam);

}
void luongmua()
{

 float r = (raincnt/2)*0.2794;
 raincnt = 0;

 Serial.print(" ");
 Serial.print("Rain: ");
 Serial.print(r);
 Serial.print(" mm ");
 
 lastSend = millis();
  Blynk.virtualWrite(V6,r);
}

void cntRain() {
 raincnt++;
}

float mapfloat(float x, float in_min, float in_max, float out_min, float out_max)
{
 return (x - in_min) * (out_max - out_min) / (in_max - in_min) + out_min;
}
