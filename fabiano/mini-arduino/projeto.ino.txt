// biblioteca para o display LCD
#include <LiquidCrystal.h>
# define LED_PIN 10

// variáveis
int gatilho = 8; // pino TRIG do sensor ultrassônico
int echo = 9; // pino ECHO do sensor ultrassônico
float tempo; // para armazenar o tempo de ida e volta do sinal em microsegundos
float distancia_cm; // para armazenar a distância em centímetros
float start = 0;
float tempo_ligado = 0 ;
boolean on = false;
 
// inicialização do display LCD
LiquidCrystal lcd(12, 11, 5, 4, 3, 2);
 
void setup() {
 // configura pino GATILHO como saída
 pinMode(gatilho,OUTPUT);

 // deixa pino em LOW
 digitalWrite(gatilho,LOW);

 delayMicroseconds(10);
 
 // configura pino ECHO como entrada
 pinMode(echo,INPUT);

 pinMode(LED_PIN,OUTPUT);
 digitalWrite(LED_PIN,LOW);
}
 
void loop() {
   // disparar pulso ultrassônico
   digitalWrite(gatilho, HIGH);

   delayMicroseconds(10);
   digitalWrite(gatilho, LOW);
   
   // medir tempo de ida e volta do pulso ultrassônico
   tempo = pulseIn(echo, HIGH);
   
   // calcular as distâncias em centímetros
   float distancia_cm = tempo / 29.4 / 2;
   
   lcd.begin(16, 2);
   lcd.setCursor(0,0);
   lcd.print("Distancia: ");
   lcd.print(distancia_cm);
   lcd.print(" cm");
   if(distancia_cm <= 5){
    if(start == 0) {
      start = millis(); 
    }
    on=true;
   }else{
      start = 0;
      on=false;
   }
    
   if(on){
       tempo_ligado = (millis() - start)/1000;  
   }else{
      tempo_ligado = 0;
   }
   lcd.setCursor(0,1);
   lcd.print("Tempo lig:");

   if(tempo_ligado>10){
      digitalWrite(LED_PIN,LOW);
      lcd.print("0.00");
    } else if(on) {
      digitalWrite(LED_PIN,HIGH);
      lcd.print(tempo_ligado);
    } else {
      digitalWrite(LED_PIN,LOW);
      lcd.print("0.00");
    }
    
   delay(1000);
   delayMicroseconds(200);
}
