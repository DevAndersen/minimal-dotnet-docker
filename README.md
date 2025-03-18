# Minimal .NET Docker images

Proof of concept for running Native AoT compiled .NET applications in small Docker images.

The .NET projects are simple "*Hello, World!*" applications, in the form of a console- and a minimal API application.

In order to get the busybox- and scratch images working, `/lib/ld-musl-x86_64.so.1` is copied over from the build stage to the final stage. This is a hacky workaround, but works for the use case. Other potential dependencies, such as those needed for working with locales and timezones, are not included in the final stage.

**Disclaimers:**

- This is just a proof of concept. There is no guarantee of this approach working beyond these examples.
- The `.csproj` files were essentially written by simply throwing everything into them that could potentially result in a smaller publish result.

## Image sizes (musl x64)

| Base image | Console | Web |
|:--|--:|--:|
| [Alpine](https://hub.docker.com/_/alpine) | 11.67 MB | 38.27 MB|
| [Busybox](https://hub.docker.com/_/busybox) | 5.96 MB | 32.56 MB |
| [Scratch](https://hub.docker.com/_/scratch) | 4.50 MB | 31.10 MB |

## How to run

Simply run `docker compose up` in the root directory of this repository to build and run the containers.
