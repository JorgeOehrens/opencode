---
name: docs-release-notes
description: Generar documentación técnica y release notes para cambios implementados, asegurando conocimiento transferible
---

# Skill: 12-docs-release-notes
## Propósito
Generar documentación técnica y release notes para cambios implementados, asegurando conocimiento transferible.

## Cuándo Usar
Siempre como paso final después de completar y validar un cambio o feature.

## Inputs
- Cambios implementados y validados
- Change plan original (04-change-planner)
- Quality gate results (10-quality-gate-runner)
- Impact analysis y Dependencies afectadas

## Pasos
1. **Analizar alcance del cambio**:
   - Identificar todas las funcionalidades modificadas
   - Mapear breaking changes si existen
   - Detectar deprecated features
   - Listar new APIs o endpoints
   - Identificar cambios en database schema

2. **Generar Release Notes**:
   - **Feature Summary**: Descripción concisa del cambio
   - **User Impact**: Cómo afecta a usuarios finales
   - **Developer Impact**: Cambios para otros desarrolladores
   - **Breaking Changes**: Cambios que requieren action
   - **Migration Guide**: Pasos si se requiere migración
   - **Bug Fixes**: Issues corregidos

3. **Actualizar Technical Documentation**:
   - **API Documentation**: Actualizar OpenAPI/Swagger
   - **Component Documentation**: Storybook o component docs
   - **Database Schema**: Actualizar ER diagrams
   - **Environment Variables**: Documentar nuevas variables
   - **Setup Instructions**: Guías de instalación/configuración

4. **Crear Code Examples**:
   - **Usage Examples**: Cómo usar nuevas funcionalidades
   - **Migration Examples**: Código para transiciones
   - **Integration Examples**: Cómo integrar con otros sistemas
   - **Troubleshooting**: Common issues y soluciones

5. **Actualizar README y Guides**:
   - **Quick Start**: Instrucciones de inicio actualizadas
   - **Features List**: Catálogo de funcionalidades actual
   - **Contributing Guide**: Si aplica desarrollo abierto
   - **Changelog**: Historial de cambios estructurado

6. **Generar Knowledge Transfer**:
   - **Decision Records**: ARCs (Architecture Decision Records)
   - **Technical Debt**: Documentar deuda técnica si se creó
   - **Lessons Learned**: Insights del desarrollo
   - **Future Improvements**: Ideas para futuras iteraciones

7. **Preparar Communication Materials**:
   - **Stakeholder Update**: Resumen ejecutivo
   - **Team Communication**: Detalles técnicos para equipo
   - **User Announcement**: Comunicado para usuarios finales
   - **Marketing Copy**: Si aplica a producto

8. **Version Control Documentation**:
   - **Git Tags**: Crear tags apropiados
   - **Branch Documentation**: Documentar propósito de branches
   - **Merge Commit Messages**: Mensajes descriptivos y estructurados
   - **Pull Request Description**: Plantilla actualizada

## Salidas
- **Release Notes**: Documento de cambios para stakeholders
- **API Documentation**: Endpoints actualizados con ejemplos
- **Component Docs**: Documentación de UI components
- **Setup Guide**: Instrucciones actualizadas
- **Migration Guide**: Pasos para breaking changes
- **Knowledge Base**: Documentación técnica completa

## Guardrails
- **NUNCA** lanzar cambios sin documentación
- **SIEMPRE** incluir breaking changes prominently
- **DOCUMENTAR** APIs públicas exhaustivamente
- **MANTENER** documentación sincronizada con código
- **INCLUIR** ejemplos prácticos y funcionales
- **VERSIONAR** documentación apropiadamente

## Templates

### Release Notes Template
```markdown
# Version X.Y.Z - [Date]

## 🚀 New Features
- **[Feature Name]**: Brief description of the new functionality
- **User Impact**: How this benefits end users

## 🐛 Bug Fixes
- **Fixed**: [Issue description] - [PR #number]

## 💥 Breaking Changes
- **[Change Title]**: Description of breaking change
- **Migration**: Steps needed to update existing code
- **Example**: Code example showing migration

## 📚 Documentation Updates
- API docs updated for new endpoints
- Component examples added to Storybook

## ⚠️ Deprecations
- **[Deprecated Feature]**: Will be removed in version X.Y.0
- **Alternative**: Recommended replacement
```

### API Documentation Template
```typescript
/**
 * Creates a new user in the system
 * 
 * @route POST /api/users
 * @access Private (admin only)
 * @param {CreateUserDto} userData - User creation data
 * @returns {Promise<User>} Created user object
 * @throws {401} Unauthorized - Invalid admin token
 * @throws {400} Bad Request - Invalid user data
 * @throws {409} Conflict - User already exists
 * 
 * @example
 * ```typescript
 * const user = await userService.createUser({
 *   email: 'user@example.com',
 *   name: 'John Doe',
 *   role: 'user'
 * });
 * ```
 */
```

### Component Documentation Template
```typescript
/**
 * Button component with multiple variants and sizes
 * 
 * @example
 * ```tsx
 * <Button variant="primary" size="lg" onClick={handleClick}>
 *   Click me
 * </Button>
 * ```
 * 
 * @param {ButtonProps} props
 * @param {string} props.children - Button content
 * @param {'primary'|'secondary'} props.variant - Visual style
 * @param {'sm'|'md'|'lg'} props.size - Button size
 * @param {boolean} props.disabled - Disable interaction
 * @param {() => void} props.onClick - Click handler
 */
```

## Comandos Típicos
```bash
# Generar API docs
npm run docs:api
npx swagger-jsdoc src/**/*.ts -o docs/api.json

# Component docs (Storybook)
npm run storybook:build

# Changelog automático
npx conventional-changelog -p angular -i CHANGELOG.md -s

# Version tags
git tag -a v1.2.3 -m "Release version 1.2.3"
git push origin v1.2.3

# Documentation deployment
npm run docs:deploy
```

## Definición de Done
✅ Release notes completas y claras generadas  
✅ Breaking changes documentados con guía de migración  
✅ API documentation actualizada con ejemplos  
✅ Component documentation actualizada  
✅ README y guías actualizadas  
✅ Ejemplos de uso funcionando  
✅ Knowledge transfer documentado  
✅ Version control tags creados  
✅ Communication materials preparados