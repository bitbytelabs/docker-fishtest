# docker-fishtest

## Worker

The worker uses an `archlinux:latest` base image and runs pacman updates in the background to
keep the software stack up to date. This is useful to get the latest compilers and tools for
running the worker.

### Use prebuilt image from GitHub Packages (GHCR)

The workflow publishes the worker image to:

- `ghcr.io/<owner>/<repo>/worker:latest` (default branch)
- `ghcr.io/<owner>/<repo>/worker:<branch|tag|sha>`

Example pull:

```bash
docker pull ghcr.io/<owner>/<repo>/worker:latest
```

### Build and run locally

```bash
cd worker
cp .env.example .env
```

Update the `.env` file with your credentials.

To start a worker, run:

```bash
docker compose up -d
```

## Server (for development)

To start a dev server, run:

```bash
cd server
git clone https://github.com/official-stockfish/fishtest
docker compose up -d
```

Copy `.netrc.example` to `.netrc` and update the `login` token with your GitHub personal access
token to increase the rate limit.
