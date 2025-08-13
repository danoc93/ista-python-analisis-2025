# Laboratorio de Python 3.12 – Ejercicios guiados (Funciones, Métodos, Excepciones y Decoradores)

---

## 0) Objetivos
- Verificar instalación de **Python 3.12**.
- Consolidar fundamentos de **funciones** y **métodos** (first-class, funciones internas, closures).
- Dominar **manejo de excepciones**.
- Aplicar **decoradores** para extender comportamientos de forma limpia y reutilizable.

**Fuentes oficiales:**
- Descargas Python 3.12: https://www.python.org/downloads/
- Tutorial – Funciones: https://docs.python.org/3.12/tutorial/controlflow.html#defining-functions
- Tutorial – Errores y Excepciones: https://docs.python.org/3.12/tutorial/errors.html
- Decoradores (más sobre `def` y funciones): https://docs.python.org/3.12/tutorial/controlflow.html#more-on-defining-functions
- Using Python (Windows/macOS/Linux): https://docs.python.org/3.12/using/


## 1) Preparación: Instalar Python 3.12

En caso de no tenerlo, usar las siguientes guias:

### 1.1 Windows
1) Descarga Python 3.12 desde la página oficial: [https://www.python.org/downloads/](https://www.python.org/downloads/)  
2) Activa “Add Python to PATH” en el instalador.  
3) Verifica en terminal:
```powershell
python --version
# o
py -3.12 --version
```

Guía oficial: [Using Python on Windows](https://docs.python.org/3.12/using/windows.html)

### 1.2 macOS
1) Descarga el instalador desde: [https://www.python.org/downloads/macos/](https://www.python.org/downloads/macos/)  
2) Alternativa con Homebrew:  
```bash
brew install python@3.12
```
3) Verifica:
```bash
python3.12 --version
```

Guía oficial: [Using Python on macOS](https://docs.python.org/3.12/using/mac.html)

### 1.3 Linux
1) Instala desde repositorios o compila desde fuente siguiendo la [guía oficial](https://docs.python.org/3.12/using/unix.html).  
2) Verifica:
```bash
python3.12 --version
```

## 2) Módulo A — Funciones y Métodos

### A.1 – Funciones como valores
**Escenario:** vas a construir un “mini centro de comandos” que ejecuta distintas acciones en función de un nombre.  
**Tarea:**  
1) Implementa **tres** funciones: `saludar(nombre)`, `despedir(nombre)`, `aplaudir(nombre)` que devuelvan mensajes.  
2) Crea un diccionario `acciones` que mapee nombres de acción (`"saludar"`, `"despedir"`, `"aplaudir"`) a las **funciones**.  
3) Implementa `ejecutar(accion, *args, **kwargs)` que busque la función por nombre y la ejecute.  
**Criterios de aceptación:**  
- `ejecutar("saludar", "Ana")` devuelve `"Hola, Ana"`.  
- Si se solicita una acción inexistente, se lanza una **excepción** clara.

**Pistas:** recuerda que las funciones son objetos y se pueden guardar en estructuras de datos.


### A.2 – Funciones internas y closures
**Escenario:** necesitas generadores de descuentos reutilizables.  
**Tarea:**  
1) Implementa `crear_descuento(porcentaje)` que devuelva una **función interna** que reciba un precio y aplique el descuento.  
2) Crea `descuento10 = crear_descuento(0.10)` y `descuento25 = crear_descuento(0.25)`.  
3) Verifica que cada función aplique correctamente su porcentaje.  
**Criterios de aceptación:**  
- `descuento10(100)` → `90.0` ; `descuento25(80)` → `60.0`.  
**Pista:** la función interna debe **capturar** `porcentaje` (closure).


## 3) Módulo B — Excepciones

### B.1 – Validación de entrada (sin I/O de archivos)
**Escenario:** validas números proporcionados por el usuario (simula con valores en una lista).  
**Tarea:**  
1) Implementa `parsear_enteros(entradas: list[str]) -> list[int]` que convierta cada string a entero.  
2) Si un elemento no es convertible, **captura** `ValueError` y agrega un mensaje de error a una lista `errores` (mantén ambas listas en paralelo o devuelve una tupla `(valores, errores)`).  
3) Garantiza que el proceso continúa aunque haya errores.  
**Criterios de aceptación:**  
- Para `["10", "x", "3"]` obtienes `[10, 3]` y algún registro de error para `"x"`.  
**Pista:** usa `try/except` alrededor de `int(...)` y decide qué reportar.


### B.2 – Excepciones personalizadas y `raise`
**Escenario:** validación de una operación de compra.  
**Tarea:**  
1) Define la excepción `CantidadInvalida` (hereda de `Exception`).  
2) Implementa `calcular_total(precio_unitario, cantidad)` que:  
   - Lance `CantidadInvalida` si `cantidad <= 0`.  
   - Lance `ValueError` si `precio_unitario < 0`.  
   - Devuelva el total en caso válido.  
3) Maneja las excepciones desde un punto de llamada y muestra mensajes claros.  
**Criterios de aceptación:**  
- `calcular_total(10, 3)` → `30`.  
- `calcular_total(10, 0)` lanza `CantidadInvalida` con mensaje claro.


## 4) Módulo C — Decoradores

### C.1 – Decorador de validación
**Escenario:** quieres asegurar contratos simples en tus funciones.  
**Tarea:**  
1) Implementa `requiere_positivos` que verifique que **todos** los argumentos numéricos sean `> 0`; si no, lance `ValueError` con un mensaje útil.  
2) Aplícalo a `calcular_descuento(precio, porcentaje)` y a `escala(valor, factor)`.  
**Criterios de aceptación:**  
- `calcular_descuento(100, 0.2)` → `80`.  
- `calcular_descuento(-1, 0.2)` lanza `ValueError` con mensaje claro.

### Notas finales
- Mantén las **capturas de excepción explícitas** (evita bloques genéricos que oculten problemas).  
- Nombra con claridad funciones y variables; escribe **mensajes de error útiles**.  
- Si te atascas, consulta la documentación oficial y pregunta a este asistente.
