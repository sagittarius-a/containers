# Containers

_Various containers I created to keep my system clean and tidy_

## Instructions

Please make sure to run `docker volume create share` before using the containers
with shared content.

## Design

- Each container directory contains at least a `Dockerfile` and a `docker-compose.yml` file.
- The `docker-compose.yml` file contains 1 rule for sharing files between the host and the container:
- Default docker compose service is called `default`. This is leveraged by scripts like `runcontainer`
- By default, containers are interactive, which is like running them with `-it` flags with regular `docker run` command
  - Running them in background mode is still possible by using `-d`/`--detach` with `runcontainer` script
- Some containers use a shared volume to easily share/keep files. See `Instructions` chapter.

## Scripts

- `getcontainer`: Fetch container files
- `runcontainer`: Easily run a container

## Example

With the initial directory structure:

```
$ tree
.
└── script.py

0 directories, 1 file
```

Getting the `seccomp-tools` container with the `getcontainer seccomp-tools` command will result in the following directory structure:

```sh
.
├── script.py
└── seccomp-tools
    ├── docker-compose.yml
    └── Dockerfile

1 directory, 3 files
```

## Notes

This could lead to a lot of created containers that are, as of today, not automatically cleaned.

## Future work

- [ ] Allow reusing existing/stopped containers easily (after `-k`/`--keep` use with `runcontainer`)