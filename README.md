# Global Solution 

## Descrição do Projeto:
O projeto visa desenvolver um sistema inovador que emprega tecnologia Arduino para monitorar de perto e otimizar as condições ambientais cruciais para a decomposição eficaz de resíduos plásticos no oceano.Este sistema é projetado para operar em colaboração com duas espécies específicas de bactérias, proporcionando um ambiente ideal para sua atividade de degradação.

## Integrantes do grupo
- Eduardo Tomazela Rm: 556807 
- Léo Masago Rm: 557768 
- Luiz Henrique Rm: 555235 

## Componentes Utilizados:
- 1 Arduino Uno R3
- 1 Placa de Ensaio
- 1 potenciometro
- 2 Resistores 220 Ω
- 1 LCD 16x2
- 1 LDR
- 1 TMP36

## Link do vídeo 
https://www.youtube.com/watch?v=G5Wt3TPFdOM

## Link da simulação no Tinkercad
https://www.tinkercad.com/things/3zhfUSji9RV-copy-of-sensor-ph-?sharecode=jrkLPmMkrt9JHbogopFFagP6G5CExiAZlJUAdUSilac

## Código do Projeto:

#include<LiquidCrystal.h>
const int rs =13,en = 12,d4 =11,d5 =10,d6 =9,d7 =8;
LiquidCrystal lcd(rs,en, d4,d5,d6,d7);
int Contrast = 0;
int ldr = A1;
int medidorph = A0;
int valorldr = 0;
int sensorValue = 0;
int temp = A2;


void setup()
{
  Serial.begin(9600);
  analogWrite (6,Contrast);
  lcd.begin(16,2);
  pinMode(ldr, INPUT);
  pinMode(medidorph, INPUT);
  pinMode(temp, INPUT);
}

void loop()
{
 int count;
 for(count=9; count>-1; count--){
   lcd.setCursor(0,0);
   lcd.print("Tempo: ");
   lcd.setCursor(6,0);
   lcd.print(count);
 
   delay(1000);
   int sensorValue = analogRead(medidorph);
   float ph = sensorValue * (14.0/1023.0);
   lcd.setCursor(0,1);
   lcd.print("PH: ");
   lcd.setCursor(4,1);
   lcd.print(ph);
  }
 lcd.clear();
  
 int valorldr = analogRead(ldr);
 lcd.setCursor(0,0);
 lcd.print("Luminosidade:");
 lcd.setCursor(13,0);
 lcd.print(valorldr);
 delay(4000);
 
 lcd.clear();
  
 int tmp = analogRead(temp);
 float voltage = (tmp * 5.0)/1024;
 float milliVolt = voltage * 1000;
 float tmpCel =  (milliVolt-500)/10;
 lcd.setCursor(0,0);
 lcd.print("Temperatura em C");
 lcd.setCursor(0,1);
 lcd.print(tmpCel);
 delay(5000);
 
 //||or && and
 
  
 lcd.clear();
  
 int sensorValue = analogRead(medidorph);
 float ph = sensorValue * (14.0/1023.0);  
  
  if(ph > 6.5 && ph < 7.5 ){
    lcd.setCursor(0,0);
    lcd.print("PH OK!");
    delay(4000);
    lcd.clear();
  }
  else if(ph < 6.5){
    lcd.setCursor(0,0);
    lcd.print("PH muito acido!");
    delay(4000);  
    lcd.clear();
  }
  else{
    lcd.setCursor(0,0);
    lcd.print("PH muito basico");
    delay(4000);
    lcd.clear();
  }
  
  if(tmpCel >= 34 && tmpCel <= 37){
    lcd.setCursor(0,0);
    lcd.print("Temperatura OK!");
    lcd.clear();
  }
  else if(tmpCel<34){
    lcd.setCursor(0,0);
    lcd.print("Temp baixa!");
    delay(4000);
    lcd.clear();
  }
  else {
    lcd.setCursor(0,0);
    lcd.print("Temp acima!");
    delay(4000);
    lcd.clear();
  }
  
  if(valorldr >= 100 && valorldr <= 200){
    lcd.setCursor(0,0);
    lcd.print("Luz OK!");
    delay(4000);
    lcd.clear();
  }
  else if(valorldr < 100){
    lcd.setCursor(0,0);
    lcd.print("Luz abaixo!");
    delay(4000);
    lcd.clear();
  }
  else{
    lcd.setCursor(0,0);
    lcd.print("Luz acima");
    delay(4000);
    lcd.clear();
  }
 
  
 
  
 
 
}


<h1>
  :dark_sunglasses: Integrantes:
</h1>

| [<img loading="lazy" src="https://avatars.githubusercontent.com/u/161898042?v=4" width=115><br><sub>Eduardo Tomazela</sub>](https://github.com/du-ntomazela) |  [<img loading="lazy" src="https://avatars.githubusercontent.com/u/101646035?v=4" width=115><br><sub>Léo Massago</sub>](https://github.com/LeoMasago) |  [<img loading="lazy" src="https://avatars.githubusercontent.com/u/162758896?v=4" width=115><br><sub>Luiz Henrique</sub>](https://github.com/LhenriqueTech) |
| :---: | :---: | :---: | 
