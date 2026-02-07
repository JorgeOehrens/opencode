---
name: quality-gate-runner
description: Ejecutar validaciones automáticas de calidad para asegurar que el código cumple con todos los estándares del proyecto
---

# Skill: 10-quality-gate-runner
## Propósito
Ejecutar validaciones automáticas de calidad para asegurar que el código cumple con todos los estándares del proyecto.

## Cuándo Usar
Siempre como último paso antes de finalizar cualquier tarea o commit.

## Inputs
- Código modificado recientemente
- Quality gate configuration (quality-gate.md)
- Scripts disponibles en package.json

## Pasos
1. **Detectar package manager y scripts**:
   - Identificar npm/yarn/pnpm disponible
   - Mapear scripts de quality gate
   - Verificar herramientas de linting/formatting
   - Detectar testing framework configurado

2. **Ejecutar Type Checking**:
   - Correr `typecheck` o `tsc --noEmit`
   - Analizar errores de TypeScript
   - Verificar configuración strict mode
   - Revisar imports y dependencias

3. **Ejecutar Linting**:
   - Correr `lint` con ESLint configurado
   - Analizar warnings y errors
   - Revisar reglas de seguridad específicas
   - Verificar naming conventions

4. **Validar Formatting**:
   - Correr `format:check` con Prettier
   - Detectar inconsistencias de formato
   - Verificar indentation y line endings
   - Revisar quote styles consistentes

5. **Ejecutar Testing Suite**:
   - Correr `test` para unit tests
   - Ejecutar `test:coverage` si está disponible
   - Verificar coverage thresholds
   - Revisar tests que fallan

6. **Validar Build Process**:
   - Correr `build` para producción
   - Detectar errores de compilación
   - Verificar bundle generation
   - Revisar assets optimization

7. **Security Validation**:
   - Correr `npm audit` para vulnerabilidades
   - Revisar hardcoded secrets
   - Validar input sanitization
   - Verificar dependencies actualizadas

8. **Performance Checks**:
   - Analizar bundle size si aplica
   - Revisar database queries ineficientes
   - Detectar memory leaks potenciales
   - Verificar lazy loading apropiado

9. **Generar Quality Report**:
   - Compilar resultados de todas las validaciones
   - Identificar blockers críticos
   - Generar lista de warnings
   - Crear actionable recommendations

## Salidas
- **Quality Status**: Pass/Fail con detalles
- **Error Report**: Lista de issues críticos
- **Warning List**: Mejoras recomendadas
- **Coverage Metrics**: Porcentajes de cobertura
- **Security Audit**: Vulnerabilidades detectadas
- **Performance Metrics**: Indicadores de rendimiento

## Guardrails
- **NUNCA** ignorar errores de TypeScript
- **SIEMPRE** corregir issues de seguridad críticas
- **BLOQUEAR** commits con tests que fallan
- **REQUERIR** coverage mínimo establecido
- **VALIDAR** every change antes de merge

## Comandos Típicos
```bash
# Detecar package manager
if [ -f "pnpm-lock.yaml" ]; then PM="pnpm"; elif [ -f "yarn.lock" ]; then PM="yarn"; else PM="npm"; fi

# Quality gate completo
$PM run typecheck && $PM run lint && $PM run format:check && $PM run test && $PM run build

# Coverage analysis
$PM run test:coverage

# Security audit
$PM audit --audit-level moderate

# Type checking detallado
npx tsc --noEmit --pretty

# Lint con auto-fix no-destructivo
$PM run lint --fix --quiet
```

## Troubleshooting Común

### TypeScript Errors
```bash
# Diagnostic detallado
npx tsc --noEmit --extendedDiagnostics

# Revisar configuración
cat tsconfig.json | jq .
```

### ESLint Issues
```bash
# Ver reglas específicas
npx eslint . --ext .ts,.tsx --rule "no-console: error"

# Auto-fix seguro
$PM run lint:fix
```

### Test Failures
```bash
# Debug específico
$PM run test -- --reporter=verbose --runInBand

# Coverage detallado
$PM run test:coverage -- --reporter=text
```

### Build Issues
```bash
# Verbose build
$PM run build -- --verbose

# Clean build
rm -rf .next dist node_modules/.cache
$PM install
$PM run build
```

## Definición de Done
✅ TypeScript type checking sin errores  
✅ ESLint aprobado (0 errors)  
✅ Prettier formatting validado  
✅ Todos los tests pasando  
✅ Build exitoso sin warnings  
✅ Security audit limpio  
✅ Coverage thresholds cumplidos  
✅ Performance metrics aceptables  
✅ Quality report generado y aprobado