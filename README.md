# Azure DevOps Work Item Analytics Extension

A Blazor WebAssembly extension for Azure DevOps that provides advanced work item analytics and visualization capabilities. This extension supports both deployment as an Azure DevOps extension and standalone local development mode.

## Features

- Real-time work item analytics dashboards
- Customizable metrics and visualizations
- Dual-hosting architecture (Extension mode and Local development mode)
- High-performance data virtualization for large datasets
- OData-based analytics queries

## Contribution Guidelines

This project follows **Specification-Driven Development (SDD)** patterns inspired by [GitHub's spec-kit](https://github.com/github/spec-kit). All features must go through a rigorous specification and design process before implementation.

### The SDD Workflow

1. **Specification First** (`/specify`)
   - Every feature begins with a specification document
   - Specifications focus on WHAT and WHY, not HOW
   - All ambiguities must be marked with `[NEEDS CLARIFICATION]`
   - Specs are reviewed for completeness before proceeding

2. **Planning Phase** (`/plan`)
   - Technical implementation plan created from the specification
   - Architecture decisions documented with rationale
   - Constitution compliance verified at multiple gates
   - Research phase resolves all technical unknowns

3. **Task Generation** (`/tasks`)
   - Detailed, numbered tasks generated from the plan
   - Test-Driven Development enforced (tests before implementation)
   - Parallel tasks marked with `[P]` for efficiency
   - Dependencies explicitly documented

4. **Implementation** (`/implement`)
   - Tasks executed in dependency order
   - Each task results in a commit
   - Tests must fail before implementation (TDD)
   - Constitution principles enforced throughout

### Constitutional Principles

All contributions must adhere to the project constitution (`.specify/memory/constitution.md`):

1. **Hybrid Architecture First** - Features must work in both extension and local modes
2. **Performance by Design** - Virtualization required for large datasets, bundle size < 50MB
3. **Security and Authentication Abstraction** - Dual authentication support mandatory
4. **Test-Driven Development** - Tests written before implementation, no exceptions
5. **Observable Analytics Pipeline** - Comprehensive error handling and retry logic

### Making a Contribution

#### For New Features

```bash
# 1. Create a feature specification
/specify "Your feature description"

# 2. Create implementation plan
/plan

# 3. Generate tasks
/tasks

# 4. Execute implementation
/implement
```

#### For Bug Fixes

1. Create an issue describing the bug
2. Write a failing test that reproduces the bug
3. Implement the fix to make the test pass
4. Ensure all existing tests still pass

#### For Documentation

- Documentation updates follow the same SDD process for significant changes
- Minor corrections can be submitted directly via PR

### Project Structure

```
.specify/
├── memory/
│   ├── constitution.md     # Project governance and principles
│   └── specs/              # Feature specifications
├── templates/              # SDD templates
└── scripts/               # Automation tools

src/
├── BlazorApp/             # Blazor WASM application
├── Extension/             # Azure DevOps extension wrapper
└── LocalHost/             # Local development server

docs/
└── original-plan.md       # Comprehensive implementation guide
```

### Code Review Requirements

All pull requests must:

1. **Pass Constitution Gates**
   - Performance requirements met
   - Security patterns followed
   - Test coverage adequate

2. **Include Specifications**
   - Link to feature spec for new features
   - Document rationale for changes

3. **Follow TDD Process**
   - Tests demonstrate the issue (for bugs) or feature
   - Tests written before implementation
   - All tests passing

4. **Maintain Dual-Mode Support**
   - Changes work in both extension and local modes
   - Authentication abstraction preserved

### Development Commands

```bash
# Run tests
dotnet test

# Build for development
dotnet build

# Build for production (with AOT)
dotnet publish -c Release

# Package extension
npm run package-extension

# Local development
dotnet watch run --project src/LocalHost/Server
```

### Getting Help

- Review the [original implementation plan](docs/original-plan.md)
- Check the [project constitution](.specify/memory/constitution.md)
- Use `/help` in the development environment
- Open an issue for questions or concerns

## License

[Your license here]