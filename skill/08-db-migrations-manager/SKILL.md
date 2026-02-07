---
name: db-migrations-manager
description: Gestionar migraciones de base de datos de forma segura y versionada, asegurando consistencia de datos
---

# Skill: 08-db-migrations-manager
## Propósito
Gestionar migraciones de base de datos de forma segura y versionada, asegurando consistencia de datos.

## Cuándo Usar
Para cualquier cambio en el schema de base de datos: nuevas tablas, modificaciones, índices, o cambios de datos.

## Inputs
- Change plan (04-change-planner)
- ORM detectado (Prisma/Drizzle/TypeORM)
- Schema actual de base de datos

## Pasos
1. **Analizar requerimientos de schema**:
   - Identificar tablas nuevas a crear
   - Detectar cambios en tablas existentes
   - Planear índices y constraints necesarios
   - Evaluar impacto en datos existentes

2. **Diseñar migración segura**:
   - **Forward migration**: cambios aplicables
   - **Rollback migration**: reversión segura
   - **Data migration**: mover/transformar datos
   - **Performance impact**: tiempo de ejecución

3. **Crear archivo de migración**:
   - Seguir convención de nombres del ORM
   - Incluir schema changes y data changes
   - Añadir rollback commands
   - Documentar propósito y impacto

4. **Validar SQL generado**:
   - Revisar queries generadas
   - Verificar foreign key constraints
   - Chequear índices apropiados
   - Validar tipos de datos

5. **Testing de migración**:
   - Test en ambiente de desarrollo
   - Verificar rollback functionality
   - Test con datos reales (sample)
   - Performance testing si es large migration

6. **Ejecutar migración**:
   - Backup de base de datos (producción)
   - Ejecutar migration script
   - Verificar cambios aplicados
   - Validar integridad de datos

7. **Actualizar application code**:
   - Regenerar tipos del ORM
   - Actualizar modelos y entidades
   - Modificar queries afectadas
   - Actualizar DTOs y validación

8. **Documentar cambios**:
   - Actualizar schema documentation
   - Documentar breaking changes
   - Añadir notas para deploy
   - Actualizar ER diagram si aplica

## Salidas
- **Migration Files**: Scripts forward y rollback
- **Updated Schema**: Base de datos actualizada
- **Generated Types**: Tipos actualizados del ORM
- **Documentation**: Cambios documentados
- **Test Results**: Validación de migración exitosa
- **Rollback Plan**: Estrategia de reversión lista

## Guardrails
- **NUNCA** ejecutar migraciones en producción sin backup
- **SIEMPRE** testear rollback antes de aplicar
- **USAR** transacciones para cambios atómicos
- **EVITAR** migraciones destructivas (preferir renombrar)
- **MONITOREAR** performance en tablas grandes
- **DOCUMENTAR** cada cambio de schema

## Comandos Típicos
```bash
# Prisma
npx prisma migrate dev --name migration_name
npx prisma migrate deploy
npx prisma generate

# Drizzle
npm run db:generate
npm run db:migrate
npm run db:push

# TypeORM
npm run typeorm migration:generate -- -n MigrationName
npm run typeorm migration:run
npm run typeorm migration:revert

# Verificar schema
npx prisma db pull
npm run db:diff

# Testing migration local
docker-compose down -v && docker-compose up -d db
npm run db:migrate
```

## Definición de Done
✅ Migration files creados con rollback  
✅ Schema changes aplicados exitosamente  
✅ Datos existentes preservados intactos  
✅ Tipos del ORM regenerados  
✅ Queries actualizadas funcionando  
✅ Tests de migración pasando  
✅ Documentación actualizada  
✅ Backup confirmado (producción)  
✅ Performance impact aceptable