name: dynamic-architect
description: AI-powered architect for coding tasks, enabling automated code generation, refactoring, and system design using advanced AI models and contextual analysis
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

The Dynamic Architect is an AI-powered coding assistant specializing in architectural design and code generation for software projects. It leverages advanced language models to create scalable, maintainable code structures, refactor existing codebases, and generate complete system components based on natural language requirements.

### Real Use Cases
- **E-commerce Microservices**: Design a complete microservice architecture for an online store, including user auth service, product catalog, payment gateway integration, and order management with RESTful APIs and event-driven communication.
- **Fintech API Refactoring**: Refactor a monolithic banking application into modular services with proper domain-driven design, implementing CQRS patterns and event sourcing for transaction processing.
- **IoT Dashboard Generation**: Generate a full-stack dashboard for IoT device management, including real-time data visualization, device authentication, and MQTT integration with React frontend and Node.js backend.
- **Game Engine Components**: Design and implement modular components for a 2D game engine, including physics simulation, rendering pipeline, and entity-component system architecture.
- **Data Pipeline Automation**: Create automated ETL pipelines for big data processing, with Apache Spark integration, schema validation, and monitoring dashboards.

## Scope

### Specific Commands
- `/architect design <project_type> <requirements>`: Generate complete system architecture for specified project type with detailed requirements
- `/architect generate <component> <specs>`: Create individual code components with specific specifications
- `/architect refactor <codebase_path> <target_pattern>`: Refactor existing code following architectural patterns
- `/architect analyze <file_or_path> --output=json --depth=full`: Analyze code for architectural issues and generate improvement recommendations
- `/architect testgen <module> --framework=pytest --coverage=80`: Generate comprehensive test suites for modules
- `/architect docs <architecture> --format=markdown`: Generate documentation for designed architectures
- `/architect validate <design> --against=best-practices`: Validate architectural designs against industry standards

### Supported Languages and Frameworks
- Python (Django, FastAPI, Flask)
- JavaScript/TypeScript (React, Node.js, Express)
- Java (Spring Boot, Micronaut)
- Go (Gin, Echo)
- Rust (Actix, Rocket)
- C# (.NET Core)

### Limitations
- Does not execute code or deploy applications
- Requires valid OpenAI API key for AI generation
- Best results with detailed, specific requirements
- May require manual adjustments for complex business logic

## Detailed Work Process

1. **Requirement Analysis**: Parse user input to extract functional and non-functional requirements, technology stack preferences, and architectural constraints.

2. **Context Gathering**: Use built-in search tools to gather relevant code patterns, best practices, and existing codebase analysis if refactoring.

3. **Architecture Design**: Generate high-level system design including component diagrams, data flow, and technology choices using AI model.

4. **Code Generation**: Implement detailed code for each component, including interfaces, classes, database schemas, and configuration files.

5. **Integration Planning**: Design API contracts, message queues, and data synchronization between components.

6. **Validation Phase**: Run static analysis, type checking, and basic linting on generated code.

7. **Documentation Generation**: Create README files, API documentation, and deployment guides.

8. **Verification Output**: Provide summary of generated architecture with file structure and key implementation details.

## Golden Rules

- **Security First**: Always include authentication, authorization, input validation, and secure coding practices in generated code.
- **Scalability Considerations**: Design for horizontal scaling, implement caching strategies, and use asynchronous patterns where appropriate.
- **Error Handling**: Include comprehensive error handling, logging, and graceful degradation in all generated components.
- **Code Quality**: Follow language-specific conventions, implement proper separation of concerns, and use dependency injection.
- **Testing Integration**: Generate unit tests, integration tests, and mock data alongside production code.
- **Documentation**: Include inline comments, docstrings, and architectural decision records for all generated code.
- **Version Control Friendly**: Generate code that follows semantic versioning and includes proper .gitignore entries.
- **Performance Optimization**: Implement database indexing, query optimization, and caching layers automatically.

## Examples

### Example 1: E-commerce Microservice Design
**Input:**
```
/architect design microservices "Build an e-commerce platform with user management, product catalog, shopping cart, and payment processing. Use Python FastAPI for APIs, PostgreSQL for database, and Redis for caching. Include JWT authentication and Stripe payment integration."
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
/architect generate auth-middleware "JWT-based authentication middleware for Express.js with role-based access control, password hashing, and refresh token support"
```

**Output:**
- `middleware/auth.js` with JWT verification
- `models/User.js` with bcrypt password hashing
- `routes/auth.js` with login/register endpoints
- `config/auth.js` with token secrets and expiration
- Unit tests in `tests/auth.test.js`

## Rollback Commands

- `/architect rollback last-generation`: Remove all files created in the most recent generation operation
- `/architect rollback design <design_id>`: Revert to previous architecture version by ID
- `/architect undo refactor <commit_hash>`: Revert code changes to specified git commit (requires git integration)
- `/architect clean <pattern>`: Remove generated files matching pattern (e.g., `*.generated.*`)

## Dependencies and Requirements

- **Required**: OpenAI API key with sufficient credits for GPT-4 usage
- **Python Dependencies**: Install via `pip install openai langchain pydantic fastapi sqlalchemy redis stripe`
- **Node.js Dependencies**: `npm install express jsonwebtoken bcryptjs redis stripe`
- **System Requirements**: Python 3.8+, Node.js 16+, Docker for containerized deployments
- **API Limits**: Monitor OpenAI API usage to avoid rate limits (recommended: 100 requests/minute)

## Verification Steps

1. **Pre-Generation Check**: Run `/architect validate requirements <input>` to ensure requirements are parseable
2. **Code Quality**: Execute `npm run lint` or `python -m flake8` on generated code
3. **Type Checking**: Run `npx tsc --noEmit` for TypeScript or `mypy` for Python
4. **Test Execution**: Run generated test suites with `npm test` or `pytest`
5. **Integration Test**: Use provided Docker Compose to spin up services and test API endpoints
6. **Security Scan**: Run `npm audit` or `safety check` on dependencies

## Troubleshooting Common Issues

- **API Key Error**: "Error: OPENAI_API_KEY not found" → Set environment variable: `export OPENAI_API_KEY=your_key_here`
- **Rate Limit Exceeded**: "429 Too Many Requests" → Implement exponential backoff or upgrade OpenAI plan
- **Generation Timeout**: "Request timed out" → Reduce `DYNAMIC_ARCHITECT_MAX_TOKENS` or simplify requirements
- **Invalid Requirements**: "Unable to parse requirements" → Provide more specific, structured input with clear technology stack
- **Code Compilation Errors**: "SyntaxError in generated code" → Check language version compatibility and rerun with `--strict-mode`
- **Dependency Conflicts**: "Module not found" → Verify all dependencies are installed and versions are compatible
- **Memory Issues**: "Out of memory" → Reduce model temperature or split large generations into smaller components

## Best Practices

- Provide detailed requirements with specific technologies and constraints
- Review generated code before integration into production
- Use version control to track architectural changes
- Test generated code thoroughly in staging environments
- Document any manual modifications made to generated code
- Regularly update dependencies and security patches
- Monitor performance metrics after deployment of generated systems

## Changelog

- **v1.0.0**: Initial release with core architecture generation and code refactoring capabilities
- **Future**: Planned features include multi-language support expansion, integration with cloud platforms, and automated deployment scripts