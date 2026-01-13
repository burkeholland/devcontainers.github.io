---
title: Glossary and Terminology Reference
layout: singlePage
sectionid: glossary
---

This glossary provides definitions for key terms and concepts related to Development Containers. Use this reference to better understand the Dev Container Specification and related tools.

## <a href="#core-concepts" name="core-concepts" class="anchor"> Core Concepts </a>

### <a href="#development-container" name="development-container" class="anchor"> Development Container (Dev Container) </a>

A development container (or dev container for short) is a container that provides a full-featured development environment. It can be used to run an application, to separate tools, libraries, or runtimes needed for working with a codebase, and to aid in continuous integration and testing. Dev containers can be run locally or remotely, in a private or public cloud.

### <a href="#dev-container-spec" name="dev-container-spec" class="anchor"> Development Container Specification (Dev Container Spec) </a>

An open specification for enriching containers with development specific content and settings. The specification seeks to find ways to enrich existing formats with common development specific settings, tools, and configuration while still providing a simplified, un-orchestrated single container option.

### <a href="#environment" name="environment" class="anchor"> Environment </a>

A logical instance of one or more development containers, along with any needed side-car containers. An environment is based on one set of metadata that can be managed as a single unit. Users can create multiple environments from the same configuration metadata for different purposes.

## <a href="#configuration" name="configuration" class="anchor"> Configuration </a>

### <a href="#devcontainerjson" name="devcontainerjson" class="anchor"> devcontainer.json </a>

A structured JSON with Comments (jsonc) metadata format that tools can use to store configuration required to develop inside of local or cloud-based containerized coding environments. This file typically resides in `.devcontainer/devcontainer.json` or `.devcontainer.json` at the root of a project.

### <a href="#image-metadata" name="image-metadata" class="anchor"> Image Metadata </a>

Dev container metadata properties that can be stored in an image label as an array of metadata snippets. This allows configuration to be stored in prebuilt images, making the image and its related configuration self-contained. The metadata is added to the image as a `devcontainer.metadata` label.

### <a href="#customizations" name="customizations" class="anchor"> Customizations </a>

Tool-specific configuration properties within `devcontainer.json`. Each tool or service (like VS Code, Codespaces, etc.) has its own namespace under `customizations` to specify product-specific settings, extensions, and behaviors.

## <a href="#features-and-templates" name="features-and-templates" class="anchor"> Features and Templates </a>

### <a href="#dev-container-features" name="dev-container-features" class="anchor"> Dev Container Features </a>

Self-contained, shareable units of installation code and development container configuration. Features allow you to quickly and easily add tooling, runtime, or library capabilities into your development container. Each Feature is defined by a `devcontainer-feature.json` file and an `install.sh` script.

### <a href="#dev-container-templates" name="dev-container-templates" class="anchor"> Dev Container Templates </a>

Pre-configured development container setups that provide starting points for different technology stacks and development scenarios. Templates help developers quickly bootstrap new projects with appropriate dev container configurations.

### <a href="#collections" name="collections" class="anchor"> Collections </a>

A set of Features and/or Templates published together, typically from a single source repository. Collections provide a way to organize and distribute related dev container components as a unit.

## <a href="#lifecycle" name="lifecycle" class="anchor"> Lifecycle and Commands </a>

### <a href="#lifecycle-scripts" name="lifecycle-scripts" class="anchor"> Lifecycle Scripts </a>

Commands that execute at specific points during the dev container lifecycle. These include:

- **onCreateCommand**: Runs when the container is created
- **updateContentCommand**: Runs when the container is updated  
- **postCreateCommand**: Runs after the container is created
- **postStartCommand**: Runs each time the container starts
- **postAttachCommand**: Runs each time a tool attaches to the container

### <a href="#prebuild" name="prebuild" class="anchor"> Prebuild </a>

The process of building a dev container image ahead of time, often in a CI/CD pipeline, so that developers can start working immediately without waiting for build steps. Prebuilds can significantly reduce environment startup time.

## <a href="#container-properties" name="container-properties" class="anchor"> Container Properties </a>

### <a href="#base-image" name="base-image" class="anchor"> Base Image </a>

The starting Docker or OCI container image that a dev container is built upon. The base image typically contains the operating system and may include pre-installed runtimes or tools.

### <a href="#mounts" name="mounts" class="anchor"> Mounts </a>

Mechanisms to make files and directories available inside a container. Mounts can be:
- **Bind mounts**: Map a host directory to a container directory
- **Volume mounts**: Use Docker volumes for persistent data storage
- **tmpfs mounts**: Use RAM-backed temporary storage

### <a href="#port-forwarding" name="port-forwarding" class="anchor"> Port Forwarding </a>

The process of making ports from inside the dev container accessible to the host or other systems. Configured via `forwardPorts` and `portsAttributes` properties in `devcontainer.json`.

### <a href="#privileged-mode" name="privileged-mode" class="anchor"> Privileged Mode </a>

A container runtime setting that grants the container extended privileges, similar to running as root on the host. Required for certain scenarios like Docker-in-Docker. Set via the `privileged` property.

### <a href="#capabilities" name="capabilities" class="anchor"> Capabilities (capAdd) </a>

