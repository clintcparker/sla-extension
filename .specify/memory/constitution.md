<!-- Sync Impact Report
Version change: 0.0.0 → 1.0.0
Modified principles: Initial constitution creation
Added sections: All sections (initial creation)
Removed sections: None
Templates requiring updates: ✅ All templates validated for initial version
Follow-up TODOs: RATIFICATION_DATE needs confirmation
-->

# Azure DevOps Work Item Analytics Extension Constitution

## Core Principles

### I. Hybrid Architecture First
The extension MUST implement a dual-hosting architecture supporting both Azure DevOps extension mode (JavaScript interop) and standalone local development mode (PAT authentication). Every feature MUST be accessible in both modes through dependency injection and interface-based service abstraction. The JavaScript bridge layer MUST be maintained as a thin wrapper that delegates all business logic to the Blazor components.

### II. Performance by Design
All dashboard components MUST implement virtualization for datasets larger than 100 items. Bundle size MUST remain under 50MB for marketplace compliance. AOT compilation and tree shaking MUST be enabled for production builds. Lazy loading MUST be implemented for non-critical assemblies and heavy components.

### III. Security and Authentication Abstraction
Authentication MUST be abstracted behind IAuthenticationService interface enabling seamless switching between extension tokens and PAT authentication. All sensitive data (tokens, PATs) MUST be handled through secure channels and never logged or exposed in client-side code. Content Security Policy compliance MUST be maintained for all extension contributions.

### IV. Test-Driven Development
Unit tests MUST be written before implementation following Red-Green-Refactor cycle. Integration tests MUST cover all Azure DevOps API interactions and authentication switching scenarios. JavaScript interop bridge MUST have comprehensive test coverage for both success and failure paths.

### V. Observable Analytics Pipeline
All data fetching operations MUST implement proper error handling, retry logic, and cancellation token support. Real-time refresh capabilities MUST use configurable polling intervals with automatic backoff on failures. Analytics queries MUST be optimized using OData projections and filters to minimize data transfer.

## Development Standards

### Code Organization
- Blazor components organized by feature (Dashboard, Analytics, Widgets)
- Services segregated into Abstractions, DevOps, and Analytics namespaces
- JavaScript interop code isolated in dedicated Interop namespace
- Extension wrapper maintained separately from Blazor application

### Debugging and Diagnostics
- Comprehensive logging service for both browser console and .NET logging
- Development-only debug breakpoint injection through JavaScript
- Detailed error boundaries around all component trees
- Performance metrics collection for critical rendering paths

## Deployment Requirements

### CI/CD Pipeline Standards
- Automated build triggered on main and develop branches
- Blazor WASM publication with AOT compilation for releases
- Extension packaging with version incrementing
- Marketplace deployment only from main branch with approval gates

### Browser Compatibility
- Chrome, Edge, Firefox, and Safari support required
- Progressive enhancement for unsupported browser features
- Graceful degradation when JavaScript is disabled
- Responsive design for various dashboard widget sizes

## Governance

The constitution supersedes all implementation decisions and architectural choices. All pull requests MUST demonstrate compliance with constitutional principles through:
- Code review verification against principles
- Automated testing validation
- Bundle size checks for performance compliance
- Security scan for authentication handling

Amendments to this constitution require:
1. Documented rationale for change
2. Impact analysis on existing codebase
3. Migration plan for breaking changes
4. Team consensus and approval

Runtime development guidance follows the patterns established in the original implementation plan at `docs/original-plan.md`.

**Version**: 1.0.0 | **Ratified**: 09-25-25 | **Last Amended**: 2025-09-25