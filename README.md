// First: pins (Digital) to 7segment (cathode)

int pin_a=1;

int pin_b=2;

int pin_c=3;

int pin_d=4;

int pin_e=5;

int pin_f=6;

int pin_g=7;

// secend: pins pins (digital) to de motor

int OUT Motor_1=8;

int OUT_Motor_2=9;

// third: pins (analog) to push button

int floor_0=A0;

int floor_1=A1;

int floor_2=A2;

// fou: pins (analog) to IR SENSOR

int sensor_0=A3;

int sensor_1=A4;

int sensor_2=A5;

int speed_ = 150;

void setup() {

pinMode (sensor_0, INPUT_PULLUP);

pinMode (sensor_1, INPUT_PULLUP);

pinMode (sensor_2, INPUT_PULLUP);

pinMode (floor_0, INPUT_PULLUP);

pinMode (floor_1, INPUT_PULLUP);

pinMode (floor_2, INPUT_PULLUP);

pinMode (OUT_Motor_1, OUTPUT);

pinMode (OUT_Motor_2,OUTPUT);

analogWrite (OUT_Motor_2, HIGH);

delay(500);

}

void loop() {

// first-floor:

if (digitalRead(floor_0) ==0){

if (digitalRead (sensor_0) ==1){

analogWrite (OUT_Motor_1, speed_);

while (digitalRead (sensor_0)){}

digitalWrite(OUT_Motor_1,0);

}

}

//third-floor:
if (digitalRead(floor_2) ==0){

if (digitalRead (sensor_2) ==1){

analogWrite (OUT_Motor_2, speed_);

while (digitalRead (sensor_2)){}

delay(400);

digitalWrite(OUT_Motor_2,0);

}

}

//sec-floor:

if (digitalRead(floor_1)==0){

if (digitalRead(sensor_1) ==1){

if (digitalRead (sensor_2) ==0) {

analogWrite(OUT_Motor_1, speed_);

while (digitalRead(sensor_1)){}

digitalWrite (OUT Motor 1,0);

}

else if (digitalRead(sensor_0)==0){

analogWrite(OUT_Motor_2, speed_);

while (digitalRead(sensor_1)){}

delay(400);

digitalWrite(OUT_Motor_2,0);

}

else {

digitalWrite(OUT_Motor_1,0);

digitalWrite (OUT_Motor_2,0);

}

}

}
//7-Segment:

if (digitalRead(sensor_0) ==0){

digitalWrite(pin_a,1);

digitalWrite(pin_b ,1);

digitalWrite(pin_c,1);

digitalWrite(pin_d,1);

digitalWrite(pin_e, 1);

digitalWrite(pin_f,1);

digitalWrite(pin_g,0);

if (digitalRead(sensor_1) == 0) {

digitalWrite(pin_a,0);

digitalWrite(pin_b,1);

digitalWrite(pin_c,1);

digitalWrite(pin_d,0);

digitalWrite(pin_e,0);

digitalWrite(pin_f,0);

digitalWrite(pin_g,0);
}
if (digitalRead(sensor_2) ==0){

digitalWrite(pin_a,1);

digitalWrite(pin_b,1);

digitalWrite(pin_c,0);

digitalWrite(pin_d,1);

digitalWrite(pin_e,1);

digitalWrite(pin_f,0);

}
}

digitalWrite(pin_g,1);

}
}
