# Project_Builder

Project overview and description.

## Project Structure

This project follows a standard development folder structure:

### Development Directories

- **`src/`** - Source code for single-service backend projects
  - Use for projects with a single service/API
  - Structure: `src/config/`, `src/routes/`, `src/services/`, `src/models/`, `src/lib/`

- **`apps/`** - Application components for multi-component projects
  - Use for projects with multiple services, frontend/backend, or agent-based systems
  - Each component gets its own subdirectory

- **`docs/`** - Project documentation
  - Requirements, specifications, guides, and API documentation

- **`scripts/`** - Utility and automation scripts
  - Build, deployment, migration, and development utilities

- **`tests/`** - Test files and test utilities
  - Unit, integration, and end-to-end tests

- **`infra/`** - Infrastructure as code and deployment configurations
  - Terraform, Docker, Kubernetes, CI/CD configurations

- **`tasks/`** - Task definitions and project management files
  - PRDs, task lists, feature specifications, planning documents

### Configuration

- **`.cursor/rules/`** - Cursor IDE rules and project-specific guidance
- **`.github/`** - GitHub configuration
  - `workflows/` - GitHub Actions workflows
  - `ISSUE_TEMPLATE/` - Issue templates
  - `PULL_REQUEST_TEMPLATE.md` - PR template

### Root Files

- `README.md` - This file
- `.gitignore` - Git ignore patterns
- `.editorconfig` - Editor configuration for consistent formatting
- `LICENSE` - Project license (MIT)

## Getting Started

1. Choose the appropriate directory structure based on your project type
2. Add your code to `src/` (single-service) or `apps/` (multi-component)
3. Document your project in `docs/`
4. Add tests to `tests/`
5. Configure infrastructure in `infra/`

## Development Guidelines

- Follow the patterns established in this workspace
- See `CLAUDE.md` in the parent directory for workspace-wide guidelines
- Refer to `.cursor/rules/prj-project-builder.mdc` for project-specific rules

## License

**MIT License - see LICENSE file for details**

