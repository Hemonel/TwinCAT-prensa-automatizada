# Prensa automátizada con 2 motores paso a paso
El programa controla el funcionamiento de una prensa automatizada. Contiene software de detección de errores, 6 modos de trabajo y seguridad con mando a 2 manos.

![imagen documentos del programa](https://github.com/Hemonel/TwinCAT-prensa-automatizada/assets/153218898/5b01f7e6-dabe-42ba-822a-85525a0fe4fd)

## 1 Sofware
Twincat XAE

## 2 Modos de trabajo
El sistema tiene 4 modos:
- Stop
- Auto
-	Manual
-	StopSec
-	Reseteando
-	Parando

![modos](https://github.com/Hemonel/TwinCAT-prensa-automatizada/assets/153218898/c78759eb-a31c-47c3-9868-d381096174d1)

### 2.1 Stop
En este modo espera a que se le de a marcha para entrar a modo automático o que se seleccione modo manual.

### 2.2 Auto
El modo más complejo ya que activa la máquina de estados que controla la prensa.

De este modo se sale a parando si se pulsa paro o a manual si se selecciona manual.

El sistema funciona ciclicamente siguiendo estos estados:

#### 2.2.1 Parada
Espera la señal de inicio.

#### 2.2.2 Entrando
Activa el eje que coloca la pieza en su lugar.

#### 2.2.3 Prensando
Activa el segundo eje cuya función es prensar la pieza.

#### 2.2.4 Aguantando
Mantiene la prensa durante 3 s.

#### 2.2.5 Liberando
El eje de prensado se retira.

#### 2.2.6 Sacando
El eje que colocó la pieza ahora la retira.

### 2.3 Manual
Modo para el manejo manual de la máquina.

Se sale al indicar modo automático.

### 2.4 StopSec
Stop seguro (sin potencia) para cuando la máquina se produce un error.

Se llega a este modo desde cualquier otro siempre que ocurra un error.

### 2.5 Reseteando
Modo temporal para cuando se solicita reset despues de un error, espera 1 s antes de comprobar si sigue habiendo errores, si los hay va a stopsec.

### 2.6 Parando
Si se le indica paro estando en automático se espera a que los ejes se detengan antes de ir a stop.

## 3 Vuelta a casa
El programa cuenta con una función de vuelta a casa (vueltaacasa), de forma que cuando se le solicita los ejes vuelven a la posición 0.

## 4 Interfaz digital
Para simular o controlar digitalmente el sistema se ha diseñado una interfaz que permite visualizar todo lo necesario.
![interfaz](https://github.com/Hemonel/TwinCAT-prensa-automatizada/assets/153218898/8260fac7-6695-4e95-9626-d159c4aacc78)
