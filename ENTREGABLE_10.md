# ENTREGABLE 10  
**Elaborado por: Grupo 8**

## INTEGRANTES:
- Alvaro Rodrigo Sucaticona Ambicho (Gestor de entregas y administración en GitHub)  
- Mara Del Aguila  
- Maria Liz Valdivia  
- Joe Leonardo Ponce Sarmiento  
- Ushiñahua Carreño Leonardo Gabriel  

---

## Índice

1. [Plan de usabilidad basado en evidencias](#plan-de-usabilidad-basado-en-evidencias)  
   1.1. [Contexto de uso](#contexto-de-uso)  
   1.2. [Perfil del usuario](#perfil-del-usuario)  
   1.3. [Análisis de tareas](#análisis-de-tareas)  
   1.4. [Criterio de éxito](#criterio-de-éxito)  
2. [Modelado 3D - Avance prototipado electrónico](#modelado-3d---avance-prototipado-electrónico)  
3. [Código Arduino](#código-arduino)
4. [Referencias](#referencias)  

---

## Plan de usabilidad basado en evidencias

### Contexto de uso:

**Usuarios principales:**  
Adolescentes con escoliosis idiopática (o congénita en algunos casos), en tratamiento con corsés ortopédicos personalizados, como el tipo TLSO o Boston, adaptados para cada paciente.

**Entorno de uso:**  
El dispositivo se usa en la vida diaria del paciente, principalmente en entornos como:

- **Hogar:** donde realizan actividades como dormir, sentarse, caminar o estudiar.  
- **Escuela:** los pacientes lo usan mientras asisten a clases, caminan por pasillos o permanecen sentados largos periodos.  
- **Entorno médico o clínico:** para revisiones periódicas, ajustes del corsé o monitoreo de tratamiento.

**Frecuencia de uso:**  
Uso prolongado diario (entre 12 y 23 horas al día), durante varios meses e incluso años, dependiendo del avance del tratamiento.

**Condiciones de uso:**  
Las actividades evaluadas incluyen sentarse, caminar, acostarse y realizar movimientos cotidianos.

El sistema debe ser capaz de medir presión en distintas posiciones, soportar movimiento y adaptarse al uso prolongado sin causar molestias.

Se observaron presión en zonas clave y la necesidad de calibración o regulación automática de la presión.

**Requisitos clave del contexto:**  
El sistema no debe interferir con las actividades normales del usuario.

Debe ser cómodo, seguro, duradero y discreto, especialmente en adolescentes, para evitar rechazo o abandono del tratamiento.

Idealmente debe integrarse de forma no invasiva al corsé y permitir monitoreo continuo de presión sin afectar la movilidad.

---

### Perfil del usuario:

**Características físicas:**  
Los usuarios son adolescentes en etapa de crecimiento (entre 10 y 17 años), con escoliosis idiopática u otras variantes. Utilizan corsés ortopédicos rígidos (como TLSO o Boston), que cubren gran parte del torso y en algunos casos el cuello.

Pueden experimentar incomodidad en zonas como el cuello, axilas, abdomen y espalda debido a la presión prolongada del corsé. La movilidad se ve limitada, especialmente para actividades como sentarse, inclinarse o acostarse.

**Capacidades cognitivas:**  
Tienen capacidad para comprender instrucciones básicas sobre el uso del dispositivo, pero requieren orientación inicial para la colocación del corsé y supervisión de parte de cuidadores o profesionales de salud. En algunos casos, se utilizaron encuestas para medir la satisfacción y percepción del uso.

**Factores emocionales:**  
Muchos pacientes reportan vergüenza, incomodidad social o frustración relacionada con el uso del corsé, sobre todo en contextos como la escuela o actividades públicas. La rigidez, el tamaño del corsé o la necesidad de ocultarlo bajo la ropa pueden generar una disminución en la autoestima o rechazo del tratamiento.

---

### Análisis de tareas:

**Tareas necesarias para el uso del dispositivo:**

- **Verificación del funcionamiento del sistema de sensores:** Comprobar que el sistema esté encendido y registre los datos correctamente. En algunos sistemas se requiere ver si hay conexión con un módulo de lectura o app ([2], [3]).  
- **Colocación del corsé correctamente sobre el cuerpo:** Debe ajustarse con firmeza en zonas específicas: abdomen y cuello, ya que es fundamental para asegurar que los sensores estén en contacto con las zonas clave de presión ([1], [2]).  
- **Uso del corsé durante actividades diarias:** Actividades como sentarse, caminar, acostarse y subir escaleras. Estas acciones ponen a prueba la estabilidad y comodidad del sistema, así como la precisión del registro de datos ([1], [3]).  
- **Carga del sistema (si es inalámbrico o a batería):** En dispositivos con autonomía de varios días o meses, puede ser necesario recargar o cambiar batería ocasionalmente.  
- **Revisión y transmisión de los datos al personal médico:** Ya sea mediante una aplicación, archivo exportado o visita clínica. Permite ajustar el tratamiento en base a la presión real aplicada durante el día ([2]).  

**Tareas críticas:**

- **Colocación correcta del corsé:** si se coloca mal, los sensores no registran bien la presión y se pierde efectividad terapéutica.  
- **Verificación del sistema:** si el sensor falla o se desconecta, no se registra información útil, afectando el seguimiento del tratamiento.

---

### Criterio de éxito:

| Criterio     | Pregunta                         | Respuesta                                                                                                                                                      |
|--------------|----------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Eficacia     | ¿La tarea se completó?           | Sí, si el sistema registra correctamente la presión en las zonas clave del corsé durante diferentes posturas y actividades cotidianas                          |
| Eficiencia   | ¿En cuánto tiempo?               | El corsé debe colocarse y activar los sensores en menos de 2 minutos. El sistema debe operar sin fallos durante al menos 12 horas continuas                    |
| Satisfacción | ¿Cómo lo evaluó el usuario?      | Se puede evaluar con una encuesta de usabilidad (SUS). Un puntaje mayor o igual a 70/100 indica una experiencia positiva .. También con entrevistas cualitativas. |
| Seguridad    | ¿Hubo errores o efectos negativos? | No deben presentarse lesiones, incomodidad prolongada ni fallos técnicos. Se espera “0 reportes de errores o molestias importantes” durante el uso continuo.   |

---
## Modelado 3D - Avance prototipado electrónico
![Texto alternativo](https://i.imgur.com/hY0vJO6.png)

---
## Código Arduino
#include <Wire.h>
#include <HX711.h>
#include "RTClib.h"
#include <BluetoothSerial.h>

HX711 scale;
RTC_DS3231 rtc;
BluetoothSerial SerialBT;

// Pines HX711
#define DT 4
#define SCK 5

const long umbral = 100;  // Umbral de presión, ajusta tras calibrar
unsigned long tiempoUso = 0;
unsigned long ultimoEnvio = 0;
String diaAnterior = "";

void setup() {
  Serial.begin(115200);
  SerialBT.begin("CORSE_BT");

  // RTC
  Wire.begin();
  if (!rtc.begin()) {
    Serial.println("RTC no encontrado");
    while (1);
  }
  if (rtc.lostPower()) {
    rtc.adjust(DateTime(F(__DATE__), F(__TIME__)));
  }

  // HX711
  scale.begin(DT, SCK);
  scale.set_scale();           // Ajustar si tienes el factor de calibración
  scale.tare();                // Pone a cero el sensor al inicio
}

void loop() {
  DateTime ahora = rtc.now();
  String dias[] = {"Domingo", "Lunes", "Martes", "Miércoles", "Jueves", "Viernes", "Sábado"};
  String diaActual = dias[ahora.dayOfTheWeek()];

  // Reiniciar contador si cambia el día
  if (diaActual != diaAnterior) {
    tiempoUso = 0;
    diaAnterior = diaActual;
  }

  long lectura = scale.get_units();

  if (lectura >= umbral) {
    tiempoUso++;
  }

  if (millis() - ultimoEnvio > 10000) {
    ultimoEnvio = millis();

    int horas = tiempoUso / 3600;
    int minutos = (tiempoUso % 3600) / 60;
    int segundos = tiempoUso % 60;

    char buffer[64];
    sprintf(buffer, "DIA=%s;TIEMPO=%02d:%02d:%02d", diaActual.c_str(), horas, minutos, segundos);
    SerialBT.println(buffer);
    Serial.println(buffer);
  }

  delay(1000);
}


## Referencias

[1] F. K. Fuss, A. Ahmad, A. M. Tan, R. Razman y Y. Weizman,  
“Pressure Sensor System for Customized Scoliosis Braces - PMC”, *PMC Home*, vol. 21, no. 4, p. 1153, 2021.  
[En línea]. Disponible en: [https://pmc.ncbi.nlm.nih.gov/articles/PMC7915694/](https://pmc.ncbi.nlm.nih.gov/articles/PMC7915694/)

[2] E. Chalmers, E. Lou, D. Hill, V. H. Zhao y M. S. Wong,  
“Development of a pressure control system for brace treatment of scoliosis - PubMed”, *PubMed*, vol. 20, no. 4, pp. 557–563, 2012.  
[En línea]. Disponible en: [https://pubmed.ncbi.nlm.nih.gov/22514207/](https://pubmed.ncbi.nlm.nih.gov/22514207/)

[3] E. Lou, D. L. Hill y J. V. Raso,  
“A wireless sensor network system to determine biomechanics of spinal braces during daily living - PubMed”, *PubMed*, vol. 20, no. 4, pp. 557–563, 2012.  
[En línea]. Disponible en: [https://pubmed.ncbi.nlm.nih.gov/20094808/](https://pubmed.ncbi.nlm.nih.gov/20094808/)

