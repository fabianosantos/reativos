Projeto Mini-Arduino
------------------------------------------------------------------------------
Integrantes: Raphael Barros, Tulio Loureiro, Fabiano Santos

Componentes utilizados:

- Placa Arduino
- Protoboard
- Sensor Ultrassonico HC - SR04 
- Display de LCD 16x2
- LED
- Resistor
- Jumpers para as ligações


------------------------------------------------------------------------------
- Descrição do Projeto:

 O projeto consiste em acender um LED quando o sensor Ultrassônico captar a existência de um objeto a uma distância igual ou menor a 5cm dele. Além disso, um Display LCD 16x2 ficará responsável por mostrar a distância que o objeto se encontra do sensor. Quando a distância for menor ou igual a 5cm,mostrará também o tempo em que o LED está aceso.
 Quando o tempo em que o LED está aceso for igual a 10 segundos, o LED se apagará e o tempo indicado no Display será "zerado".
 O sistema então volta a executar, quando o objeto for afastado em mais de 5cm do sensor e assim, reaproximado.
 
 - Informações extras sobre o funcionamento do Sensor Ultrassônico:
 
 O funcionamento do Sensor Ultrassônico HC-SR04 se baseia no envio de sinais ultrassônicos pelo sensor, que aguarda o retorno (echo) do sinal, e com base no tempo entre envio e retorno, calcula a distância entre o sensor e o objeto detectado.
 Para determinar a distância entre o sensor e o objeto, utiliza-se a equação Distância = (Tempo echo em nível alto * velocidade do som) /2
 
 
 Link do vídeo disponibilizado no YouTube : https://youtu.be/Aj_9ZsvvqEg
