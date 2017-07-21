//L293D
//Motor A
const int motorPin1  = 5;  // Pin 14 of L293
const int motorPin2  = 6;  // Pin 10 of L293
const int photoResistor = A0;
const int photoResistor2 = A1;
int pResistor;
int pResistor2;


//This will run only one time.
void setup(){
    Serial.begin(9600);
    //pinMode(motorPin1, OUTPUT);
    //pinMode(motorPin2, OUTPUT);
    pinMode(photoResistor, INPUT);
    pinMode(photoResistor2, INPUT);
   
}


void loop(){
   pResistor = analogRead(photoResistor);
   pResistor2 = analogRead(photoResistor2);
    if(abs(pResistor - pResistor2) <= 50) {
        digitalWrite(motorPin1, LOW);
        digitalWrite(motorPin2, LOW); 
     } else {
            if(pResistor > pResistor2) {
                digitalWrite(motorPin1, HIGH);
                digitalWrite(motorPin2, LOW);
            } else {
                if(pResistor2 > pResistor) {
                  digitalWrite(motorPin1, LOW);
                  digitalWrite(motorPin2, HIGH);
               }
           } 
        
        
     
   }
}

