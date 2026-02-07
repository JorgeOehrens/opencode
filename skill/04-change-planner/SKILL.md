---
name: change-planner
description: Planificar cambios complejos descomponiéndolos en tareas manejables y validando impacto
---

# Skill: 04-change-planner
## Propósito
Planificar cambios complejos descomponiéndolos en tareas manejables y validando impacto.

## Cuándo Usar
Para features complejos, refactorings grandes, o cualquier cambio que afecte múltiples componentes.

## Inputs
- Requerimiento del usuario
- Arquitectura mapeada (02-architecture-mapper)
- Convenciones extraídas (03-conventions-extractor)
- Stack detectado (01-repo-scanner)

## Pasos
1. **Analizar el requerimiento**:
   - Descomponer en componentes funcionales
   - Identificar dependencies internas y externas
   - Definir criterios de aceptación
   - Estimar complejidad y riesgo

2. **Mapear impacto**:
   - **Frontend**: Components, pages, routing, state
   - **Backend**: Controllers, services, database schema
   - **Shared**: Types, utilities, constants
   - **Tests**: Unit, integration, E2E tests
   - **Documentation**: API docs, README, comments

3. **Crear plan de implementación**:
   - **Phase 1**: Preparación y setup
   - **Phase 2**: Core functionality  
   - **Phase 3**: Integration y testing
   - **Phase 4**: Polish y documentation

4. **Identificar blockers y riesgos**:
   - Dependencies externas no controladas
   - Cambios breaking en APIs
   - Migraciones de base de datos complejas
   - Features flags necesarios

5. **Definir estrategia de testing**:
   - Unit tests para nueva lógica
   - Integration tests para endpoints
   - E2E tests para user flows
   - Performance tests si aplica

6. **Planificar quality gate**:
   - Type checking checkpoints
   - Lint validation en cada fase
   - Code review requirements
   - Automated testing pipeline

## Salidas
- **Implementation Plan**: Fases detalladas con tareas
- **Impact Analysis**: Componentes afectados y riesgo
- **Risk Assessment**: Blockers y estrategias de mitigación
- **Test Strategy**: Qué y cómo testear
- **Dependencies Map**: Qué se necesita primero
- **Timeline Estimate**: Duración estimada por fase

## Guardrails
- **NO subestimar** impacto de cambios aparentemente pequeños
- **SIEMPRE incluir** testing en el plan
- **CONSIDERAR** backward compatibility
- **DOCUMENTAR** suposiciones y riesgos

## Comandos Típicos
```bash
# Análisis de impacto en archivos
grep -r "functionName\|componentName" src/ --include="*.ts" --include="*.tsx"

# Verificar dependencias
cat package.json | jq '.dependencies'

# Analizar tests existentes
find . -name "*.test.*" -o -name "*.spec.*" | head -10

# Revisión de schema DB
cat prisma/schema.prisma | grep -E "(model|enum)"

# Detectar importaciones cruzadas
npx madge --circular src/

# Historial de cambios relacionados
git log --oneline --grep="keyword" --all
```

## Definición de Done
✅ Requerimiento completamente descompuesto  
✅ Impacto analizado y documentado  
✅ Plan de implementación detallado creado  
✅ Riesgos identificados con mitigación  
✅ Estrategia de testing definida  
✅ Quality gate planificado  
✅ Timeline y dependencias mapeadas  
✅ Aprobación del plan por el usuario