# Umbrel App Submission – bitBalance

## Context

First-time submission of a custom app to the Umbrel App Store.

The objective was to integrate a private Bitcoin wallet balance tracker using the existing Electrs service, without relying on external APIs.

This process also established the baseline workflow later reused for additional Umbrel apps.

## Environment Constraints

Umbrel introduces platform-specific constraints that are not always obvious from generic Docker documentation:

- Docker networking is managed internally
- Services communicate through predefined environment variables
- Persistent application data should use `${APP_DATA_DIR}`
- App packaging must follow Umbrel manifest conventions

## Issues Encountered

### 1. Network Configuration

**Initial assumption**  
Custom Docker network required.

**Observed behavior**  
Umbrel manages service networking automatically.

**Resolution**  
Removed all manual `networks` configuration from `docker-compose.yml`.

---

### 2. Volume Persistence

**Initial issue**  
Application data directory was not explicitly tracked in the repository.

**Impact**  
In a clean clone, the directory would not exist, creating avoidable runtime inconsistency.

**Resolution**  
Added `data/` directory with `.gitkeep` to preserve expected structure.

---

### 3. Configuration Minimalism

**Initial approach**  
Explicit configuration of services and structure.

**Adjusted approach**  
Reduce configuration to only what Umbrel actually requires.

**Outcome**  
Improved compatibility and closer alignment with Umbrel expectations.

---

### 4. Submission Workflow Reality

Technical implementation was only part of the process.

Additional steps included:

- publishing multi-arch Docker images
- preparing repository structure
- validating manifests
- creating and updating a fork
- opening pull requests
- iterating after lint or review feedback

**Observation**  
Publishing to Umbrel is straightforward after experience is acquired, but not trivial on a first submission.

## Key Takeaways

- Platform conventions override generic Docker habits
- Minimal configuration reduces integration friction
- Real behavior must be validated inside the target platform
- Publishing workflows are part of engineering, not separate from it
- Once the first app is shipped, subsequent apps become significantly easier

## Outcome

- Pull request accepted after review iterations
- Reviewer confirmed alignment with Umbrel standards
- App moved to gallery preparation stage
- Reusable packaging knowledge established for future releases
