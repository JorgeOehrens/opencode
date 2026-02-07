---
name: repo-scanner
description: Automatically detect the real technology stack and base structure of the project
---

# Skill: 01-repo-scanner
## Propósito
Detectar automáticamente el stack tecnológico real del proyecto y su estructura base.

## Cuándo Usar
Siempre como primer skill en cualquier interacción, antes de tomar decisiones técnicas.

## Inputs
- Ruta del repositorio (directorio actual por defecto)
- Archivos de configuración existentes

## Pasos
1. **Escanear archivos de configuración clave**:
   - package.json (dependencias y scripts)
   - tsconfig.json (configuración TypeScript)
   - next.config.js/nuxt.config.js (framework frontend)
   - nest-cli.json (framework backend)
   - tailwind.config.js (styling)
   - prisma/schema.prisma o drizzle.config.ts (ORM)
   - vitest.config.js/jest.config.js (testing)

2. **Analizar estructura de carpetas**:
   - src/ o lib/ (código fuente)
   - components/ o ui/ (componentes frontend)
   - pages/ o app/ (routing)
   - services/ o controllers/ (backend)
   - tests/ o __tests__/ (pruebas)
   - docs/ (documentación)

3. **Detectar package manager**:
   - pnpm-lock.yaml → pnpm
   - yarn.lock → yarn
   - package-lock.json → npm

4. **Identificar CI/CD**:
   - .github/workflows/ (GitHub Actions)
   - .gitlab-ci.yml (GitLab CI)
   - Dockerfile (containerización)

5. **Mapear tecnologías específicas**:
   - Framework: Next.js, NestJS, Express, Fastify
   - DB: Prisma, Drizzle, TypeORM, Supabase
   - Auth: NextAuth, Passport, Auth0
   - Styling: Tailwind, Styled Components, Emotion
   - Testing: Vitest, Jest, Playwright, Cypress

## Salidas
- **Stack detectado**: Lista de tecnologías confirmadas
- **Estructura del proyecto**: Mapa de carpetas clave
- **Package manager**: Herramienta a usar
- **Scripts disponibles**: Comandos ejecutables
- **Convenciones iniciales**: Patrones estructurales detectados

## Guardrails
- **NO asumir** tecnologías sin evidencia en archivos
- **NO modificar** ningún archivo durante scanning
- **DOCUMENTAR** cualquier ambigüedad detectada
- **VERIFICAR** múltiples fuentes para confirmar stack

## Comandos Típicos
```bash
# Detección básica
find . -name "package.json" -o -name "tsconfig.json" -o -name "*.config.*" | head -20

# Análisis de dependencias
cat package.json | jq '.dependencies, .devDependencies'

# Estructura de carpetas
find . -type d -name "src" -o -name "lib" -o -name "components" | head -10

# Package manager detection
ls -la | grep -E "(pnpm-lock|yarn.lock|package-lock)"
```

## Definición de Done
✅ Stack tecnológico identificado con 100% certeza  
✅ Estructura de proyecto mapeada completamente  
✅ Package manager detectado y confirmado  
✅ Scripts relevantes identificados  
✅ Archivos clave localizados y catalogados  
✅ Ambigüedades documentadas (si existen)