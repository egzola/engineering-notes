# Umbrel App Submission – Telegrapho

## Context

Submission of a third custom app to the Umbrel App Store after previously publishing bitBalance and bitBoard.

The objective was to build a lightweight self-hosted realtime text bridge that allows users to transfer text instantly between devices using infrastructure they control.

Unlike bitBalance and bitBoard, Telegrapho focuses on simplicity rather than dashboards, blockchain infrastructure or external market data.

## Why This Submission Was Different

Previous publication experience reduced most of the uncertainty around the Umbrel ecosystem.

Existing knowledge could be reused across:

* repository structure
* Docker packaging
* multi-architecture builds
* GitHub Container Registry publishing
* Umbrel manifest conventions
* pull request workflow
* lint requirements

This allowed most effort to remain focused on the application itself rather than deployment mechanics.

## Technical Scope

Telegrapho required solving practical communication and usability concerns:

* realtime text synchronization
* channel-based message isolation
* mobile usability
* QR code sharing
* lightweight deployment
* no database dependency
* low resource consumption
* simple self-hosted operation

The application intentionally avoids external services and keeps runtime requirements minimal.

## Issues Encountered

### 1. Buildx Multi-Architecture Environment

The initial build environment was configured with the default Docker driver, which does not support multi-platform image publishing.

**Resolution**

Created a dedicated Buildx builder using the `docker-container` driver and published a multi-platform image for:

* `linux/amd64`
* `linux/arm64`

---

### 2. GitHub Container Registry Authentication

Image publication initially failed due to expired or unavailable Personal Access Tokens previously created for individual projects.

**Resolution**

Reviewed existing registry credentials, replaced project-specific tokens with a single reusable publishing token and successfully published the image to GHCR.

---

### 3. Umbrel Manifest Validation

Automated lint checks identified several metadata issues:

* unsupported category value
* missing submission URL
* tagline formatting
* release notes requirements for new apps

**Resolution**

Adjusted the manifest to comply with current Umbrel App Store validation rules until all checks passed successfully.

---

### 4. Container Verification

After publication, the container image was validated independently from the development environment.

**Resolution**

Verified:

* public image availability
* image digest consistency
* successful image pull
* successful container startup
* healthy runtime state

This confirmed that the published artifact matched the tested application.

## Key Takeaways

* Repeated releases dramatically reduce deployment friction
* Most publication issues occur outside application code
* Multi-architecture support remains essential for Umbrel compatibility
* Registry credential management benefits from simplification
* Automated lint feedback prevents reviewer-facing issues
* Small self-hosted applications can remain highly useful without adding complexity

## Outcome

* Pull request submitted successfully
* Automated lint passed with no errors or warnings
* Multi-architecture container published
* Public GHCR image validated
* Runtime behavior verified after publication
* Third Umbrel App Store submission completed
