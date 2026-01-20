# 📋 Issues Completos del Proyecto - Redes de Computadoras

**Proyecto:** Redes-3ero-Estudios
**Objetivo:** Aprender Redes de Computadoras en 3 días con enfoque profesional
**Total Issues:** 12
**Fecha creación:** 19 Enero 2026

---

## 🗺️ Mapa de Dependencias

```
Issue #1 (Estructura)
    ↓
Issue #2 (MkDocs)
    ↓
Issue #3 (Módulo 00) ──┐
    ↓                  │
Issue #4 (Módulo 01)   │
    ↓                  │
Issue #5 (Módulo 02)   │
    ↓                  │
Issue #6 (Módulo 03) ──┤
    ↓                  │
Issue #7 (Módulo 04)   │──→ Issue #12 (Guía Examen)
    ↓                  │
Issue #8 (Módulo 05)   │
    ↓                  │
Issue #9 (Módulo 06) ──┘

Issue #10 (Docker) ─────→ Paralelo/Opcional
Issue #11 (CI/CD) ──────→ Paralelo/Después
```

---

## 📅 Plan de Ejecución (3 Días)

### Día 1: Infraestructura + Fundamentos
- [ ] Issue #1: Estructura del proyecto (2-3h)
- [ ] Issue #2: MkDocs (1h)
- [ ] Issue #3: Módulo 00 (3-4h)
- [ ] Issue #4: Módulo 01 (inicio, 2h)

### Día 2: Capas Inferiores
- [ ] Issue #4: Módulo 01 (completar)
- [ ] Issue #5: Módulo 02 (3-4h)
- [ ] Issue #6: Módulo 03 (4-5h)

### Día 3: Capas Superiores + Preparación
- [ ] Issue #7: Módulo 04 (4-5h)
- [ ] Issue #8: Módulo 05 (3-4h)
- [ ] Issue #9: Módulo 06 (inicio)
- [ ] Issue #12: Guía de Examen (paralelo)

### Post 3 días (opcional):
- [ ] Issue #9: Módulo 06 (completar)
- [ ] Issue #10: Docker
- [ ] Issue #11: CI/CD

---

# Issue #1: Estructurar el repositorio del proyecto

**Labels:** `enhancement`, `infrastructure`, `prioridad-alta`
**Asignado a:** Tú
**Dependencias:** Ninguna

## Descripción

Crear la estructura base de carpetas y archivos de configuración para el proyecto de estudio de Redes de Computadoras. Esta estructura debe ser profesional, escalable y seguir las mejores prácticas de ingeniería de software para proyectos Python educativos.

El repositorio debe organizarse de manera que soporte:
- Documentación teórica modular
- Código de práctica y ejemplos
- Ejercicios con auto-evaluación
- Herramientas de simulación
- Testing automatizado
- Material de apoyo (PDFs, recursos externos)

## Objetivos

1. Tener una estructura de carpetas clara y profesional que facilite la navegación y el aprendizaje progresivo.
2. Configurar todas las herramientas de calidad de código necesarias para mantener estándares profesionales.
3. Establecer la base para que futuros issues puedan añadir contenido sin modificar la estructura fundamental.
4. Documentar claramente la organización del proyecto para facilitar colaboración y revisión.

## Tareas

1. **Crear estructura de directorios:**
   ```bash
   mkdir -p docs/{modulos,teoria,examenes,recursos}
   mkdir -p src/redes/{ejemplos,ejercicios,simuladores,utils}
   mkdir -p tests/{test_ejemplos,test_ejercicios,test_simuladores}
   mkdir -p materiales/conferencias
   mkdir -p notas
   mv Conf/*.pdf materiales/conferencias/  # Si aplica
   ```

2. **Actualizar `pyproject.toml`:**
   - Añadir dependencias de desarrollo: `mypy`, `pytest`, `pytest-cov`, `bandit`, `ipython`, `rich`, `typer`
   - Configurar `ruff` con reglas específicas para código educativo
   - Configurar `mypy` con opciones estrictas
   - Configurar `pytest` con opciones de cobertura

3. **Actualizar `.pre-commit-config.yaml`:**
   - Hook para `ruff check` (linting)
   - Hook para `ruff format` (formatting)
   - Hook para `mypy`
   - Hook para trailing whitespace
   - Hook para end-of-file fixer
   - Hook para check-yaml

4. **Crear archivos de configuración:**
   - `.gitignore` completo (Python, IDEs, OS, venv, cache)
   - `pytest.ini` con configuración de testing
   - `mypy.ini` con opciones de type checking
   - `.editorconfig` para consistencia de editores

5. **Crear templates de GitHub:**
   - `.github/pull_request_template.md`
   - `.github/ISSUE_TEMPLATE/modulo.md` (para nuevos módulos)
   - `.github/ISSUE_TEMPLATE/ejercicio.md` (para ejercicios)
   - `.github/ISSUE_TEMPLATE/bug.md` (para bugs)

