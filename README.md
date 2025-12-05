# practica_filtros_digitales **Ciencia de Datos**
Práctica en R sobre diseño de filtros digitales: análisis de polos/ceros, respuesta en frecuencia y aplicación a un ECG con eliminación de ruido.

Este repositorio contiene una práctica completa sobre **diseño, análisis y aplicación de filtros digitales en R**, centrada en sistemas LTI discretos y en cómo la **posición de polos y ceros afecta a su respuesta en frecuencia**.

Además, se realiza una **aplicación real** filtrando un ECG con ruido eléctrico de 50 Hz, combinando un filtro *notch* y un filtro pasa-altos para eliminar la interferencia y la variación de línea basal.

---

##  Objetivos de la práctica

- Analizar sistemas discretos mediante la **transformada Z**  
- Visualizar **polos, ceros, respuesta en frecuencia e impulsional**  
- Comparar filtros **FIR (solo ceros) vs IIR (solo polos)**  
- Estudiar el efecto de los parámetros `r` y `ω0`  
- Filtrar un **ECG ruidoso** para recuperar señal limpia

---

##  Contenido del repositorio

| Archivo | Descripción |
|---|---|
| `practica_filtros_digitales.Rmd` | Informe completo con código, explicaciones y resultados |
| `practica_filtros_digitales.pdf` | PDF renderizado desde Rmd |
| `ecg.mat` | ECG real contaminado por ruido de red |
| `README.md` | Este documento |

---

##  Qué se hace en este proyecto

###  Análisis de filtros FIR `H1(z)`
- Implementación mediante `impz()` y `freqz()`
- Efecto del parámetro `r` sobre el ancho del notch  
- Efecto de `ω0` desplazando la frecuencia de rechazo  
- Visualización de polos y ceros con `zplane()`

###  Análisis de filtros IIR `H2(z) = 1 / H1(z)`
- Los polos pasan a ser los ceros de `H1(z)`
- Estudio de estabilidad según `|r| < 1`
- Respuesta resonante/pasabanda

###  Filtro peine (promediador)
- Cálculo manual de ceros
- Distribución uniforme sobre el círculo unidad
- Interpretación en el espectro como **peine periódico**

###  Filtrado de un ECG real
✔ Eliminación del ruido de red 50 Hz (notch)  
✔ Filtro pasa-altos para corregir línea basal  
✔ Comparación señal original vs filtrada

---

## Cómo ejecutar
# Instalar librerías necesarias
install.packages(c("signal","pracma","R.matlab"))

# Ejecutar desde RStudio o R
rmarkdown::render("practica_filtros_digitales.Rmd")

---

## Resultados

El informe en PDF (`practica_filtros_digitales.pdf`) contiene todas las figuras y resultados:
- Respuesta en frecuencia de diferentes filtros
- Diagramas de polos y ceros
- Filtrado de un ECG real (antes y después del notch y del filtro pasa-altos)
