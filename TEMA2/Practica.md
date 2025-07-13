# Guía paso a paso: Simulación de una estación meteorológica en Tinkercad

## Objetivo

Simular un sistema ciberfísico básico: una **estación meteorológica** que muestra la **temperatura y la humedad** usando una placa Arduino y sensores virtuales. Así comprendemos cómo lo físico (datos del sensor) se conecta con lo virtual (procesamiento y visualización).

---

## 1. Crea una cuenta en Tinkercad

1. Ve a [https://www.tinkercad.com](https://www.tinkercad.com)
2. Haz clic en **Iniciar Sesión** (Unirse ahora) o **Registrarse**.
3. Regístrate con una cuenta de correo de Educantabria o usa una cuenta de Google si lo prefieres.

---

## 2. Accede a la sección de "Inicio"

- Una vez dentro, vas a la sección de **"Circuitos"**.
- Pulsa **"Crea tu primer diseño de circuitos"** para comenzar un nuevo proyecto.

---

## 3. Añade los componentes

Busca y arrastra los siguientes elementos al área de trabajo:

- 🟦 1 x **Arduino UNO R3**
- 🌡️ 1 x **Sensor de temperatura y humedad DHT11**
- 🖥️ 1 x **Pantalla LCD 16x2** (opcional)
- ⚡ 1 x **Fuente de alimentación (5V)**
- 🔌 Cables para las conexiones

Puedes encontrar los componentes usando el buscador en la parte derecha.

---

## 4. Realiza las conexiones

Conecta los pines del **DHT11** al **Arduino** así:

| DHT11 | Arduino UNO |
|--------|-------------|
| VCC    | 5V          |
| GND    | GND         |
| DATA   | Pin digital 2 |

Conecta también la **pantalla LCD** (si se desea), o bien solo muestra los datos por el monitor serial.

---

## 5. Programa el Arduino

Haz clic en el botón **"Code"** (Código) y selecciona la opción **"Text"** en vez de "Blocks".

Copia este ejemplo básico:

```cpp
#include "DHT.h"

#define DHTPIN 2      // Pin digital donde está conectado el DHT
#define DHTTYPE DHT11 // Tipo de sensor

DHT dht(DHTPIN, DHTTYPE);

void setup() {
  Serial.begin(9600);
  dht.begin();
}

void loop() {
  float h = dht.readHumidity();
  float t = dht.readTemperature();

  if (isnan(h) || isnan(t)) {
    Serial.println("Error al leer del sensor DHT11");
    return;
  }

  Serial.print("Humedad: ");
  Serial.print(h);
  Serial.print(" %\t");
  Serial.print("Temperatura: ");
  Serial.print(t);
  Serial.println(" °C");

  delay(2000);
}
```

---

## 6. Simula tu proyecto

* Haz clic en el botón **"Start Simulation"** (Iniciar simulación).
* Observa cómo aparecen los datos en el **Monitor Serial** (pulsa en el icono del monitor en la parte inferior del editor).
* Puedes variar los valores del sensor haciendo clic sobre él.

---

## 7. (Opcional) Mejora el diseño

* Añade una **pantalla LCD** para mostrar los datos físicamente en lugar del monitor serial.
* Agrega un **LED** que se encienda si la temperatura supera un valor.
* Simula enviar los datos a la nube (comentando en el código dónde iría esa parte).

---

## 8. Guarda y comparte tu proyecto

* Pulsa en el nombre del circuito (arriba) para renombrarlo, por ejemplo: `Estacion_meteorologica_virtual`.
* Haz clic en el botón **"Share"** (Compartir) para obtener un enlace público.

---

## 🧪 Resultado

Has creado una **simulación de un sistema ciberfísico** donde un sensor virtual envía datos a un microcontrolador que los procesa y los muestra digitalmente. Esta experiencia reproduce a pequeña escala lo que ocurre en miles de entornos reales industriales, agrícolas o domésticos conectados al Internet de las cosas (IoT).

```

---


```
