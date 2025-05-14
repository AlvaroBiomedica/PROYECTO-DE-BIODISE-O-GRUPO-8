# Entregable 7 – Proyecto PressCorset

## INTEGRANTES
- Alvaro Rodrigo Sucaticona Ambicho (Gestor de entregas y administración en GitHub)  
- Mara Del Aguila  
- Maria Liz Valdivia  
- Joe Leonardo Ponce Sarmiento  

---

## Índice

1. Caja negra  
2. Lista de Entrada y Salidas
3. Esquema de funciones  
4. Matriz morfológica  
5. Tabla de valoración  
6. Conclusión del caso de estudio elegido (CS1)  
7. Boceto  

---

## 1. Caja negra
![caja](https://i.imgur.com/RA4S2D3.jpeg)


---

## 3. Esquema de funciones


![esquema](https://i.imgur.com/kOhZlzG.jpeg)

### Función principal
Monitorear el uso correcto del corsé ortopédico mediante sensores, evaluando su uso diario y transmitiendo información útil para el seguimiento médico.

### Funciones secundarias:

- Recolectar: Presión ejercida sobre el corsé, estado del corsé (puesto o no puesto) y Nivel de energía del sistema. Es necesaria como información de entrada para empezar con el funcionamiento correcto del sistema.
- Medir: Una vez recolectados los datos, el sistema los transforma en información útil a través de sensores integrados. Se mide específicamente la presión corporal sobre el corsé mediante sensores de presión distribuidos en puntos clave. A partir de estas lecturas, el sistema determina si el corsé está siendo utilizado correctamente o no. Además, se lleva a cabo una lectura constante del nivel de batería del sistema, lo que permite asegurar el funcionamiento continuo del dispositivo sin interrupciones.
- Almacenar: Se guardan registros locales de las lecturas de presión y del tiempo de uso acumulado, además de asociar esta información con un identificador único del paciente o del dispositivo. Asimismo, se almacena el estado del sistema, incluyendo el nivel de energía y la conectividad, con el objetivo de llevar un control básico de mantenimiento y funcionamiento.
- Procesar: Se calcula el total de horas de uso diario y semanal del corsé, un indicador fundamental para evaluar el cumplimiento del tratamiento. Además, se identifican patrones de adherencia, lo que permite conocer si el paciente está usando el corsé de forma constante, irregular o insuficiente. Esta función es clave para la toma de decisiones clínicas posteriores.
- Notificar y visualizar: Finalmente, el sistema emite notificaciones y presenta la información de forma clara y útil. En caso de batería baja o desconexión de red, se generan alertas para el usuario o el equipo médico. Paralelamente, se transmiten los datos procesados a una base de datos remota, donde pueden visualizarse en reportes con gráficos y estadísticas. Esta información es clave para el seguimiento clínico y la toma de decisiones médicas informadas.

---

## 4. Matriz morfológica

![matriz](https://i.imgur.com/hePCjA3.jpeg)

---

## 5. Tabla de valoración
![tablaval](https://i.imgur.com/8blWgPE.png)

- CS1: Sistema electrónico Arduino con tres sensores de presión adaptables.  
- CS2: Sistema electrónico Arduino con sensores de temperatura adaptables.  
- CS3: Corsé similar al del paciente con material menos rígido.


---

## 6. Conclusión del CS elegido

Después de analizar los tres casos de estudio, consideramos que el CS1, un sistema electrónico Arduino con tres sensores de presión adaptables, es la opción más viable frente al CS2 y al CS3. Esto se debe a que permite obtener información precisa y en tiempo real sobre la fuerza que ejerce el corsé en diferentes zonas del cuerpo, lo cual es fundamental para evaluar y ajustar su efectividad terapéutica. A diferencia del CS2, que se enfoca solo en medir temperatura (más relacionado con la comodidad que con la función correctiva), y del CS3, que propone un cambio en el material sin aportar datos activos, el CS1 ofrece una solución más completa, adaptable y funcional tanto para el médico como para el paciente. Además, el uso de Arduino hace que sea una alternativa accesible y fácil de implementar, tanto en prototipos como en aplicaciones clínicas reales.
## 7. Boceto
![boceto](https://i.imgur.com/jAOIXmP.jpeg)
