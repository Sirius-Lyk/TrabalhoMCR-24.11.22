# TrabalhoMCR-24.11.22
Trabalho de MCR - Simulação de carrinho controlado via MQTT
O trabalho envolve o desenvolvimento e simulação através do site (Wokwi.com) de um carrinho controlado por três botões: Frente, Ré e Pare.
Conta com um esp32; 2 LEDs Verdes que indicam as rodas frontais; 2 LEDs Vermelhos que indicam as rodas traseiras; Um sensor de distância ultrassônico e um display OLED para acompanhamento do estado de movimento e freio.
![Sem Título-1](https://user-images.githubusercontent.com/118866041/203677512-6290ccb3-3b87-401e-8236-0be8c6cfe86d.png)

O IoT Contém um sensor de distância ultrassônico no qual evita a covisão frontal caso o carrinho esteje a menos de 9cm de distância de uma superfície. O sensor poder ser trocado e adaptado para um sensor de leitura analógica com apenas algumas alterações no código. 

line 10 [ int sensor = digitalRead(PinSensor) ]; 

line 219  [ if (millis() <= tempo+100) {
              sensor *=3;
              cm = (sensor / 100);
              if (cm <= 9){
              client.publish("MVP-Pare", "on");
            }
            else {
            }
          ];
          
line 194  [ while(cm <= 8){
              sensor *=3;
              cm = (sensor / 100);
              digitalWrite(LEDFrenteD, LOW);
              digitalWrite(LEDFrenteE, LOW);
              digitalWrite(LEDReD, HIGH);
              digitalWrite(LEDReE, HIGH);
            }
          ];
          
O display Oled foi utilizado com o objetivo de mostrar o estado das rodas e do "freio", sendo atualizado ao fazer alteração em seus estados.


**Imagem para consulta de pinos**

![image](https://user-images.githubusercontent.com/118866041/203679887-2f3344d2-9bec-498f-99ff-c26cb0519ef2.png)
