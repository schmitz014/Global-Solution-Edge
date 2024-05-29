## Projeto em Ardunino: Radar de materias tóxicos

Este projeto demonstra como criar um sistema de mapeamento de ambiente usando um Arduino Uno, um servo motor e um sensor ultrassônico HC-SR04. O servo motor gira em um arco de 150 graus (15° a 165°), enquanto o sensor ultrassônico mede a distância dos objetos em cada posição angular. Os dados coletados são enviados para o computador via porta serial, onde podem ser processados e visualizados para criar um mapa do ambiente e assim localizar os poluentes dos mares.

**Componentes Necessários:**

* Arduino Uno
* Servo motor (SG90 ou similar)
* Sensor ultrassônico HC-SR04
* Protoboard
* Jumpers

**Montagem do Circuito (Conforme a Imagem):**

1. **Servo Motor:**
   * Fio vermelho: Conectar ao pino 5V do Arduino.
   * Fio marrom ou preto: Conectar ao pino GND do Arduino.
   * Fio laranja ou amarelo: Conectar ao pino digital do Arduino.

2. **Sensor Ultrassônico:**
   * VCC: Conectar ao pino 5V do Arduino.
   * GND: Conectar ao pino GND do Arduino.
   * TRIG: Conectar ao pino digital do Arduino.
   * ECHO: Conectar ao pino digital do Arduino.

**Funcionamento do Código:**

1. **Inclusão de Bibliotecas:**
   * `#include <Servo.h>`: Inclui a biblioteca necessária para controlar o servo motor.

2. **Definição de Pinos:**
   * `trigPin` e `echoPin`: Definem os pinos digitais conectados aos pinos TRIG e ECHO do sensor ultrassônico.

3. **Variáveis:**
   * `duration`: Armazena a duração do pulso recebido pelo pino ECHO do sensor ultrassônico.
   * `distance`: Armazena a distância calculada a partir da duração do pulso.

4. **Configuração (`setup()`):**
   * `pinMode()`: Configura os pinos TRIG e ECHO como saída e entrada, respectivamente.
   * `Serial.begin(9600)`: Inicializa a comunicação serial com uma taxa de 9600 bauds.
   * `myServo.attach(12)`: Associa o objeto `myServo` ao pino digital 12, onde o servo motor está conectado.

5. **Loop Principal (`loop()`):**
   * Dois loops `for`: Controlam o movimento do servo motor em um arco de 15° a 165° e de volta.
   * `myServo.write(i)`: Define a posição angular do servo motor para o valor de `i`.
   * `delay(30)`: Introduz um atraso de 30 milissegundos entre cada movimento do servo motor.
   * `calculateDistance()`: Chama a função para calcular a distância medida pelo sensor ultrassônico.
   * `Serial.print()`: Envia os dados (ângulo e distância) para a porta serial, separados por vírgulas e pontos para facilitar a leitura no computador.

6. **Cálculo da Distância (`calculateDistance()`):**
   * Envia um pulso de 10 microssegundos no pino TRIG para iniciar a medição.
   * Mede a duração do pulso recebido no pino ECHO.
   * Calcula a distância usando a fórmula: `distance = duration * 0.034 / 2`.

**Visualização dos Dados:**

Utilize um software como o Arduino IDE Serial Monitor, Processing ou Python para receber e visualizar os dados enviados pelo Arduino. Você pode criar um gráfico em tempo real que mostre a distância em função do ângulo, gerando um mapa do ambiente.

**Observações:**

* Certifique-se de que a alimentação do servo motor seja adequada. Se necessário, utilize uma fonte de alimentação externa.
* Ajuste a velocidade de rotação do servo motor alterando o valor do `delay` dentro dos loops `for`.
* Explore diferentes formas de visualizar os dados, como gráficos polares ou mapas 2D.
* Este é um projeto básico. Você pode adicionar recursos como detecção de obstáculos, controle remoto, etc.

**Tecnologias Utilizadas:**
* C++

**Membros da Equipe:**
* Pedro Schmitz
* Rafael Porto

