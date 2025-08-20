# Laboratorio: Análisis Tabular con pandas y DuckDB

## 0) Objetivos (3 min)
- Leer archivos tabulares con **pandas**; crear **columnas derivadas**; aplicar **agrupaciones** y **filtros**.  
- Repetir el flujo con **DuckDB** (SQL embebido) sobre los mismos archivos.  
- Comparar brevemente **cuándo conviene cada enfoque**.  

**Fuentes oficiales**  
- pandas: https://pandas.pydata.org/docs/  
- DuckDB: https://duckdb.org/docs/ 

Nota: para ahorrar tiempo puedes usar **GitHub Codespaces** en lugar de crear un `venv`. Es opcional, pero puede simplificar la instalación y ejecución de este laboratorio en un entorno ya configurado.  

---

## 1) Preparación (5 min)
1. (Opcional) Crea y activa un **entorno virtual** (venv).  
2. O usa directamente **Codespaces** en GitHub (más rápido, sin instalación manual).  
3. Instala dependencias mínimas:  
   - `pip install pandas`  
   - `pip install pyarrow`  
   - `pip install duckdb`  
4. Ten a mano un archivo **CSV pequeño** (3–6 columnas, ~1–50k filas).  

Puedes encontrar muchos en el internet, por ejemplo https://github.com/MainakRepositor/Datasets

---

## 2) Parte A — pandas 

### A.1 Lectura y exploración
**Tareas**
- Carga el **CSV** a un DataFrame.  
- Inspecciona filas superiores, tipos de datos y conteo de nulos.  
- Identifica una columna clave (ej.: id, fecha, categoría).

**Pistas**
- Revisa en la doc de pandas cómo leer CSV, mostrar primeras filas, `info()` y `isna().sum()`.  

**Criterios de aceptación**
- Explicar cuántas filas y columnas hay, tipos más comunes, columnas con nulos.

---

### A.2 Columnas derivadas y limpieza (10 min)
**Tareas**
- Crea al menos una columna derivada a partir de otras.  
- Normaliza o limpia al menos una columna (texto o fechas).  
- Gestiona nulos en al menos una columna (eliminar, imputar o descartar).  

**Pistas**
- Revisa cómo asignar nuevas columnas y cómo usar `assign`.  
- Para fechas, busca `to_datetime`.  
- Para nulos, revisa `fillna` o `dropna`.  

---

### A.3 Agrupaciones y filtros (12 min)
**Tareas**
- Agrupa por una dimensión (ej.: categoría/fecha/cliente).  
- Calcula al menos dos métricas por grupo.  
- Aplica un filtro booleano antes o después del `groupby`.  
- Exporta el resumen a CSV o Parquet.  

**Pistas**
- Revisa `groupby`, `agg` y `query` en la doc de pandas.  
- Recuerda: tras un filtrado, el índice no se renumera automáticamente; usa `reset_index` si lo necesitas.  


---

## 3) Parte B — DuckDB (≈25 min)

### B.1 Primer query sobre archivo (8 min)
**Tareas**
- Ejecuta una consulta SQL que lea directamente el mismo CSV (sin cargarlo antes en pandas).  
- Selecciona columnas, filtra filas y devuelve un conteo simple.  

**Pistas**
- Busca en la doc de DuckDB cómo consultar archivos con `SELECT ... FROM 'archivo.csv'`.  

---

### B.2 Repetir el análisis en SQL (12 min)
**Tareas**
- Escribe una consulta que replique lo hecho en pandas:  
  - Columnas derivadas (expresiones en `SELECT`).  
  - Filtros (`WHERE`).  
  - Agrupaciones y agregaciones (`GROUP BY`, `SUM`, `AVG`, etc.).  
- Exporta el resumen a CSV o Parquet.  

**Pistas**
- Revisa `COPY TO` en la doc de DuckDB.  
- En Python, revisa `.df()` para traer resultados a pandas.  
