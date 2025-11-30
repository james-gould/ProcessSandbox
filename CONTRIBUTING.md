# Contributing to ProcessSandbox

Thank you for your interest in contributing to ProcessSandbox! This document provides guidelines and instructions for contributing.

## Code of Conduct

Be respectful, constructive, and professional in all interactions.

## Getting Started

1. Fork the repository
2. Clone your fork: `git clone https://github.com/yourusername/ProcessSandbox.git`
3. Create a feature branch: `git checkout -b feature/my-feature`
4. Make your changes
5. Run tests: `dotnet test`
6. Commit and push to your fork
7. Create a Pull Request

## Development Setup

### Prerequisites

- Visual Studio 2022 or JetBrains Rider
- .NET 8.0 SDK
- .NET Framework 4.8 Developer Pack
- Windows OS (required for Job Objects)

### Building

```bash
dotnet restore
dotnet build
```

### Running Tests

```bash
# Unit tests
dotnet test tests/ProcessSandbox.Tests

# Integration tests
dotnet test tests/ProcessSandbox.Integration.Tests

# All tests
dotnet test
```

## Code Guidelines

### Style

- Follow standard C# conventions
- Use nullable reference types
- Prefer explicit over implicit
- Add XML documentation for public APIs
- Keep methods focused and small

### Naming

- Interfaces: `IProcessPool`
- Classes: `ProcessPool`
- Methods: `StartWorkerProcess`
- Private fields: `_workerProcess`
- Constants: `MaxRetryCount`

### Testing

- Write unit tests for new functionality
- Add integration tests for end-to-end scenarios
- Aim for >80% code coverage
- Test error conditions and edge cases

### Documentation

- Update XML comments for public APIs
- Add/update README if changing usage
- Update CHANGELOG.md with your changes
- Include code examples for new features

## Pull Request Process

1. **Update documentation** - README, XML comments, etc.
2. **Add tests** - Unit and integration tests
3. **Update CHANGELOG.md** - Add entry under "Unreleased"
4. **Ensure CI passes** - All tests must pass
5. **Request review** - Tag maintainers

### PR Title Format

Use conventional commits format:
- `feat: Add circuit breaker support`
- `fix: Handle worker crash during startup`
- `docs: Update configuration guide`
- `test: Add concurrent call tests`
- `refactor: Simplify IPC channel code`

## Issue Reporting

### Bug Reports

Include:
- ProcessSandbox version
- .NET version and OS
- Minimal reproduction code
- Expected vs actual behavior
- Stack traces/logs

### Feature Requests

Include:
- Use case description
- Proposed API/usage
- Why existing features don't work
- Are you willing to implement it?

## Architecture Guidelines

### Adding New Features

1. **Design first** - Open an issue to discuss
2. **Keep it generic** - Don't add use-case-specific code
3. **Configuration over code** - Prefer configurable options
4. **Backward compatibility** - Don't break existing APIs
5. **Performance** - Consider impact on IPC overhead

### Code Organization

- `Proxy/` - Proxy generation and method dispatch
- `Pool/` - Process pool management
- `IPC/` - Inter-process communication
- `Monitoring/` - Resource monitoring
- `JobObjects/` - Windows Job Objects integration

## Testing Philosophy

- **Unit tests** - Fast, isolated, no external dependencies
- **Integration tests** - Full process lifecycle, IPC, real workers
- **Test clarity** - Test names describe what they verify
- **Arrange-Act-Assert** - Clear test structure

## Release Process

(For maintainers)

1. Update version in `Directory.Build.props`
2. Update `CHANGELOG.md` with release date
3. Tag: `git tag v1.0.0`
4. Push: `git push origin v1.0.0`
5. GitHub Actions publishes to NuGet

## Questions?

Open a [Discussion](https://github.com/yourusername/ProcessSandbox/discussions) or reach out to maintainers.

## License

By contributing, you agree that your contributions will be licensed under the MIT License.
