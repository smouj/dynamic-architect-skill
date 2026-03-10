name: dynamic-architect
description: Arquitecto impulsado por IA para tareas de codificación, habilitando la generación automática de código, refactorización y diseño de sistemas utilizando modelos de IA avanzados y análisis contextual
tags: coding, ai, automation, architecture, generation, refactoring
version: 1.0.0
author: OpenClaw Team
dependencies: 
  - openai>=1.0.0
  - langchain>=0.1.0
  - python>=3.8
  - pydantic>=2.0.0
  - fastapi (for web architectures)
  - sqlalchemy (for database designs)
environment_variables:
  - OPENAI_API_KEY (required for AI model access)
  - DYNAMIC_ARCHITECT_MODEL (default: gpt-4, options: gpt-3.5-turbo, gpt-4-turbo)
  - DYNAMIC_ARCHITECT_MAX_TOKENS (default: 4000, max context window)
  - DYNAMIC_ARCHITECT_TEMPERATURE (default: 0.3, creativity level 0-1)
---

# Dynamic Architect Skill

## Purpose

El Dynamic Architect es un asistente de codificación impulsado por IA especializado en diseño arquitectónico y generación de código para proyectos de software. Utiliza modelos avanzados de lenguaje para crear estructuras de código escalables y mantenibles, refactorizar codebases existentes y generar componentes completos del sistema basados en requisitos en lenguaje natural.

### Casos de Uso Reales
- **Microservicios de E-commerce**: Diseñar una arquitectura completa de microservicios para una tienda en línea, incluyendo servicio de autenticación de usuario, catálogo de productos, integración de pasarela de pago y gestión de pedidos con APIs RESTful y comunicación basada en eventos.
- **Refactorización de API Fintech**: Refactorizar una aplicación bancaria monolítica en servicios modulares con diseño orientado al dominio adecuado, implementando patrones CQRS y event sourcing para el procesamiento de transacciones.
- **Generación de Dashboard IoT**: Generar un dashboard full-stack para gestión de dispositivos IoT, incluyendo visualización de datos en tiempo real, autenticación de dispositivos e integración MQTT con frontend React y backend Node.js.
- **Componentes de Motor de Juegos**: Diseñar e implementar componentes modulares para un motor de juegos 2D, incluyendo simulación física, pipeline de renderizado y arquitectura de sistema entidad-componente.
- **Automatización de Pipeline de Datos**: Crear pipelines ETL automatizados para procesamiento de big data, con integración Apache Spark, validación de esquema y dashboards de monitoreo.

## Scope

### Comandos Específicos
- `/architect design <project_type> <requirements>`: Generar arquitectura completa del sistema para el tipo de proyecto especificado con requisitos detallados
- `/architect generate <component> <specs>`: Crear componentes individuales de código con especificaciones específicas
- `/architect refactor <codebase_path> <target_pattern>`: Refactorizar código existente siguiendo patrones arquitectónicos
- `/architect analyze <file_or_path> --output=json --depth=full`: Analizar código para problemas arquitectónicos y generar recomendaciones de mejora
- `/architect testgen <module> --framework=pytest --coverage=80`: Generar suites de pruebas completas para módulos
- `/architect docs <architecture> --format=markdown`: Generar documentación para arquitecturas diseñadas
- `/architect validate <design> --against=best-practices`: Validar diseños arquitectónicos contra estándares de la industria

### Lenguajes y Frameworks Soportados
- Python (Django, FastAPI, Flask)
- JavaScript/TypeScript (React, Node.js, Express)
- Java (Spring Boot, Micronaut)
- Go (Gin, Echo)
- Rust (Actix, Rocket)
- C# (.NET Core)

### Limitaciones
- No ejecuta código ni despliega aplicaciones
- Requiere clave API válida de OpenAI para generación de IA
- Mejores resultados con requisitos detallados y específicos
- Puede requerir ajustes manuales para lógica de negocio compleja

## Detailed Work Process

1. **Análisis de Requisitos**: Analizar entrada del usuario para extraer requisitos funcionales y no funcionales, preferencias de stack tecnológico y restricciones arquitectónicas.

2. **Recopilación de Contexto**: Utilizar herramientas de búsqueda integradas para recopilar patrones de código relevantes, mejores prácticas y análisis de codebase existente si se está refactorizando.

3. **Diseño Arquitectónico**: Generar diseño de alto nivel del sistema incluyendo diagramas de componentes, flujo de datos y elecciones tecnológicas utilizando modelo de IA.

4. **Generación de Código**: Implementar código detallado para cada componente, incluyendo interfaces, clases, esquemas de base de datos y archivos de configuración.

5. **Planificación de Integración**: Diseñar contratos de API, colas de mensajes y sincronización de datos entre componentes.

6. **Fase de Validación**: Ejecutar análisis estático, verificación de tipos y linting básico en el código generado.

7. **Generación de Documentación**: Crear archivos README, documentación de API y guías de despliegue.

8. **Salida de Verificación**: Proporcionar resumen de la arquitectura generada con estructura de archivos y detalles clave de implementación.

## Golden Rules

