# Umbrel App Submission – bitBoard

## Context

Submission of a second custom app to the Umbrel App Store after previously publishing bitBalance.

The objective was to build a customizable crypto price dashboard focused on speed, clean visuals and practical always-on monitoring for desktops, tablets and secondary displays.

Unlike bitBalance, this project relied on public pricing APIs instead of local blockchain infrastructure.

## Why This Submission Was Different

Previous experience with bitBalance significantly reduced friction.

Existing knowledge could be reused across:

- repository structure
- Docker packaging
- multi-architecture builds
- GitHub Container Registry publishing
- Umbrel manifest conventions
- pull request workflow
- lint expectations

This confirmed that the first submission carries most of the learning cost.

## Technical Scope

bitBoard required solving practical product-oriented concerns:

- responsive dashboard layout
- drag & drop card ordering
- persistent local settings
- mobile usability adjustments
- real-time price refresh logic
- external API rate-limit awareness
- lightweight runtime footprint

## Issues Encountered

### 1. Multi-Architecture Build Pipeline

Initial local build worked only for the default architecture.

**Resolution**

Configured `docker buildx` workflow for:

- `linux/amd64`
- `linux/arm64`

Published a multi-platform image to GHCR.

---

### 2. Docker Image Hygiene

Initial image contained unnecessary local context and reused cached layers.

**Resolution**

- added `.dockerignore`
- rebuilt with `--no-cache`
- validated final container contents
- updated digest in `docker-compose.yml`

---

### 3. Umbrel Submission Validation

Automated lint checks initially flagged manifest issues such as submission fields and image references.

**Resolution**

Adjusted metadata, image publication visibility and manifest details until all checks passed cleanly.

---

### 4. UI Reality vs Static Design

Layouts that looked correct on desktop introduced horizontal scroll on mobile devices.

**Resolution**

Reworked responsive behavior based on real device constraints rather than desktop assumptions.

## Key Takeaways

- First shipping experience compounds strongly into later releases
- Packaging quality matters as much as application code
- Clean Docker artifacts reduce long-term friction
- Real mobile behavior differs from browser resize assumptions
- External APIs require graceful handling of rate limits
- Shipping becomes faster when previous release patterns are reusable

## Outcome

- Pull request submitted successfully
- Automated lint passed with no errors or warnings
- Multi-architecture container published
- Production-ready release workflow refined further
