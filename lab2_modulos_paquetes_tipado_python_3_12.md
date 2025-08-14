# Laboratorio: MÓDULOS, PAQUETES y (Opcional) ANOTACIONES DE TIPADO

**Nota:** Utiliza Python 3.12 y cualquier referencia o documento oficial como sea necesario

---

## Parte A — Módulos (20–25 min)  
**Escenario:** construirás un módulo con utilidades coherentes y lo consumirás desde un punto de entrada.

**Tareas**  
1. Crea un archivo `.py` con un conjunto de **3–4 funciones** sobre un tema concreto (elige uno):  
   - Utilidades de cadenas (normalizar, validar, formatear).  
   - Utilidades numéricas (operaciones aritméticas seguras, validaciones).  
   - Manejo básico de fechas/horas (formateo, diferencia simple, validación).  
2. Crea un segundo archivo que importe ese módulo y utilice cada función con casos representativos, incluyendo al menos un caso límite que produzca un error controlado o validación.  
3. Documenta en un archivo de notas:  
   - Qué **API** pública ofrece tu módulo (funciones y propósito).  
   - Por qué decidiste separarlo como un módulo independiente.  

**Criterios de aceptación**  
- Funciones coherentes y relacionadas.  
- Importadas y utilizadas correctamente desde otro archivo.  
- Al menos un caso límite probado y documentado.  

**Referencia oficial**  
- [Modules – Python 3.12 Docs](https://docs.python.org/3.12/tutorial/modules.html)

---

## Parte B — Paquetes (20–25 min)  
**Escenario:** organizarás varios módulos bajo un paquete con espacio de nombres propio.

**Tareas**  
1. Crea una carpeta para tu paquete con **al menos dos módulos** temáticos.  
2. Añade un archivo `__init__.py` en la carpeta del paquete (puede estar vacío o reexportar funciones clave).  
3. Desde un script principal:  
   - Importa funciones usando **importaciones absolutas** (`paquete.modulo`).  
   - Desde un módulo dentro del paquete, haz una **importación relativa** a otro módulo del mismo paquete.  
4. Documenta en tus notas:  
   - Cuándo usar importaciones absolutas vs. relativas.  
   - Qué expone tu `__init__.py` y por qué.  

**Criterios de aceptación**  
- Paquete con `__init__.py` y ≥2 módulos bien diferenciados.  
- Importaciones absolutas y relativas probadas y documentadas.  

**Referencia oficial**  
- [Packages – Python 3.12 Docs](https://docs.python.org/3.12/tutorial/modules.html#packages)

---

## Parte C — Opcional: Investigación sobre anotaciones de tipado (15–20 min)  
**Escenario:** comprenderás qué son las anotaciones de tipado, para qué sirven y cómo se usan en Python.

**Tareas**  
1. Investiga en la documentación oficial qué son las **type hints** y cómo se aplican a variables, parámetros y valores de retorno.  
2. Busca ejemplos que combinen tipos básicos (`int`, `str`, `list`) y combinaciones (`Union`, `Optional`).  
3. Resume en tus notas (máx. 8 líneas):  
   - Qué aportan las anotaciones de tipo en proyectos reales.  
   - Limitaciones en tiempo de ejecución.  
   - Herramientas que las aprovechan (por ejemplo, `mypy`, `pyright`).  

**Referencia oficial**  
- [Typing – Python 3.12 Docs](https://docs.python.org/3.12/library/typing.html)  
- [PEP 484 – Type Hints](https://peps.python.org/pep-0484/)  