Linux kernel capabilities that can be added to a container to grant specific privileges without running in fully privileged mode. Configured via the `capAdd` property.

## <a href="#users-and-permissions" name="users-and-permissions" class="anchor"> Users and Permissions </a>

### <a href="#container-user" name="container-user" class="anchor"> Container User </a>

The user account that the container runs as during build and initialization steps. Set via the `containerUser` property in `devcontainer.json`.

### <a href="#remote-user" name="remote-user" class="anchor"> Remote User </a>

The user account that a tool or IDE should use when connecting to and working inside the container. This is typically a non-root user for security. Set via the `remoteUser` property in `devcontainer.json`.

## <a href="#tools-and-services" name="tools-and-services" class="anchor"> Tools and Services </a>

### <a href="#dev-container-cli" name="dev-container-cli" class="anchor"> Dev Container CLI </a>

The reference implementation command-line interface for the Dev Container Specification. It can create, configure, and manage dev containers based on `devcontainer.json` configuration. Available at [devcontainers/cli](https://github.com/devcontainers/cli).

### <a href="#supporting-tools" name="supporting-tools" class="anchor"> Supporting Tools </a>

Editors, IDEs, and services that implement the Dev Container Specification, including:
- **VS Code Dev Containers extension**: Visual Studio Code extension for local dev containers
- **GitHub Codespaces**: Cloud-hosted dev containers on GitHub
- **CodeSandbox**: Cloud development environments with dev container support
- **DevPod**: Client-only tool for creating dev containers on various backends
- **Visual Studio**: Support for C++ dev containers with CMake
- **IntelliJ IDEA**: Dev container support via SSH or Docker

## <a href="#distribution" name="distribution" class="anchor"> Distribution and Registries </a>

### <a href="#oci-registry" name="oci-registry" class="anchor"> OCI Registry </a>

An Open Container Initiative (OCI) compliant registry used to publish and distribute Dev Container Features and Templates. Examples include GitHub Container Registry (ghcr.io) and Docker Hub.

### <a href="#feature-id" name="feature-id" class="anchor"> Feature ID </a>

A unique identifier for a Dev Container Feature, typically in the format of a registry URL followed by the feature name and version (e.g., `ghcr.io/devcontainers/features/node:1`).

## <a href="#development-workflow" name="development-workflow" class="anchor"> Development Workflow </a>

### <a href="#inner-loop" name="inner-loop" class="anchor"> Inner Loop </a>

The iterative development cycle of coding, building, and testing that developers perform frequently during active development. Dev containers optimize the inner loop by providing consistent, fast development environments.

### <a href="#outer-loop" name="outer-loop" class="anchor"> Outer Loop </a>

The broader development workflow that includes CI/CD, deployment, and production operations. While separate from the inner loop, dev containers can be leveraged in CI/CD pipelines for consistency.

### <a href="#workspace-folder" name="workspace-folder" class="anchor"> Workspace Folder </a>

The primary directory inside the dev container where the project source code is located. This is where lifecycle scripts execute and where the IDE/editor typically opens. Configured via `workspaceFolder` property.

## <a href="#advanced-concepts" name="advanced-concepts" class="anchor"> Advanced Concepts </a>

### <a href="#docker-compose" name="docker-compose" class="anchor"> Docker Compose </a>

An orchestration tool that can be used with dev containers to define and run multi-container applications. Dev containers support referencing a `docker-compose.yml` file for complex scenarios requiring multiple services.

### <a href="#docker-in-docker" name="docker-in-docker" class="anchor"> Docker-in-Docker </a>

Running Docker inside a Docker container. Some dev container Features enable this capability, which is useful for building container images or running containers during development.

### <a href="#host-requirements" name="host-requirements" class="anchor"> Host Requirements </a>

Minimum hardware requirements (CPU cores, memory, storage, GPU) that a dev container needs to function properly. Specified via the `hostRequirements` property in `devcontainer.json`.

### <a href="#init-process" name="init-process" class="anchor"> Init Process </a>

A minimal init system (like tini) that can be added to a container to properly handle process signals and zombie processes. Enabled via the `init` property.

### <a href="#security-opt" name="security-opt" class="anchor"> Security Options (securityOpt) </a>

Container security settings such as SELinux and AppArmor profiles, or modifications to the seccomp profile. Configured via the `securityOpt` property.

## <a href="#variables" name="variables" class="anchor"> Variables and Substitution </a>

### <a href="#predefined-variables" name="predefined-variables" class="anchor"> Predefined Variables </a>

Variables that can be used in `devcontainer.json` values for dynamic configuration:
- `${localEnv:VARIABLE_NAME}`: References environment variables from the local machine
- `${containerEnv:VARIABLE_NAME}`: References environment variables from inside the container
- `${localWorkspaceFolder}`: The local path to the workspace folder
- `${containerWorkspaceFolder}`: The container path to the workspace folder

## <a href="#see-also" name="see-also" class="anchor"> See Also </a>

For more detailed information, refer to:
- [Dev Container Specification](/implementors/spec)
- [devcontainer.json Reference](/implementors/json_reference)
- [Features Reference](/implementors/features)
- [Templates Reference](/implementors/templates)
- [Supporting Tools](/supporting)
