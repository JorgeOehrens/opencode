---
name: conventions-extractor
description: Extract and document all code conventions, naming patterns, and project standards
---

# Skill: 03-conventions-extractor
## Propósito
Extraer y documentar todas las convenciones de código, naming y patrones usados en el proyecto.

## Cuándo Usar
Siempre después del architecture-mapper para entender las reglas no escritas del proyecto.

## Inputs
- Código fuente existente
- Configuración de linters y formatters
- Archivos de configuración

## Pasos
1. **Analizar convenciones de naming**:
   - **Files**: kebab-case, camelCase, PascalCase
   - **Variables**: camelCase, snake_case
   - **Constants**: UPPER_SNAKE_CASE
   - **Components**: PascalCase con prefijos específicos
   - **Functions**: verbos en camelCase
   - **Types/Interfaces**: PascalCase con prefijos (I, T)

2. **Extraer patrones de estructura**:
   - **Folder organization**: por feature o por tipo
   - **Import aliases**: @/ paths configurados
   - **Index files**: barrel exports patterns
   - **File naming**: .test., .spec., .stories.

3. **Identificar patrones de código**:
   - **React**: hooks patterns, component structure
   - **TypeScript**: interface vs type, utility types
   - **Error handling**: custom errors, try/catch patterns
   - **Async patterns**: promises, async/await style
   - **State management**: context, redux, zustand patterns

4. **Extraer configuración de herramientas**:
   - **ESLint rules**: reglas específicas del proyecto
   - **Prettier config**: formatting rules
   - **TypeScript config**: strict mode, paths, targets
   - **Testing patterns**: describe/it structure, mocks

5. **Documentar convenciones de Git**:
   - **Commit messages**: convención (Conventional, etc)
   - **Branch naming**: feature/, bugfix/, hotfix/
   - **PR templates**: estructura requerida
   - **Review process**: aprobaciones necesarias

6. **Identificar patrones de negocio**:
   - **Response format**: API responses consistentes
   - **Error codes**: códigos de error estandarizados
   - **Validation patterns**: schemas y DTOs
   - **Logging patterns**: formato y niveles

## Salidas
- **Naming Convention Guide**: Reglas completas de naming
- **Code Pattern Catalog**: Patrones reutilizables
- **Tool Configuration Extract**: Configuraciones extraídas
- **Git Convention Guide**: Reglas de version control
- **Business Pattern Guide**: Patrones específicos del dominio
- **Template Examples**: Ejemplos para cada patrón

## Guardrails
- **NO inventar** convenciones que no existen
- **DOCUMENTAR** excepciones y casos especiales
- **PRESERVAR** convenciones existentes
- **CONSISTENT** con todas las reglas extraídas

## Comandos Típicos
```bash
# Analizar naming de archivos
find src -name "*.ts" -o -name "*.tsx" | head -20 | xargs -I {} basename {}

# Extraer imports patterns
grep -r "^import" src/ | head -20 | sort | uniq

# Analizar ESLint config
cat .eslintrc.js | grep -E "(rules|extends)"

# Verificar Prettier config
cat .prettierrc | jq .

# Analizar commit messages
git log --oneline -20 | head -10

# Component patterns
find src -name "*.tsx" -exec grep -l "export.*function\|export.*const.*=" {} \; | head -5
```

## Definición de Done
✅ Todas las convenciones de naming extraídas  
✅ Patrones de código identificados y documentados  
✅ Configuración de herramientas analizada  
✅ Convenciones de Git documentadas  
✅ Patrones de negocio mapeados  
✅ Templates y ejemplos creados  
✅ Guía completa de convenciones generada