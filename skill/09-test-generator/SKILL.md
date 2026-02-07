---
name: test-generator
description: Generar suites de tests completos (unit, integration, E2E) siguiendo las convenciones del proyecto
---

# Skill: 09-test-generator
## Propósito
Generar suites de tests completos (unit, integration, E2E) siguiendo las convenciones del proyecto.

## Cuándo Usar
Siempre después de implementar nueva funcionalidad o modificar código existente.

## Inputs
- Código implementado recientemente
- Testing framework detectado (Vitest/Jest/Playwright)
- Convenciones de testing del proyecto

## Pasos
1. **Analizar código a testear**:
   - Identificar functions, components, endpoints nuevos
   - Detectar casos edge y boundary conditions
   - Mapear dependencies externas a mockear
   - Evaluar complejidad ciclomática

2. **Generar unit tests**:
   - **Functions**: Test happy path, error cases, edge cases
   - **Components**: Renderizado, props, user interactions
   - **Hooks**: State changes, effects, error handling
   - **Services**: Business logic, error handling, dependencies

3. **Crear integration tests**:
   - **API endpoints**: Request/response, validation, errors
   - **Database operations**: CRUD, transactions, constraints
   - **External services**: API calls, error handling, retries
   - **Authentication**: Login flows, permissions, tokens

4. **Implementar E2E tests**:
   - **User flows**: Journeys completos del usuario
   - **Critical paths**: Features principales del negocio
   - **Cross-browser**: Chrome, Firefox, Safari
   - **Mobile**: Responsive design y touch interactions

5. **Configurar mocks y fixtures**:
   - Mock de APIs externas
   - Database fixtures para tests
   - User personas para testing
   - Test data factories

6. **Setup testing utilities**:
   - Helper functions comunes
   - Custom matchers y assertions
   - Test environment configuration
   - Coverage exclusions y thresholds

7. **Generar performance tests**:
   - Load testing para APIs críticas
   - Memory leak detection
   - Bundle size monitoring
   - Rendering performance

## Salidas
- **Unit Test Suite**: Tests para functions y components
- **Integration Tests**: Tests para APIs y database
- **E2E Test Suite**: User journeys automatizados
- **Mock Utilities**: Factories y helpers reutilizables
- **Coverage Report**: Métricas de cobertura detalladas
- **Performance Benchmarks**: Tests de rendimiento

## Guardrails
- **NUNCA** testear implementation details
- **SIEMPRE** testear behavior esperado
- **MOCKEAR** solo dependencies externas
- **MANTENER** tests independent y isolated
- **EVITAR** test coverage frágil (brittle)
- **ASEGURAR** tests reproducibles

## Comandos Típicos
```bash
# Generar tests unitarios
npm run test -- --coverage src/modules/new-feature

# E2E tests
npm run test:e2e

# Tests específicos
npm run test -- --testNamePattern="ComponentName"

# Watch mode para desarrollo
npm run test -- --watch src/components/

# Coverage report
npm run test:coverage -- --reporter=text-summary

# Debug tests
npm run test -- --runInBand --detectOpenHandles
```

## Templates de Tests

### Unit Test (Vitest/Jest)
```typescript
describe('FunctionName', () => {
  it('should return expected result for valid input', () => {
    // Arrange
    const input = {}
    
    // Act
    const result = functionName(input)
    
    // Assert
    expect(result).toEqual(expected)
  })
})
```

### Component Test (RTL)
```typescript
describe('ComponentName', () => {
  it('should render with default props', () => {
    render(<ComponentName />)
    expect(screen.getByRole('button')).toBeInTheDocument()
  })
  
  it('should handle user interaction', async () => {
    const user = userEvent.setup()
    render(<ComponentName />)
    
    await user.click(screen.getByRole('button'))
    expect(mockFunction).toHaveBeenCalled()
  })
})
```

### API Test (Supertest)
```typescript
describe('POST /api/endpoint', () => {
  it('should return 201 for valid request', async () => {
    const response = await request(app)
      .post('/api/endpoint')
      .send(validData)
      .expect(201)
      
    expect(response.body).toEqual(expectedResponse)
  })
})
```

## Definición de Done
✅ Unit tests para todo nuevo código creado  
✅ Integration tests para APIs y database operations  
✅ E2E tests para user flows críticos  
✅ Coverage ≥ 80% en archivos modificados  
✅ Todos los tests pasando consistentemente  
✅ Mocks y fixtures configurados  
✅ Tests independientes y reproducibles  
✅ Performance tests para features críticas