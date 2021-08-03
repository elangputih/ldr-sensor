#include <ESP8266HTTPClient.h>
#include <ESP8266WiFi.h>

//seting jaringan
const char* ssid = "LAB HARDWARE 1";
const char * password = "prodikom123";
const char * host = "192.168.23.150" ;//alamat ip server

//variable indikator koneksi
#define PIN_LED 5 

void setup() {
  Serial.begin(9600);
  pinMode (PIN_LED, OUTPUT);

  //seting wifi
  WiFi.hostname ("NodeMCU");
  WiFi.begin(ssid, password);

  //cek konkesi wifi
  while (WiFi.status() != WL_CONNECTED)
  {
    //led mati
    digitalWrite (PIN_LED, LOW);
    //mencoba koneksi terus
    Serial.print("?");
    delay(500);
  }
  //apabila terkoneksi
  digitalWrite(PIN_LED,HIGH);
  //menampilkan pesan di serial wifi connected
  Serial.println("WiFi Connected");
  
  }
  

void loop() {
  int sensor = analogRead(0);
  Serial.println(sensor);
  
  //cek koneksi ke server
  WiFiClient client ;
  if (! client.connect (host, 80))
  {
    Serial.println ("connection Failed");
    return;
  }
  //proses pengiriman data
  String Link ;
  HTTPClient http;
  Link = "http://192.168.23.40/ldrsensor/kirimdata.php?sensor=" +String(sensor);
  //eksekusi link
  http.begin(Link);
  //mode yg di gunakan adalah get
  http.GET();
  http.end();
  delay (1000);
}