6. **Actualizar `README.md`:**
   - Descripción del proyecto y objetivos
   - Explicación detallada de la estructura de carpetas
   - Instrucciones de instalación y setup
   - Guía rápida de uso
   - Roadmap de aprendizaje

7. **Crear `CONTRIBUTING.md`:**
   - Workflow de Git (branches, commits convencionales, PRs)
   - Estándares de código y calidad
   - Cómo añadir nuevas lecciones y ejercicios
   - Proceso de revisión

8. **Crear índice maestro:**
   - `docs/00_indice_general.md` con estructura de todos los módulos
   - Tabla de progreso (para ir marcando lo completado)
   - Referencias cruzadas entre módulos

## Criterios de aceptación

- [ ] Existe la estructura completa de carpetas con todos los directorios mencionados
- [ ] `pyproject.toml` incluye todas las dependencias necesarias y configuraciones
- [ ] `.pre-commit-config.yaml` tiene al menos 6 hooks configurados y funcionales
- [ ] Existen todos los archivos de configuración mencionados (`.gitignore`, `pytest.ini`, `mypy.ini`, `.editorconfig`)
- [ ] Los templates de GitHub están creados en `.github/` y son utilizables
- [ ] `README.md` documenta claramente la estructura y cómo usar el proyecto
- [ ] `CONTRIBUTING.md` existe con guías claras
- [ ] Al ejecutar `pre-commit run --all-files` no hay errores
- [ ] Al ejecutar `pytest` el comando funciona (aunque no haya tests todavía)
- [ ] Al ejecutar `mypy src/` no hay errores de configuración
- [ ] Todos los PDFs están en `materiales/conferencias/`

## Dependencias

- Ninguna (este es el issue fundacional)

---

# Issue #2: Configurar sistema de documentación con MkDocs

**Labels:** `enhancement`, `documentation`, `infrastructure`, `prioridad-alta`
**Dependencias:** Issue #1

## Descripción

Configurar MkDocs con el tema Material para generar documentación web profesional y navegable del curso de Redes de Computadoras. Esto permitirá tener toda la teoría, ejemplos y ejercicios en un formato web moderno, con búsqueda, navegación jerárquica y sintaxis highlighting para código.

## Objetivos

1. Tener un sistema de documentación profesional que se pueda visualizar como sitio web
2. Facilitar la navegación entre módulos y temas del curso
3. Integrar código Python con sintaxis highlighting automático
4. Preparar base para potencial publicación en GitHub Pages (opcional)

## Tareas

1. **Instalar dependencias de MkDocs:**
   - Añadir a `requirements-dev.txt`:
     ```
     mkdocs>=1.5.0
     mkdocs-material>=9.5.0
     mkdocstrings[python]>=0.24.0
     pymdown-extensions>=10.7.0
     ```

2. **Crear configuración `mkdocs.yml`:**
   - Configurar nombre del proyecto: "Redes de Computadoras - Curso 2025"
   - Configurar tema Material con paleta de colores (sugerencia: azul/cyan para redes)
   - Activar extensiones útiles:
     - `codehilite` para sintaxis highlighting
     - `admonition` para bloques de notas/avisos
     - `pymdownx.superfences` para diagramas
     - `pymdownx.tabbed` para pestañas
     - `toc` para tabla de contenidos
   - Configurar navegación básica por módulos

3. **Crear estructura inicial de docs:**
   - `docs/index.md` - Página principal con introducción al curso
   - `docs/como_usar.md` - Guía de uso de la documentación
   - `docs/roadmap.md` - Mapa del curso con todos los módulos
   - `docs/modulos/README.md` - Introducción a los módulos

4. **Crear template para lecciones:**
   - `docs/templates/leccion_template.md` con estructura estándar

5. **Configurar scripts de generación:**
   - Crear `scripts/serve_docs.sh` para levantar servidor local de MkDocs
   - Crear `scripts/build_docs.sh` para generar sitio estático

6. **Documentar el sistema:**
   - Actualizar `README.md` con sección sobre cómo usar MkDocs
   - Añadir comandos básicos

## Criterios de aceptación

- [ ] `mkdocs.yml` existe y está correctamente configurado
- [ ] Las dependencias de MkDocs están en `requirements-dev.txt`
- [ ] Al ejecutar `mkdocs serve` se levanta un servidor local sin errores
- [ ] La documentación tiene un diseño profesional con el tema Material
- [ ] Existen los archivos iniciales: `index.md`, `como_usar.md`, `roadmap.md`
- [ ] El template de lección está creado y es reutilizable
- [ ] Los scripts de generación están en `scripts/` y funcionan
- [ ] La navegación lateral muestra correctamente la estructura del curso
- [ ] El código Python se muestra con sintaxis highlighting
- [ ] La documentación es navegable y tiene búsqueda funcional

---

# Issue #3: Crear Módulo 00 - Fundamentos de Redes

**Labels:** `enhancement`, `documentation`, `modulo`, `fundamentos`, `prioridad-alta`
**Dependencias:** Issue #1, Issue #2

## Descripción

