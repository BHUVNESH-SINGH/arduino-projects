int redPin=11;
int bluePin=6;
int greenPin=10;
int S2=7;
int S3=8;
int outPin=4;
unsigned int pulseWidth;
int rColorStrenght;
int bColorStrenght;
int gColorStrenght;
void setup() {
// put your setup code here, to run once:
Serial.begin(9600);
pinMode(redPin, OUTPUT);
pinMode(bluePin, OUTPUT);
pinMode(greenPin, OUTPUT);
pinMode(S2, OUTPUT);
pinMode(S3, OUTPUT);
pinMode(outPin, INPUT);
}void loop() {
// put your main code here, to run repeatedly:
digitalWrite(S2, LOW);
digitalWrite(S3, LOW);
pulseWidth = pulseIn(outPin, LOW);
rColorStrenght = (pulseWidth/400)-1;
rColorStrenght = (255- rColorStrenght);
digitalWrite(S2, HIGH);
digitalWrite(S3, HIGH);
pulseWidth = pulseIn(outPin, LOW);
gColorStrenght = (pulseWidth/400)-1;
gColorStrenght = (255- gColorStrenght);
digitalWrite(S2, LOW);
digitalWrite(S3, HIGH);
pulseWidth = pulseIn(outPin, LOW);
bColorStrenght = (pulseWidth/400)-1;
bColorStrenght = (255- bColorStrenght);
if(rColorStrenght > gColorStrenght && gColorStrenght > bColorStrenght) {
rColorStrenght= 255;
gColorStrenght= gColorStrenght/2;
bColorStrenght= 0;
}
if(rColorStrenght > bColorStrenght && bColorStrenght > gColorStrenght) {
rColorStrenght= 255;
bColorStrenght= bColorStrenght/2;
gColorStrenght= 0;
}
if(gColorStrenght > rColorStrenght && rColorStrenght > bColorStrenght) {
gColorStrenght= 255;
rColorStrenght= rColorStrenght/2;
bColorStrenght= 0;}
if(gColorStrenght > bColorStrenght && bColorStrenght > rColorStrenght) {
gColorStrenght= 255;
bColorStrenght= bColorStrenght/2;
rColorStrenght= 0;
}
if(bColorStrenght> rColorStrenght && rColorStrenght > gColorStrenght) {
bColorStrenght= 255;
rColorStrenght= rColorStrenght/2;
gColorStrenght= 0;
}
if(bColorStrenght > gColorStrenght && gColorStrenght > rColorStrenght) {
bColorStrenght= 255;
gColorStrenght= gColorStrenght/2;
rColorStrenght= 0;
}
analogWrite(redPin, rColorStrenght);
analogWrite(bluePin, bColorStrenght);
analogWrite(greenPin, gColorStrenght);
Serial.print(rColorStrenght);
Serial.print(“,”);
Serial.print(bColorStrenght);
Serial.print(“,”);
Serial.print(gColorStrenght);
Serial.print(“,”);
delay(500);
}
