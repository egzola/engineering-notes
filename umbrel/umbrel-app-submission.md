# Umbrel App Submission – bitBalance

## Context

First-time submission of a custom app to the Umbrel App Store.

The goal was to integrate a Bitcoin wallet balance tracker using the existing Electrs service, without relying on external APIs.

## Environment Constraints

Umbrel imposes implicit constraints that are not fully documented:

- Docker networking is managed internally
- Services are exposed via predefined environment variables
- Application data must persist using `${APP_DATA_DIR}`

## Issues Encountered

### 1. Network Configuration

Initial assumption:
Custom Docker network required.

Actual behavior:
Umbrel manages service networking automatically.

Resolution:
Removed all manual `networks` configuration from `docker-compose.yml`.

---

### 2. Volume Persistence

Initial issue:
Application data directory was not explicitly tracked in the repository.

Impact:
In a clean clone, the directory would not exist → potential runtime inconsistency.

Resolution:
Added `data/` directory with `.gitkeep` to ensure presence.

---

### 3. Configuration Minimalism

Initial approach:
Explicit configuration of services and structure.

Adjusted approach:
Reduce configuration to only what Umbrel requires.

Outcome:
Improved compatibility and alignment with Umbrel expectations.

## Key Takeaways

- Platform conventions override generic Docker practices
- Minimal configuration reduces integration issues
- Runtime behavior must be validated in the target environment

## Outcome

- PR accepted after review iterations
- Reviewer confirmed alignment with Umbrel standards
- App moved to gallery preparation stage
