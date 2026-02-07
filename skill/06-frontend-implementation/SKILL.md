---
name: frontend-implementation
description: Implementar funcionalidades frontend siguiendo patrones de React/Next.js y convenciones del proyecto
---

# Skill: 06-frontend-implementation
## Propósito
Implementar funcionalidades frontend siguiendo patrones de React/Next.js y convenciones del proyecto.

## Cuándo Usar
Para crear components, pages, hooks o cualquier funcionalidad frontend de usuario.

## Inputs
- Change plan (04-change-planner)
- Architecture mapeada (02-architecture-mapper)
- Convenciones extraídas (03-conventions-extractor)

## Pasos
1. **Analizar requerimiento UI**:
   - Descomponer UI en components reutilizables
   - Identificar state management necesario
   - Definir data fetching strategy
   - Plan responsive design approach

2. **Crear estructura de components**:
   - Seguir convención de nombres y carpetas
   - Crear components atómicos y compuestos
   - Implementar TypeScript interfaces para props
   - Configurar barrel exports para el module

3. **Implementar hooks personalizados**:
   - Separar lógica de negocio de components
   - Crear hooks para data fetching
   - Implementar caching strategies
   - Manejar loading y error states

4. **Implementar pages/routes**:
   - Crear pages según routing convention
   - Implementar SEO metadata
   - Configurar loading y error boundaries
   - Optimizar para SSR/SSG cuando aplique

5. **State management**:
   - Usar Context API para estado global simple
   - Implementar Zustand/Redux para estado complejo
   - Separar estado de UI vs estado de negocio
   - Optimizar re-renders con memo/useMemo

6. **Styling y responsive design**:
   - Seguir convención Tailwind/shadcn-ui
   - Implementar mobile-first approach
   - Crear variantes y themes consistentes
   - Optimizar para performance y accesibilidad

7. **Formularios y validación**:
   - Implementar con React Hook Form/Zod
   - Validación en cliente y servidor
   - Manejo de errores y submit states
   - Accesibilidad con proper labels

8. **Testing frontend**:
   - Unit tests para hooks y utils
   - Component tests con React Testing Library
   - E2E tests para user flows críticos
   - Visual regression tests si aplica

## Salidas
- **UI Components**: Components reutilizables y tipados
- **Pages/Routes**: Páginas funcionales con SEO
- **Custom Hooks**: Lógica separada y reusable
- **State Management**: Estado gestionado eficientemente
- **Forms**: Formularios validados y accesibles
- **Test Suite**: Coverage completo para frontend

## Guardrails
- **SIEMPRE** tipar todas las props
- **NUNCA** mezclar lógica de negocio con UI
- **IMPLEMENTAR** loading y error states
- **SEGUIR** patrones de accesibilidad WCAG
- **OPTIMIZAR** para performance desde el inicio

## Comandos Típicos
```bash
# Crear component template
mkdir -p src/components/ui
cat > src/components/ui/{Component}.tsx << 'EOF'
interface {Component}Props {
  // prop definitions
}

export function {Component}({}: {Component}Props) {
  return <div>Component content</div>
}
EOF

# Crear hook personalizado
cat > src/hooks/use{Hook}.ts << 'EOF'
export function use{Hook}() {
  // hook implementation
}
EOF

# Crear page
cat > src/app/{route}/page.tsx << 'EOF'
export default function {Page}() {
  return <div>Page content</div>
}
EOF

# Testing components
npm run test -- src/components/{Component}

# Type checking frontend
npm run typecheck

# Build verification
npm run build
```

## Definición de Done
✅ Todos los components implementados y funcionando  
✅ Pages creadas con routing correcto  
✅ State management implementado eficientemente  
✅ Forms validados y accesibles  
✅ Responsive design implementado  
✅ Tests unitarios y de integración pasando  
✅ Performance optimizada  
✅ Quality gate superado sin warnings