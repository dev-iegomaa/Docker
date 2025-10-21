# 📚 What Is a Docker Architecture?

Docker architecture consists of:
- Image
- Container
- Registry
- Client
- Daemon

![Docker Architecture](./../images/docker-architecture.png)

## 🧱 What Is a Image?

A Docker **image** is a lightweight, standalone, `read-only` template, and executable package that includes everything needed to run a piece of software — such as the code, runtime, libraries, environment variables, and configuration files.

You can think of an image as a `blueprint` or `template` for creating containers.

When you run an image, Docker uses it to create a container — an isolated environment where your application runs.

You can build, pull, or push images using Docker commands.

🧩 Example: `php:8.2-apache`, `mysql:8`, `redis:alpine`

## 📦 What Is a Container?

A **container** is a standard unit of software that packages up code and all its dependencies so the application runs quickly and reliably from one computing environment to another.

A container is a running `instance` of an image.

It’s created from an image, but it’s isolated and can be started, stopped, or deleted anytime.

Multiple containers can be created from the same image.

It is a lightweight, standalone, isolated, executable package of software that includes everything needed to run an application: code, runtime, system tools, system libraries, and settings.

It makes your app portable and consistent everywhere.

✅ **Think of it like:**
> A small box that has your app + all its tools **dependecies & libraries** inside.

### Example:
If your app needs **PHP 8.2** and **MySQL**, you can put them inside containers.  
Then, you can run them on any computer that has Docker — no setup problems.

- Containerization has been around for a long time, but it was introduced in a different way by Docker.

## 🐳 What Is Registry?

A registry is where Docker images are stored and shared.

The main public registry is **Docker Hub**, but you can also host private registries.

When you run docker pull, Docker downloads the image from the registry.

🧩 Example: `docker pull redis` pulls the Redis image from Docker Hub.

## 💻 What Is Client?

The client is the **command-line tool** you use to interact with Docker.

It is used to run commands like `docker run`, `docker build`, `docker push`, and `docker pull`.

The client send commands to the Docker Daemon `dockerd`.

The Docker commands use the `Docker API` to interact with the Docker Daemon.

## ⚙️ What Is Docker Daemon (`dockerd`)?

The Docker Daemon `listens` for docker API requests and manage containers, images, networks and volumes.

## 📦 What Is Namespace?

Docker use techniques called **namespaces** to **isolate** containers from each other.

When you run a container, it runs in a **new namespace** that has a unique name.

Each aspect of a container runs in a separate namespace and it's isolated from other containers.
