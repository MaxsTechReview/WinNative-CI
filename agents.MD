# Agents Documentation

This document outlines the various automated and assistive agents that interact with the WinNative-CI repository.

## CI Automation Agents

The primary "agents" in this repository are automated workflows that manage the release lifecycle.

### GitHub Actions (Release Agent)
- **Role**: Automatically detects new builds from the main repository.
- **Responsibilities**:
  - Creating/Updating GitHub Releases for active Pull Requests.
  - Uploading APK artifacts to the corresponding release.
  - Maintaining release notes with links back to the source PR.
- **Trigger**: Pushes or PR updates in the source repository.

### Artifact Cleanup Agent
- **Role**: (Proposed/Optional) Manages the lifecycle of temporary release artifacts.
- **Responsibilities**:
  - Deleting releases for PRs that have been merged or closed.
  - Ensuring storage quotas are managed effectively.

## AI Agent Guidelines

When AI agents (e.g., Gemini, GitHub Copilot) are assisting with this repository, they should adhere to the following principles to maintain consistency with the automated release flow.

### Context Preservation
AI agents should always check the `README.md` and `ARCHITECTURE.md` to understand that this is a **release target** repository, not the primary source of code changes.

### File Modification Constraints
- **Release Assets**: AI agents should NEVER manually attempt to modify or upload release assets (APKs). This is strictly the domain of the CI agent.
- **Documentation**: AI agents are encouraged to keep documentation up-to-date as the CI workflow evolves.

### Versioning Awareness
AI agents should be aware that versioning here is driven by PR numbers and short SHA hashes from the source repository, rather than traditional semantic versioning.
