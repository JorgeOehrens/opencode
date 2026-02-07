---
name: backend-implementation
description: Implementar funcionalidades backend siguiendo patrones arquitectónicos y convenciones del proyecto
---

# Skill: 05-backend-implementation
## Propósito
Implementar funcionalidades backend siguiendo patrones arquitectónicos y convenciones del proyecto.

## Cuándo Usar
Para crear nuevos endpoints, servicios, lógica de negocio o cualquier funcionalidad backend.

## Inputs
- Change plan (04-change-planner)
- Architecture mapeada (02-architecture-mapper) 
- Convenciones extraídas (03-conventions-extractor)

## Pasos
1. **Preparar estructura base**:
   - Crear/radicar carpetas según convención
   - Setup de módulo o feature siguiendo patrón
   - Crear barrel exports si corresponde
   - Configurar rutas base en router principal

2. **Implementar DTOs y validación**:
   - Crear interfaces para request/response
   - Configurar validación con class-validator/zod
   - Definir tipos de error personalizados
   - Documentar schemas para API docs

3. **Implementar Services layer**:
   - Crear service con inyección de dependencias
   - Implementar lógica de negocio pura
   - Manejar errores con consistent responses
   - Logging apropiado para debugging

4. **Crear/actualizar Controllers**:
   - Implementar endpoints con verbos HTTP correctos
   - Validar request con DTOs
   - Manejar responses con status codes apropiados
   - Middleware para auth, rate limiting si aplica

5. **Implementar Repository layer**:
   - Crear repository para acceso a datos
   - Queries optimizadas con indexes
   - Transactions para operaciones complejas
   - Error handling de base de datos

6. **Configurar Middleware y Guards**:
   - Authentication/authorization checks
   - Request validation middleware
   - Error handling global
   - CORS y security headers

7. **Testing backend implementation**:
   - Unit tests para services y repositories
   - Integration tests para endpoints
   - Mocks para external dependencies
   - Test coverage para nuevo código

## Salidas
- **Backend Features**: Endpoints funcionales
- **Business Logic**: Services con lógica implementada
- **Data Access**: Repositories con queries optimizadas
- **API Documentation**: OpenAPI/Swagger actualizado
- **Test Suite**: Tests automatizados para nuevo código
- **Error Handling**: Responses consistentes y logging

## Guardrails
- **NUNCA** exponer información sensible en responses
- **SIEMPRE** validar inputs en boundary layer
- **USAR** inyección de dependencias correctamente
- **MANEJAR** todos los casos de error
- **SEGUIR** patrones RESTful consistentes

## Comandos Típicos
```bash
# Crear estructura de módulo
mkdir -p src/modules/{feature}/{controllers,services,repositories,dto}

# Generar DTO con validación
echo "export class Create{Feature}Dto {}" > src/modules/{feature}/dto/create-{feature}.dto.ts

# Implementar service template
cat > src/modules/{feature}/services/{feature}.service.ts << 'EOF'
@Injectable()
export class {Feature}Service {
  constructor() {}
}
EOF

# Testing
npm run test -- src/modules/{feature} --watch

# Type checking
npm run typecheck

# Build verification
npm run build
```

## Definición de Done
✅ Todos los endpoints implementados funcionando  
✅ Lógica de negocio separada en services  
✅ DTOs con validación completa  
✅ Error handling consistente implementado  
✅ Repositories con queries optimizadas  
✅ Tests unitarios y de integración pasando  
✅ API documentation actualizada  
✅ Quality gate superado sin errores