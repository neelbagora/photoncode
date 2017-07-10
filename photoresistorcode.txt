
int photoresistor = A0; // Input pin from photoresistor

int power = A5; // Pin used to output power to photoresistor
int analogvalue; //Stores photoresistor reading



void setup() {
    Serial.begin(9600); //For serial monitor
    pinMode(A0,INPUT);  // A0 pin is input (from photoresistor)
    pinMode(power,OUTPUT); //Power pin used as output

    digitalWrite(power,HIGH); //outputs maximum possible voltage from power pin.

    
}

void loop() {

    analogvalue = analogRead(photoresistor); //assigns photoresistor reading to analogvalue
    Serial.println(analogvalue); //serial monitor printing
    delay(100); //delay 100 milliseconds

}
