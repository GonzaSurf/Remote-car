//Remote-car
//Remote car with bluetooth comunication and the mian is arduino

#define motor_1L1 = 2;
#define motor_1L2 = 3;
#define motor_1R1 = 4;
#define motor_1R2 = 5;
#define motor_2L1 = 6;
#define motor_2L2 = 7;
#define motor_2R1 = 8;
#define motor_2R2 = 9;
#define led_izq = 10;
#define led_der = 11;

void setup() {
  Serial.begin(9600);
  pinMode(motor_1L1, OUTPUT);
  pinMode(motor_1L2, OUTPUT);
  pinMode(motor_1R1, OUTPUT);
  pinMode(motor_1R2, OUTPUT);
  pinMode(motor_2L1, OUTPUT);
  pinMode(motor_2L2, OUTPUT);
  pinMode(motor_2R1, OUTPUT);
  pinMode(motor_2R2, OUTPUT);
  pinMode(led_izq, OUTPUT);
  pinMode(led_der, OUTPUT);
}

void loop() {
  if (Serial.available() >  0){
    int valor = 0;
    switch (valor){
      case 1:
        Fordward();
        break;
       case 2:
        Backward();
        break;
       case 3:
        move_Left();
        break;
       case 4:
        move_Right();
        break;
    }
  }
}

void Fordward(){
  digitalWrite(motor_1L1, HIGH); 
  digitalWrite(motor_1L2, LOW);
  digitalWrite(motor_1R1, HIGH);
  digitalWrite(motor_1R2, LOW);
  digitalWrite(motor_2L1, HIGH);
  digitalWrite(motor_2L2, LOW);
  digitalWrite(motor_2R1, HIGH);
  digitalWrite(motor_2R2, LOW);
  Serial.print("Avanando...");
}

void Backward(){
  digitalWrite(motor_1L1, LOW);
  digitalWrite(motor_1L2, HIGH);
  digitalWrite(motor_1R1, LOW);
  digitalWrite(motor_1R2, HIGH);
  digitalWrite(motor_2L1, LOW);
  digitalWrite(motor_2L2, HIGH);
  digitalWrite(motor_2R1, LOW);
  digitalWrite(motor_2R2, HIGH);
  digitalWrite(led_izq, HIGH);
  Serial.print("Retrocediendo...");
}

void move_Left(){
  digitalWrite(motor_1L1, HIGH);
  digitalWrite(motor_1L2, LOW);
  digitalWrite(motor_1R1, LOW);
  digitalWrite(motor_1R2, HIGH);
  digitalWrite(motor_2L1, HIGH);
  digitalWrite(motor_2L2, LOW);
  digitalWrite(motor_2R1, LOW);
  digitalWrite(motor_2R2, HIGH);
  Serial.print("Girando a la izquierda...");
}

void move_Right(){
  digitalWrite(motor_1L1, LOW);
  digitalWrite(motor_1L2, HIGH);
  digitalWrite(motor_1R1, HIGH);
  digitalWrite(motor_1R2, LOW);
  digitalWrite(motor_2L1, LOW);
  digitalWrite(motor_2L2, HIGH);
  digitalWrite(motor_2R1, HIGH);
  digitalWrite(motor_2R2, LOW);
  digitalWrite(led_der, HIGH);
  Serial.print("Girando a la derecha...");
}
