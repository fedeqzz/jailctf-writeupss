<img width="188" height="622" alt="image" src="https://github.com/user-attachments/assets/46e9584c-530e-4e00-9880-a5a6c80ca1a6" />

# V1t CTF 2025
## OSINT : Lost in Hokkaido

---

## Description

<img width="524" height="579" alt="image" src="https://github.com/user-attachments/assets/15a472f7-e451-460e-b9a3-cf27e7276476" />

My friend sent me this picture, the snowflakes are so beautiful.  
Can you figure out where is this?

**Flag format:** `v1t{latitude,longitude}`  
**Example:** `v1t{22.44385,-74.22042}`  

[🔗 File Download (Google Drive)](https://drive.google.com/file/d/1BDD4-_E6397He7ZUsoV0e15TRwM2tUhY/view?usp=sharing)

---

## Files

<img width="3468" height="4624" alt="chall (1)" src="https://github.com/user-attachments/assets/73f9566d-15f0-49b3-8093-13aee1c93d52" />

- **File:** `chall.png`  
- **Size:** ~15 MB  
- **Description:** Fotografía nevada con dos casas, un auto azul y uno rojo. Al fondo se observa una estructura tipo fábrica y varios postes eléctricos con carteles en japonés y números visibles.

---

## Analysis
A simple vista, la imagen muestra una calle residencial japonesa cubierta de nieve.  
Los elementos más relevantes para el análisis inicial fueron:

- 🏠 **Dos casas** típicas de zonas residenciales japonesas.  
- 🚗 **Dos autos** (uno azul y otro rojo) estacionados frente a las casas.  
- ⚡ **Un poste eléctrico** con tres carteles visibles:
  - Uno **amarillo** con el número `11363`.
  - Otro **blanco** con una serie de dígitos `73-77-85-07`.
  - Un tercero **blanco** con caracteres japoneses borrosos.
- 🏫 **Una estructura grande al fondo**, que parecía una fábrica (aunque después se determinó que era una escuela).

El estilo arquitectónico y la nieve apuntaban a una zona del norte de Japón, muy probablemente **Hokkaido**.

---

## Theory
En los retos **OSINT (Open Source Intelligence)** de geolocalización, el objetivo es encontrar una ubicación real a partir de información visual o contextual.  
Algunos métodos útiles incluyen:

- **Búsqueda inversa de imágenes** → Google, Yandex, TinEye.  
- **Identificación de elementos característicos** → señales, vehículos, idioma, clima, arquitectura.  
- **Análisis de metadatos EXIF** → coordenadas GPS o modelos de cámara.  
- **Sistemas de numeración en postes eléctricos (Japón)** → cada poste contiene códigos que indican región y distrito.

Con esta información, es posible reducir drásticamente el área de búsqueda dentro de Google Maps o Street View.

---

## Solution

### Step 1: Observación inicial
Se abren los detalles visibles en la imagen:
- Se distinguen los números **11363** y **73-77-85-07** en los carteles.  
- Por el tipo de poste, los vehículos y la nieve, la primera hipótesis fue **Hokkaido**.  
- Los números inferiores del poste parecían incompletos, pero se alcanzaban a ver los pares **41** y **posiblemente 42 o 43**, aunque en ese momento no se entendía su significado.

---

### Step 2: Búsqueda inversa
Se subió la imagen a **Google Imágenes**, lo cual arrojó coincidencias con fotografías y paisajes típicos de **Sapporo (Hokkaido)**.  
Esto confirmó que el área era probablemente del norte de Japón.

---

### Step 3: Análisis de postes eléctricos

<img width="720" height="412" alt="image" src="https://github.com/user-attachments/assets/f7f9d531-d700-4e00-b57c-b9782db7de00" />

Buscando información sobre cómo se leen los números en los postes eléctricos japoneses, se encontraron varios sitios y documentos en japonés, pero ninguno explicaba claramente el formato.  
Luego apareció un **video japonés** donde se mostraba un mapa de regiones y la correspondencia de los primeros pares de números con zonas específicas del país.  
Gracias a este video y una página japonesa adicional, se descubrió que **faltaban dos pares de números en la parte inferior del poste** que no se veían completamente en la foto.  
Al observar con más detalle, se alcanzaban a distinguir parcialmente **41**, **42** y **43**.

> 🎥 **Video:** https://www.youtube.com/watch?v=i14tTl6BF7Y

Ese fue el momento en el que se entendió que los postes tienen **seis pares numéricos en formato vertical**, donde los **dos primeros pares indican región y distrito** respectivamente.

---

### Step 4: Identificación de región

<img width="818" height="713" alt="image" src="https://github.com/user-attachments/assets/687e0540-b705-4f22-865a-4ddccbc919d4" />

Con la información del video, se identificó que el par **41** correspondía a la **región de Hokkaido**.  
Inicialmente se pensó que el siguiente número visible era **43**, por lo que se exploraron zonas asociadas a ese distrito en **Google Street View**.  

Sin embargo, tras comparar más postes, se observó que los números cambiaban progresivamente de **43 a 42** conforme se desplazaba por la zona, indicando una **transición entre distritos**.  
Ahí se descubrió que el número correcto era **42**, y que los postes del área compartían patrones muy similares al de la imagen del reto.

A partir de este punto, se empezó a **emparejar los números de los postes con sus ubicaciones**, utilizando las referencias visuales (casas, carreteras, nieve y estructuras).

---

### Step 5: Localización final
Ya dentro del distrito **42**, se identificaron postes con numeraciones muy similares.  
Mientras se recorría la zona, apareció una estructura grande al fondo idéntica a la de la imagen inicial.  
Retrocediendo unos metros con **Google Street View**, se pudo observar:

- Las **dos casas** con la misma forma y orientación.  
- Los **vehículos azul y rojo** estacionados.  
- El **poste con el código 11363** coincidente.  
- Y la **estructura del fondo**, que finalmente resultó ser una **escuela**, no una fábrica.

Después de comparar todos los elementos visuales, la ubicación quedó confirmada.

---

## Flag
```text
v1t{43.12345,141.56789}
