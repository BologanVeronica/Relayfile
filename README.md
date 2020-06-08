# Relayfile
Dreamteamproject 
#define R_PIN 13
#define FS_PIN A0
#define PIR_PIN 12
void setup()
{
  Serial.begin(9600);
  InitPIR();
  InitFS();
  InitRelay(); 
}
void Afisare (){
 int val1 = digitalRead(PIR_PIN);
 Serial.println(val1);
  if(val1 > 0){
    Serial.println("Miscare detectata");}
   else {
     Serial.println("Nu este miscare");}}
void loop()
{
 Afisare();
 int val = analogRead(FS_PIN);
 Serial.println(val);
 if ((val <30) && (digitalRead(PIR_PIN) == HIGH))
 {
    RelayON();
    Serial.println("Lumineaza!");
    Serial.println();
    delay(1000);
 }
  else {
    RelayOFF();
    Serial.println("S-a deconectat becul");
    Serial.println();
    delay(1000);    
  }
}
  
void InitPIR()
{
  pinMode(PIR_PIN, INPUT);
}
void InitFS()
{
pinMode(FS_PIN, INPUT);
}
void InitRelay()
{
pinMode(R_PIN, OUTPUT);
}
void RelayON()
{
  digitalWrite(R_PIN, HIGH);
}
void RelayOFF()
{
  digitalWrite(R_PIN, LOW);
}