Crear el primer módulo educativo que introduce los conceptos más básicos de redes de computadoras sin asumir ningún conocimiento previo. Este módulo servirá como base fundamental para todos los demás y establecerá el tono pedagógico del curso: explicaciones desde cero con analogías del mundo real.

Este módulo es crítico porque establece:
- El formato estándar que seguirán todos los módulos
- El nivel de profundidad pedagógica esperado
- La integración entre teoría, código y ejercicios
- El uso de analogías como herramienta principal

## Objetivos

1. Explicar qué es una red de computadoras usando solo lenguaje cotidiano y analogías
2. Introducir el concepto de "comunicación" entre dispositivos de forma intuitiva
3. Presentar casos de uso concretos que el estudiante reconozca inmediatamente
4. Crear el primer código ejecutable del curso: simulación simple y visual de comunicación
5. Establecer el formato estándar que seguirán todos los módulos subsecuentes
6. Validar que una persona sin conocimientos técnicos puede entender completamente el contenido

## Tareas

[Ver issue completo en descripción anterior - Issue #3]

## Criterios de aceptación

- [ ] Existe el directorio completo `docs/modulos/00_fundamentos/` con todos los archivos
- [ ] `README.md` explica todos los conceptos usando SOLO lenguaje cotidiano
- [ ] La analogía del sistema postal está completa y cubre todos los elementos
- [ ] `01_casos_de_uso.md` tiene exactamente 8-10 casos de uso bien explicados
- [ ] El archivo `comunicacion_simple.py` ejecuta sin errores
- [ ] El código usa `rich` y produce output visualmente atractivo
- [ ] El código sigue principios SOLID
- [ ] Todos los comentarios están en español y son pedagógicos
- [ ] El ejercicio es completamente realizable
- [ ] Todos los tests pasan exitosamente
- [ ] Las 10 preguntas de autoevaluación cubren todos los conceptos
- [ ] Los diagramas Mermaid se renderizan correctamente
- [ ] Una persona sin conocimientos previos puede entender todo el módulo

---

# Issues #4 - #9: Módulos 01-06

[Estos issues siguen la misma estructura que el #3, adaptados a cada capa]

**Issue #4:** Módulo 01 - Capa Física
**Issue #5:** Módulo 02 - Capa de Enlace
**Issue #6:** Módulo 03 - Capa de Red (IP)
**Issue #7:** Módulo 04 - Capa de Transporte (TCP/UDP)
**Issue #8:** Módulo 05 - Enrutamiento
**Issue #9:** Módulo 06 - Capa de Aplicación (HTTP, FTP, DNS)

[Ver descripciones completas anteriormente]

---

# Issue #10: Crear Módulo 07 - Contenedores y Docker para Redes

**Labels:** `enhancement`, `documentation`, `modulo`, `docker`, `herramientas`, `prioridad-media`
**Dependencias:** Issue #1, Issue #2

[Ver descripción completa anteriormente]

---

# Issue #11: Configurar CI/CD y automatización con GitHub Actions

**Labels:** `enhancement`, `infrastructure`, `ci-cd`, `testing`, `automation`, `prioridad-media`
**Dependencias:** Issue #1, Issue #2

[Ver descripción completa anteriormente]

---

# Issue #12: Crear Guía de Estudio y Preparación para Examen

**Labels:** `enhancement`, `documentation`, `examen`, `estudio`, `prioridad-alta`
**Dependencias:** Issues #3-9

## Descripción

Crear una guía completa de estudio que ayude a los estudiantes a prepararse efectivamente para los exámenes de Redes de Computadoras. Esta guía debe consolidar todos los módulos, proporcionar estrategias de estudio, ejercicios de repaso, exámenes de práctica y mapeo con el material oficial del curso.

[Ver descripción completa anteriormente]

---

## 🎯 Notas Importantes

### Modelos de Claude Recomendados

Para este proyecto:
- **Planificación/Diseño:** Claude Sonnet 4 (el que estás usando ahora)
- **Implementación de código:** Claude Sonnet 4 o Claude Opus 4.5
- **Documentación:** Claude Sonnet 4
- **Revisión/Testing:** Claude Sonnet 4

### Workflow Git Sugerido

```bash
# Para cada issue:
git checkout -b issue-N-nombre-descriptivo
# Trabajar...
git add .
git commit -m "feat(scope): descripción #N"
git push origin issue-N-nombre-descriptivo
# Crear PR en GitHub
# Mergear después de review
```

### Commits Convencionales

Formato: `tipo(scope): descripción #issue`

Tipos:
- `feat`: Nueva funcionalidad
- `fix`: Corrección
- `docs`: Documentación
- `test`: Tests
- `chore`: Mantenimiento
- `ci`: CI/CD

Scopes:
- `modulo-XX`: Para módulos específicos
- `infra`: Infraestructura
- `docs`: Documentación general

---

**Última actualización:** 19 Enero 2026
**Estado:** 0/12 completados
**Próximo paso:** Comenzar con Issue #1
