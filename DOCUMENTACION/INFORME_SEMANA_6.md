## Informe semana 6
## Integrantes

- Alvaro Rodrigo Sucaticona Ambicho (Gestor de entregas y administración en GitHub)  
- Mara Del Aguila  
- Maria Liz Valdivia  
- Joe Leonardo Ponce Sarmiento  

Motor dirección básica:
Este ejemplo permite alternar el sentido de giro de un motorreductor DC GA12-N20 mediante un módulo controlador de motores L298N, sin controlar la velocidad. El sistema ejecuta un cambio de dirección cada 5 segundos, lo cual permite simular mecanismos biomédicos que requieren inversión de movimiento como válvulas alternantes o dispositivos de tracción reversibles.
Este ejercicio no fue complicado de hacer y se hizo rápido.

![Motor dirección básica](https://i.postimg.cc/yNxBPw5N/Picture1.png)

Motor dirección velocidad:
Este ejemplo permite controlar tanto el sentido de giro como la velocidad de un motorreductor DC GA12-N20 utilizando un Arduino UNO y un módulo L298N. Se emplea una señal PWM (modulación por ancho de pulso) para ajustar la velocidad del motor, y se alterna el sentido de rotación cada 5 segundos. Esta estrategia puede aplicarse a sistemas biomédicos de bombeo, movilidad o rehabilitación mecánica.
Este ejercicio se le complicó debido que el motor tenia un pin bloqueado que alteraba la conexión.

![Motor dirección velocidad](https://i.postimg.cc/CxFwZZsk/Picture2.png)

Motor velocidad potenciómetro:
Este ejemplo muestra cómo activar un micromotor de vibración (tipo coin cell) utilizando un Arduino UNO y un transistor NPN como interruptor. Se trata de una implementación básica de retroalimentación háptica, común en dispositivos biomédicos como alarmas silenciosas o señales táctiles en interfaces hombre-máquina.
En este ejercicios utilizó la misma estructura de conexión que el anterior solo agregando el potenciómetro por lo cual no se les hizo difícil de desarrollar.

![Motor velocidad potenciómetro](https://i.postimg.cc/Kv7Zv7Bm/Picture3.png)

Motor vibración básico:
Este ejemplo muestra cómo activar un micromotor de vibración (tipo coin cell) utilizando un Arduino UNO y un transistor NPN como interruptor. Se trata de una implementación básica de retroalimentación háptica, común en dispositivos biomédicos como alarmas silenciosas o señales táctiles en interfaces hombre-máquina.   
En este ejercicio no nos tomó mucho tiempo desarrollarlo pero arrastramos un error de posición del motor vibrador en el protoboard.

![Motor vibración básico](https://i.postimg.cc/W1XT025K/Picture4.png)

Motor vibrador potenciómetro: 
Este ejemplo permite controlar la intensidad de vibración de un micromotor tipo coin cell utilizando un potenciómetro como entrada de usuario. La señal analógica se convierte en una señal PWM que regula la energía entregada al motor a través de un transistor. El sistema permite simular un control háptico proporcional, ideal para interfaces biomédicas de retroalimentación sensorial.
Como arrastramos el error del ejercicio anterior, nuestras conexiones con el motor hacen que nuestro potenciómetro no afectaba la velocidad del motor pero al final si lo llegamos a solucionar.

![Motor vibrador potenciómetro](https://i.postimg.cc/pXMWHc90/Picture5.png)

Feedback Háptico con FSR y Motor Vibrador:
Simular un sistema de feedback háptico continuo, donde el usuario recibe una señal táctil proporcional al nivel de presión ejercida, útil en aplicaciones de rehabilitación, entrenamiento sensorial o interfaces humano-máquina. Se nos complicó con la medida de fuerza para detectar la presión pero lo arreglamos en la programación. 

![Feedback Háptico con FSR y Motor Vibrador](https://i.postimg.cc/05wkh1NM/Picture6.jpg)
