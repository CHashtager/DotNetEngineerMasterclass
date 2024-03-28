# Docker

## Basic Definition

Docker is an open-source platform that enables developers to build, deploy, run, and manage containerized applications. It provides an abstraction layer that packages an application with its dependencies, libraries, and runtime environment into a single, portable container.

## Containerization of Applications

Containerization is the process of packaging an application and its dependencies into a lightweight, self-contained, and portable unit called a container. Containers are isolated from the host system and other containers, ensuring consistent and predictable behavior across different environments.

## Best Practices of Dockerizing Applications

- **Modular Design:** Break down applications into smaller, reusable components.
- **Layered Approach:** Utilize Docker's layered filesystem for efficient caching and rebuilds.
- **Minimize Image Size:** Keep images as small as possible for faster distribution and reduced attack surface.
- **Separate Build and Run:** Separate the build and run stages for better caching and security.
- **Use Non-Root User:** Run containers with a non-root user for enhanced security.
- **Leverage Docker Compose:** Use Docker Compose for managing multi-container applications.

## Containerization Tools

Docker is the most popular containerization tool, but there are others like:

- **Podman:** Open-source, daemonless container engine.
- **containerd:** Industry-standard container runtime.
- **CRI-O:** Kubernetes-native container runtime.

## Docker Compose

Docker Compose is a tool for defining and running multi-container Docker applications. It allows you to specify the services, networks, volumes, and other configurations in a declarative YAML file, making it easier to manage and deploy complex applications.

## Compose CLI

The Docker Compose CLI provides a set of commands for working with Docker Compose files and managing multi-container applications. Some common commands include:

- `docker compose up`: Create and start containers defined in the Compose file.
- `docker compose down`: Stop and remove containers, networks, and volumes.
- `docker compose start/stop/restart`: Start, stop, or restart services.
- `docker compose logs`: View logs from containers.
- `docker compose scale`: Scale one or more services up or down.
