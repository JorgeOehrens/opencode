---
name: auth-rbac-enforcer
description: Implementar y reforzar autenticación y autorización basada en roles (RBAC) siguiendo las mejores prácticas de seguridad
---

# Skill: 07-auth-rbac-enforcer
## Propósito
Implementar y reforzar autenticación y autorización basada en roles (RBAC) siguiendo las mejores prácticas de seguridad.

## Cuándo Usar
Para cualquier feature que requiera control de acceso, login, o permisos específicos por rol.

## Inputs
- Change plan (04-change-planner)
- Stack detectado (01-repo-scanner)
- Architecture mapeada (02-architecture-mapper)

## Pasos
1. **Analizar requerimientos de seguridad**:
   - Identificar roles y permisos necesarios
   - Definir recursos protegidos
   - Mapear user flows con autenticación
   - Determinar estrategias de session management

2. **Implementar Authentication**:
   - Configurar auth provider (NextAuth, Passport, etc)
   - Implementar login/register flows
   - Configurar session management seguro
   - Implementar password hashing y validation
   - Configurar 2FA/MFA si aplica

3. **Diseñar RBAC system**:
   - Definir roles (admin, user, moderator, etc)
   - Crear permisos granulares (read, write, delete)
   - Implementar role assignment
   - Configurar role inheritance si aplica

4. **Crear middleware de autorización**:
   - Implementar guards para routes protegidos
   - Crear decorators para endpoints (NestJS)
   - Configurar route protection (Next.js middleware)
   - Implementar checks a nivel de componente

5. **Proteger API endpoints**:
   - Validar tokens en cada request
   - Implementar rate limiting
   - Configurar CORS apropiadamente
   - Validar permisos por recurso y acción

6. **Proteger frontend routes**:
   - Implementar protected routes
   - Crear auth context/provider
   - Redirección automática a login
   - Loading states durante auth check

7. **Security hardening**:
   - Implementar CSRF protection
   - Configurar security headers
   - Sanitizar todos los inputs
   - Implementar proper error handling (no info leaks)

8. **Testing de seguridad**:
   - Test authentication flows completos
   - Verificar RBAC permissions
   - Test edge cases (expired tokens, etc)
   - Security testing automatizado si aplica

## Salidas
- **Auth System**: Login/register funcionales y seguros
- **RBAC Implementation**: Roles y permisos trabajando
- **Protected Routes**: Backend y frontend seguros
- **Security Middleware**: Protección contra ataques comunes
- **Session Management**: Manejo seguro de sesiones
- **Security Tests**: Cobertura de casos de seguridad

## Guardrails
- **NUNCA** almacenar passwords en plaintext
- **SIEMPRE** validar en backend (nunca confiar en frontend)
- **USAR** tokens JWT con expiración corta
- **IMPLEMENTAR** rate limiting en endpoints sensibles
- **LOGGEAR** intentos de acceso fallidos
- **VALIDAR** todos los inputs contra XSS/SQL injection

## Comandos Típicos
```bash
# Configurar NextAuth
npm install next-auth @auth/prisma-adapter

# Crear middleware de auth
cat > middleware.ts << 'EOF'
import { withAuth } from "next-auth/middleware"
export default withAuth({ pages: { signIn: "/login" } })
EOF

# Crear guard de NestJS
cat > src/common/guards/roles.guard.ts << 'EOF'
@Injectable()
export class RolesGuard implements CanActivate {
  canActivate(context: ExecutionContext): boolean {
    // implementation
  }
}
EOF

# Testing auth flows
npm run test -- --testNamePattern="auth"

# Security audit
npm audit
```

## Definición de Done
✅ Authentication flows implementados y funcionando  
✅ RBAC system con roles y permisos definidos  
✅ Todos los endpoints protegidos apropiadamente  
✅ Frontend routes con control de acceso  
✅ Security middleware configurado  
✅ Session management seguro implementado  
✅ Tests de seguridad pasando  
✅ Security audit sin vulnerabilidades críticas