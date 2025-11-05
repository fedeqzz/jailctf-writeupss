# jailctf-writeupss



<img width="524" height="579" alt="image" src="https://github.com/user-attachments/assets/15a472f7-e451-460e-b9a3-cf27e7276476" />

<img width="188" height="622" alt="image" src="https://github.com/user-attachments/assets/46e9584c-530e-4e00-9880-a5a6c80ca1a6" />

# V1t CTF 2025
## OSINT : Lost in Hokkaido

---

## Description
Jimmy volvió a perderse… esta vez, en un lugar cubierto de nieve en algún punto de Japón.  
Solo tenemos una imagen con unas casas, un coche azul, otro rojo y un misterioso poste con números.  
¿Podrás encontrar dónde está?

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

Los códigos japoneses suelen tener el formato `XX-YY-NNNNN`, donde:
- `XX` = región eléctrica.  
- `YY` = distrito o subzona.  
- `NNNNN` = número de poste.

Con esta información, es posible reducir drásticamente el área de búsqueda dentro de Google Maps o Street View.

---

## Solution

### Step 1: Observación inicial
Se abren los detalles visibles en la imagen:
- Se distinguen los números **11363**, **73-77-85-07** y parcialmente **41-42**.  
- Arquitectura japonesa, vehículos y nieve → **Hokkaido** es la primera hipótesis.

### Step 2: Búsqueda inversa
Se sube la imagen a **Google Imágenes**.  
Los resultados más similares corresponden a calles en **Sapporo**, una de las ciudades principales de Hokkaido.

### Step 3: Análisis de postes eléctricos
Se investigó cómo se leen los códigos en los postes de Japón.  
Varios artículos (en japonés) y un video mostraban que los **primeros pares numéricos** indican región y distrito.  
Además, se confirmó que los postes de Japón tienen **seis pares numéricos** en formato vertical.

### Step 4: Identificación de región
Entre las listas encontradas, la región **41** pertenece a **Hokkaido**.  
Comenzando desde Sapporo, se recorrieron manualmente varias zonas mediante **Google Street View** para comparar los postes y las edificaciones.

### Step 5: Localización final
Tras varios intentos, se encontró una estructura al fondo idéntica a la de la foto.  
Al retroceder unos metros en Street View, aparecieron las **dos casas, los autos (azul y rojo) y el poste con los mismos números.**  
La “fábrica” del fondo resultó ser en realidad una **escuela**.

---

## Flag
```text
MYCTF{Hokkaido_Sapporo_Region42}
