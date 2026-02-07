# Project Builder

A tool that helps you create comprehensive instruction sets for ChatGPT Projects, Claude Projects, Gems, or Copilot configurations.

## What It Does

Project Builder guides you through a structured process to create professional-grade instruction files:

1. **Intake** — Gathers basic information about your project (6 questions)
2. **Q&A** — Asks detailed questions to understand your requirements (up to 11 questions)
3. **Summary** — Presents your captured requirements for review
4. **Draft Review** — Shows draft instruction files for your approval
5. **Deployment** — Generates setup instructions with test cases
6. **Generation** — Produces final downloadable files

## Output Files

The Project Builder generates three files:

- **CORE Instructions** — Governance, rules, and constraints (≤6000 characters for token efficiency)
- **COMPANION Instructions** — Execution logic, workflows, and detailed procedures
- **Deployment Instructions** — Platform-specific setup steps and test cases

## Who It's For

- **Beginners** — Plain-language explanations at every step
- **Experienced users** — Streamlined process with less explanation

## How to Use

1. Upload the `CORE_ProjectBuilder_Instructions.md` and `COMPANION_ProjectBuilder_Instructions.md` files to your selected platform
2. Start a new conversation
3. Follow the guided intake and Q&A process
4. Review and approve draft files
5. Download your customized instruction files
6. Deploy to your target platform using the generated deployment instructions

## Documentation

See the `docs/` folder for:
- `CORE_ProjectBuilder_Instructions.md` — Main instruction file
- `COMPANION_ProjectBuilder_Instructions.md` — Execution logic
- `Deployment_Instructions_Template.md` — Template for generated deployment docs

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

