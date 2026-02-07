---
name: architecture-mapper
description: Create comprehensive project architecture mapping identifying modules, dependencies, and data flow
---

# Skill: 02-architecture-mapper
## Propósito
Crear un mapa completo de la arquitectura del proyecto, identificando módulos, dependencias y flujo de datos.

## Cuándo Usar
Después del repo-scanner para proyectos nuevos o cuando necesites entender la arquitectura existente profundamente.

## Inputs
- Stack detectado por 01-repo-scanner
- Código fuente existente
- Archivos de configuración

## Pasos
1. **Mapear estructura de capas**:
   - **Presentation**: Components, pages, controllers, routes
   - **Business Logic**: Services, use cases, domain models
   - **Data Access**: Repositories, models, schemas
   - **Infrastructure**: DB, external APIs, utilities

2. **Identificar módulos y bounded contexts**:
   - Agrupar archivos por dominio funcional
   - Detectar frontend vs backend separation
   - Mapear shared modules y utilities

3. **Analizar flujo de datos**:
   - Request → Controller → Service → Repository → DB
   - UI Events → State Management → API Calls
   - Real-time connections y websockets

4. **Documentar patrones arquitectónicos**:
   - **Clean Architecture**: Dependencias invertidas
   - **MVC/MVVM**: Separation de concerns
   - **Microservices**: Service boundaries
   - **Monolith**: Module organization

5. **Mapear integraciones externas**:
   - APIs de terceros
   - Base de datos y ORMs
   - Authentication providers
   - File storage y CDNs
   - Message queues o eventos

6. **Identificar configuración y environment**:
   - Variables de entorno
   - Configuración por staging
   - Feature flags o toggles

## Salidas
- **Architecture Diagram**: Mapa visual de componentes
- **Module Matrix**: Relaciones entre módulos
- **Data Flow**: Flujo completo de información
- **Integration Points**: Conexiones externas
- **Pattern Catalog**: Patrones identificados
- **Environment Map**: Configuración y secrets

## Guardrails
- **NO modificar** arquitectura existente sin requerimiento
- **RESPECTAR** boundaries existentes entre módulos
- **DOCUMENTAR** every architectural decision
- **VALIDAR** que el mapeo refleje la realidad actual

## Comandos Típicos
```bash
# Análisis de importaciones
find src -name "*.ts" -o -name "*.tsx" | xargs grep "^import" | head -20

# Mapeo de estructura
tree src -I node_modules --dirsfirst

# Análisis de dependencias
npx madge --circular src/

# Backend structure
find src -type f -name "*.ts" | grep -E "(controller|service|repository)" | sort

# Frontend components
find src -name "*.tsx" | grep -E "(component|page)" | sort
```

## Definición de Done
✅ Todas las capas arquitectónicas identificadas  
✅ Módulos y bounded contexts mapeados  
✅ Flujo de datos documentado completamente  
✅ Patrones arquitectónicos catalogados  
✅ Integraciones externas identificadas  
✅ Configuración y environments mapeados  
✅ Relaciones entre componentes documentadas