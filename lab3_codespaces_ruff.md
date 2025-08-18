# Laboratorio: Codespaces, entorno virtual, ruff/mypy, pruebas y CI

Trabajaremos en el entorno de Codespaces empleando todas las herramientas revisadas hasta la fecha.

---

## 0) Objetivos
- Entender como usar **GitHub Codespaces**
- Aprender a gestionar un **entorno virtual** de Python, generar un **archivo de requisitos** e **instalar** dependencias.
- Instalar y ejecutar **ruff** (lint/format) y **mypy** (type checking).
- *(Opcional)* Configurar **pytest** y escribir **un par de pruebas automatizadas**.
- *(Opcional)* Explorar **CI** con **GitHub Actions** o **CircleCI**.

---

## 1) Requisitos previos
- Usar Python disponible en Codespaces
- Usa la terminal del Codespace como sea necesario

**Referencias:**
- GitHub Codespaces – Qué es y cómo empezar: https://docs.github.com/en/codespaces
- Python venv (entornos virtuales): https://docs.python.org/3/library/venv.html
- Gestión de dependencias con pip: https://pip.pypa.io/en/stable/user_guide/

---

## 2) Crear tu Codespace
0. Crea un repositorio en blanco
1. En tu repositorio, usa el botón **Code** → pestaña **Codespaces** → **Create codespace on main**.
2. Espera a que el entorno arranque (VS Code en el navegador). Verás un terminal integrado.
3. Verifica que Python y pip estén disponibles (usa los comandos habituales desde el terminal; no los incluimos aquí para que los busques y ejecutes tú).

---

## 3) Entorno virtual y dependencias
1. Crea un **entorno virtual** en la raíz del repo (nómbralo, por ejemplo, `.venv`).
2. **Actívalo** en el terminal del Codespace.
3. Crea un archivo **`requirements.txt`** con las herramientas que usarás en este laboratorio: ruff, mypy y pytest (pytest es opcional pero recomendado).
4. **Instala** las dependencias desde el archivo de requisitos.
5. Genera un lock file de versiones para reproducibilidad.

**Pistas:**
- Revisa la documentación de venv para el comando de creación y de pip para la activación/instalación según tu shell.
- Para instalar desde un archivo de requisitos, consulta “Install from requirements files” en la guía de pip.
- Para crear un Lockfile revisa las diapositivas.

**Docs:**
- venv: https://docs.python.org/3/library/venv.html
- pip (requirements files): https://pip.pypa.io/en/stable/user_guide/#requirements-files

---

## 4) Módulo de ejemplo con tipado incompleto
1. Crea una carpeta de código fuente (por ejemplo, `src/`).
2. Dentro, crea un archivo (por ejemplo, `operaciones.py`) con **dos funciones** sencillas (suma y división) pero **sin todas las anotaciones de tipo** y con, al menos, **un caso mal diseñado** (por ejemplo, retornar un valor especial en vez de lanzar error) para que mypy se queje.
3. Crea un pequeño archivo ejecutable (por ejemplo, `main.py`) que **importe** tus funciones y las utilice.

**Pistas para provocar advertencias:**
- Omite anotaciones en algunos parámetros.
- Devuelve `None` en una ruta donde esperaría un número.
- Mezcla `int`/`float` sin declarar tipos explícitos.

**Docs:**
- Anotaciones de tipo en Python: https://docs.python.org/3/library/typing.html

---

## 5) Configurar ruff y mypy

0. Instala y lee como configurar ruff y mypy.
1. Decide dónde centralizar la configuración (sugerencia: `pyproject.toml`).
2. Añade configuración mínima para **ruff** (activación de linter y formateo) y **mypy** (modo estricto, directorios a analizar, exclusiones si hacen falta).
3. Ejecuta ruff y mypy desde el terminal del Codespace y **lee con calma** todos los mensajes.

**Pistas para ruff:**
- Empieza con reglas por defecto y arreglos automáticos cuando sea posible.
- Si te abruma, desactiva temporalmente algunos chequeos y vuelve a activarlos después.

**Pistas para mypy:**
- Identifica los avisos por **tipos faltantes** y por **tipo de retorno incierto**.
- Agrega **anotaciones** en firmas y variables intermedias.
- Considera usar `typing.Optional`, `Union` o `Annotated` cuando tenga sentido, o refactoriza para evitar retornos ambiguos.

**Docs:**
- ruff: https://docs.astral.sh/ruff/
- mypy: https://mypy.readthedocs.io/en/stable/
- pyproject.toml (PEP 518): https://peps.python.org/pep-0518/

---

## 6) Iteración: corrige hasta pasar mypy/ruff
1. Aborda los mensajes de mypy **del más grave al más simple**.
2. Refactoriza funciones que devuelvan varios tipos según rama lógica.
3. Re-lanza ruff y mypy hasta que los reportes queden **limpios** (o con excepciones justificadas y acotadas).

**Pistas:**
- Prefiere **tipos concretos** en entradas/salidas.
- Usa **comprobaciones explícitas** en vez de confiar en coerciones implícitas.
- Documenta puntualmente cualquier `type ignore` y minimiza su uso.

---

## 7) (Opcional) Pruebas con pytest
1. Crea una carpeta de pruebas (por ejemplo, `tests/`).
2. Escribe **dos pruebas**: una para `sumar` y otra para `dividir`, cubriendo casos normales y borde (p.ej., división por cero).
3. Ejecuta pytest y verifica que pasan.
4. Añade una excepción o comportamiento claro para los **casos inválidos** y ajusta las pruebas.

**Pistas:**
- Piensa en **valores límite** y **entradas inválidas**.
- Organiza los tests por comportamiento, no por implementación.

**Docs:**
- pytest: https://docs.pytest.org/en/stable/
- Buenas prácticas: https://docs.pytest.org/en/stable/goodpractices.html

---

## 8) (Opcional) CI con GitHub Actions o CircleCI
**Alternativa A – GitHub Actions**
1. Crea un flujo de trabajo en `.github/workflows/` que:
   - Instale dependencias.
   - Ejecute ruff y mypy.
   - (Opcional) Ejecute pytest.
2. Haz un commit y abre un pull request para ver el resultado en la pestaña **Actions**.

**Docs:**
- GitHub Actions – Conceptos: https://docs.github.com/en/actions/learn-github-actions/understanding-github-actions
- GitHub Actions – Guía rápida: https://docs.github.com/en/actions/quickstart

**Alternativa B – CircleCI**
1. Crea la configuración en `.circleci/` para instalar dependencias y correr ruff/mypy/pytest.
2. Conecta tu repositorio en CircleCI y activa el proyecto.

**Docs:**
- CircleCI – Getting Started: https://circleci.com/docs/getting-started/
- CircleCI – Python: https://circleci.com/docs/languages/python/

**Sugerencias generales de CI:**
- Cachea dependencias para acelerar.
- Ejecuta linters y type-checking **antes** de tests para fallar rápido.
- Mantén los jobs **claros y pequeños**.


---

Recordemos que los laboratorios son opcionales, pero con evidencia se ganan 1.5% extras, en caso de este proyecto incluir referencia al repositorio creado en este laboratorio en el repositorio de la clase.
