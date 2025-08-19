# Laboratorio: Pytest + Módulo simple y CSV en Python 3.12

**Duración estimada:** ~1 hora  
**Objetivo:** Practicar pruebas con **pytest** sobre un módulo sencillo y validar un dataset en **CSV** con la librería estándar de Python.

---

## Parte A — Módulo simple probado con pytest (25–30 min)

**Escenario**  
Diseñarás un módulo con funciones básicas y validarás su comportamiento con pruebas unitarias.

**Tareas**  
1. Crea un módulo con 2–3 funciones simples en un dominio elegido (texto, números o fechas).  
2. Especifica qué debe hacer cada función (entradas y salidas esperadas).  
3. Escribe casos de prueba con **pytest** que incluyan:  
   - Resultados correctos para entradas válidas.  
   - Manejo de casos límite (cadenas vacías, ceros, etc.).  
   - Errores cuando las entradas no sean válidas.  
4. Documenta brevemente tus pruebas y cómo ejecutarlas.


---

## Parte B — Lectura y validación de CSV con pytest (25–30 min)

**Escenario**  
Usarás la librería estándar **csv** para leer un dataset público conocido y validar su contenido con pytest.

**Tareas**  
1. Selecciona un CSV público pequeño/mediano (ejemplo: Kaggle, datos abiertos, GitHub).  
Por ejemplo [Hay Varios Gratis](https://docs.databricks.com/aws/en/discover/databricks-datasets#third-party-sample-datasets-in-csv-format).  

2. Define reglas mínimas de validación, como:  
   - Columnas obligatorias presentes.  
   - Tipos esperados en cada columna.  
   - Reglas simples (ej. valores no negativos, IDs únicos).  
3. Escribe pruebas con pytest que verifiquen esas reglas.  
4. Documenta el dataset elegido (origen, delimitador, columnas) y cómo ejecutar las pruebas.


---

## Referencias
- [pytest](https://docs.pytest.org/)  
- [Módulo csv — Python 3.12](https://docs.python.org/3.12/library/csv.html)
