# 📋 Pull Request

## Descripción

<!-- Describe brevemente qué cambios introduce este PR -->

## Tipo de cambio

<!-- Marca con una X lo que aplique -->

- [ ] 📝 Documentación (añadir/actualizar teoría, ejemplos, ejercicios)
- [ ] ✨ Nueva funcionalidad (código, simulador, herramienta)
- [ ] 🐛 Bug fix (corrección de error)
- [ ] 🔧 Configuración/Infraestructura
- [ ] ✅ Tests
- [ ] 📚 Material de apoyo (PDFs, recursos externos)

## Issue relacionado

<!-- Si este PR cierra un issue, usa: Closes #X -->
<!-- Si está relacionado pero no lo cierra: Related to #X -->

Closes #

## Cambios realizados

<!-- Lista detallada de cambios -->

### Archivos modificados
-

### Archivos añadidos
-

### Archivos eliminados
-

## Cómo probar

<!-- Instrucciones paso a paso para probar los cambios -->

```bash
# Ejemplo:
# 1. Ejecutar el código de ejemplo:
python src/redes/ejemplos/nuevo_ejemplo.py

# 2. Ejecutar los tests:
pytest tests/test_ejemplos/test_nuevo_ejemplo.py
```

## Checklist

<!-- Marca con X las casillas que apliquen -->

### General
- [ ] El código sigue los estándares del proyecto (SOLID, nombres descriptivos, comentarios)
- [ ] He probado que el código funciona correctamente
- [ ] He actualizado la documentación si era necesario
- [ ] Los commits siguen la convención (feat:, fix:, docs:, etc.)

### Si añadiste código Python
- [ ] El código tiene docstrings explicativos
- [ ] El código pasa `ruff check src/`
- [ ] El código pasa `ruff format src/`
- [ ] El código pasa `mypy src/`
- [ ] Añadí tests si era apropiado
- [ ] Los tests pasan: `pytest`

### Si añadiste documentación
- [ ] Los conceptos se explican desde cero (sin asumir conocimientos)
- [ ] Incluye analogías de la vida real
- [ ] Los ejemplos de código son ejecutables y están probados
- [ ] La ortografía y gramática están correctas

### Si añadiste un módulo completo
- [ ] Seguí la estructura estándar de módulos
- [ ] Incluí README.md con introducción
- [ ] Incluí código de ejemplo ejecutable
- [ ] Incluí ejercicio práctico
- [ ] Incluí autoevaluación
- [ ] Actualicé el índice general (`docs/00_indice_general.md`)

## Screenshots / Output

<!-- Si aplica, añade capturas o output del código -->

```
# Output esperado del código:
...
```

## Notas adicionales

<!-- Cualquier información extra que el revisor deba saber -->

---

**Reviewer:** Por favor verifica que:
- [ ] La explicación es comprensible para alguien sin conocimientos previos
- [ ] El código es claro y educativo (no "mágico")
- [ ] Los ejemplos son realistas y útiles
