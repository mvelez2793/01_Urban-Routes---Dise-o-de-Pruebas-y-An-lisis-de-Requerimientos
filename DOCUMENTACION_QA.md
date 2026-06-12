# 📂 Documentación Técnica de Diseño de Pruebas: Urban Routes (Car Sharing)

Este documento profundiza en la estrategia de diseño de pruebas, el análisis algorítmico y la aplicación de técnicas formales de testing para el módulo "Compartir Automóvil" (Car Sharing) de Urban Routes.

## 🧠 Contexto del Proyecto y Objetivos
El objetivo principal de este sprint fue asegurar la calidad de la nueva funcionalidad de alquiler de vehículos compartidos. El alcance de las pruebas se dividió en dos frentes críticos:
1. **Validación de UI/UX y Formularios:** Comprobación estricta de la ventana emergente "Agregar licencia de conducir", asegurando que los campos "Nombre" y "Apellido" rechazaran datos inválidos.
2. **Validación de Lógica de Negocio (Backend):** Verificación del algoritmo que calcula dinámicamente la duración del viaje y el costo, el cual varía dependiendo de la hora del día y la velocidad promedio del vehículo.

## 🎯 Estrategia y Técnicas de Diseño Aplicadas

Para garantizar una cobertura óptima sin redundancia, apliqué las siguientes técnicas de ingeniería de software:

*   **Mapas Mentales (Mind Mapping):** Utilizado para modelar visualmente la interfaz y el comportamiento esperado del modal de la licencia de conducir.
*   **Clases de Equivalencia y Valores Límite (BVA):** Aplicado a los campos de texto para estresar las restricciones de la base de datos.
*   **Diagramas de Flujo:** Diseñé un diagrama lógico para mapear las condicionales `If/Else` del sistema respecto a los rangos horarios y la velocidad.

---

## 🧪 Evidencia Técnica 1: Partición de Equivalencia (Campos de Texto)

Análisis de fronteras aplicado al campo **"Nombre"** y **"Apellido"**. La restricción del sistema exigía una longitud de texto válida entre 2 y 14 caracteres.

| Clase de Equivalencia | Tipo | Límites (`Li`, `Ls`) | Valores de Prueba (Positivos) | Valores de Prueba (Límites/Negativos) |
| :--- | :--- | :--- | :--- | :--- |
| Longitud Válida | Rango | 2, 14 | 10 caracteres ("Roque Ivan") [9] | `Li: 2`, `Ls: 14`, `Li-1: 1` (Inválido), `Ls+1: 15` (Inválido) |
| Caracteres Especiales | Conjunto | N/A | N/A | "Auxili@dor13" (Inválido) |
| Caracteres No Latinos | Conjunto | N/A | "María" (Uso de tildes)  | N/A |

---

## 🧮 Evidencia Técnica 2: Validación del Algoritmo de Precios

La aplicación calcula el precio basándose en la distancia y una **matriz de velocidad dinámica** que depende de la hora de salida. 

**Reglas de Negocio extraídas para el Testing:**
*   `00:01 - 08:00` ➔ Velocidad: 45 km/h .
*   `08:01 - 12:00` ➔ Velocidad: 30 km/h .
*   **Fórmulas evaluadas:** 
    *   `T (Duración del viaje) = S (distancia) / V (velocidad a la hora de salida)`.
    *   `Costo = T (Duración del viaje) * $0.1 USD/minuto`.

### Ejemplo de Caso de Prueba Matemático (Caja Negra)

| ID | Escenario (Hora de inicio: 00:01-08:00) | Datos de Prueba (Inputs) | Cálculos Internos Validados | Resultado Esperado |
| :--- | :--- | :--- | :--- | :--- |
| **p-1** | Cálculo de costo y tiempo válido en horario nocturno/madrugada [15, 16]. | **Desde:** East 2nd Street, 601 <br> **Hasta:** 1717 E 7th St <br> **Distancia (S):** 1.5 km [16] | **Velocidad (V):** 45 km/h <br> **T =** 1.5 / 45 = 0.0333 hrs (2 min)  <br> **Costo =** 2 min * $0.1  | **Duración del viaje:** 2 minutos. <br> **Costo del viaje:** $0.2 USD. |

> *Nota: Este nivel en los casos de prueba garantizó que el equipo de desarrollo pudiera identificar discrepancias de redondeo y fallos en la asignación de variables de velocidad.*

---
*Documentación estructurada por María Auxiliadora Vélez Mendoza.*