- **Seguridad Primero**: Siempre incluir autenticación, autorización, validación de entrada y prácticas de codificación segura en el código generado.
- **Consideraciones de Escalabilidad**: Diseñar para escalado horizontal, implementar estrategias de caching y usar patrones asíncronos cuando sea apropiado.
- **Manejo de Errores**: Incluir manejo comprehensivo de errores, logging y degradación graceful en todos los componentes generados.
- **Calidad del Código**: Seguir convenciones específicas del lenguaje, implementar separación adecuada de responsabilidades y usar inyección de dependencias.
- **Integración de Pruebas**: Generar pruebas unitarias, de integración y datos mock junto con código de producción.
- **Documentación**: Incluir comentarios inline, docstrings y registros de decisiones arquitectónicas para todo el código generado.
- **Amigable con Control de Versiones**: Generar código que siga versionado semántico e incluya entradas apropiadas en .gitignore.
- **Optimización de Rendimiento**: Implementar indexación de base de datos, optimización de consultas y capas de caching automáticamente.

## Examples

### Example 1: E-commerce Microservice Design
**Input:**
```
/architect design microservices \"Build an e-commerce platform with user management, product catalog, shopping cart, and payment processing. Use Python FastAPI for APIs, PostgreSQL for database, and Redis for caching. Include JWT authentication and Stripe payment integration.\"
```

**Output:**
- Generated `architecture.md` with component diagram
- `user-service/` directory with FastAPI app, models, and tests
- `product-service/` with catalog management and search
- `cart-service/` with Redis-backed shopping cart
- `payment-service/` with Stripe integration
- Docker Compose file for local development
- API documentation in OpenAPI format

**Files Created:**
- `services/user-service/main.py`
- `services/product-service/models.py`
- `docker-compose.yml`
- `docs/architecture.md`

### Example 2: Code Refactoring
**Input:**
```
/architect refactor ./legacy-monolith --pattern=microservices --target=3-services --language=python
```

**Output:**
- Analysis report of current monolithic structure
- Proposed service boundaries with dependency graphs
- Refactored code split into `auth-service/`, `data-service/`, `api-gateway/`
- Migration scripts for database schema changes
- Updated Docker configurations

### Example 3: Component Generation
**Input:**
```
/architect generate auth-middleware \"JWT-based authentication middleware for Express.js with role-based access control, password hashing, and refresh token support\"
```

**Output:**
- `middleware/auth.js` with JWT verification
- `models/User.js` with bcrypt password hashing
- `routes/auth.js` with login/register endpoints
- `config/auth.js` with token secrets and expiration
- Unit tests in `tests/auth.test.js`

## Rollback Commands

- `/architect rollback last-generation`: Remover todos los archivos creados en la operación de generación más reciente
- `/architect rollback design <design_id>`: Revertir a versión de arquitectura anterior por ID
- `/architect undo refactor <commit_hash>`: Revertir cambios de código al commit git especificado (requiere integración git)
- `/architect clean <pattern>`: Remover archivos generados que coincidan con patrón (e.g., `*.generated.*`)

## Dependencies and Requirements

- **Required**: Clave API de OpenAI con créditos suficientes para uso de GPT-4
- **Dependencias Python**: Instalar vía `pip install openai langchain pydantic fastapi sqlalchemy redis stripe`
- **Dependencias Node.js**: `npm install express jsonwebtoken bcryptjs redis stripe`
- **Requisitos del Sistema**: Python 3.8+, Node.js 16+, Docker para despliegues containerizados
- **Límites de API**: Monitorear uso de API de OpenAI para evitar límites de tasa (recomendado: 100 requests/minute)

## Verification Steps

1. **Verificación Pre-Generación**: Ejecutar `/architect validate requirements <input>` para asegurar que los requisitos sean parseables
2. **Calidad del Código**: Ejecutar `npm run lint` o `python -m flake8` en el código generado
3. **Verificación de Tipos**: Ejecutar `npx tsc --noEmit` para TypeScript o `mypy` para Python
4. **Ejecución de Pruebas**: Ejecutar suites de pruebas generadas con `npm test` o `pytest`
5. **Prueba de Integración**: Usar Docker Compose proporcionado para iniciar servicios y probar endpoints de API
6. **Escaneo de Seguridad**: Ejecutar `npm audit` o `safety check` en dependencias

## Troubleshooting Common Issues

- **Error de Clave API**: \"Error: OPENAI_API_KEY not found\" → Establecer variable de entorno: `export OPENAI_API_KEY=your_key_here`
- **Límite de Tasa Excedido**: \"429 Too Many Requests\" → Implementar backoff exponencial o actualizar plan de OpenAI
- **Timeout de Generación**: \"Request timed out\" → Reducir `DYNAMIC_ARCHITECT_MAX_TOKENS` o simplificar requisitos
- **Requisitos Inválidos**: \"Unable to parse requirements\" → Proporcionar entrada más específica y estructurada con stack tecnológico claro
- **Errores de Compilación de Código**: \"SyntaxError in generated code\" → Verificar compatibilidad de versión del lenguaje y volver a ejecutar con `--strict-mode`
- **Conflictos de Dependencias**: \"Module not found\" → Verificar que todas las dependencias estén instaladas y versiones compatibles
- **Problemas de Memoria**: \"Out of memory\" → Reducir temperatura del modelo o dividir generaciones grandes en componentes más pequeños

## Best Practices

- Proporcionar requisitos detallados con tecnologías y restricciones específicas
- Revisar código generado antes de integrar en producción
- Usar control de versiones para rastrear cambios arquitectónicos
- Probar código generado exhaustivamente en entornos de staging
- Documentar cualquier modificación manual realizada al código generado
- Actualizar regularmente dependencias y parches de seguridad
- Monitorear métricas de rendimiento después del despliegue de sistemas generados

## Changelog

- **v1.0.0**: Lanzamiento inicial con capacidades de generación de arquitectura y refactorización de código
- **Futuro**: Características planificadas incluyen expansión de soporte multi-lenguaje, integración con plataformas cloud y scripts de despliegue automatizados