<div align="center">

<h3 align="center"><b><u>Deploy this project Instantly</u></b></h3>

<a href="https://launch.nife.io/deploy-app/start?repository-url=https://github.com/nifetency/rails-example">
  <img
    src="https://launch.nife.io/deploy-on-nife.svg"
    alt="Deploy on NIFE"
    width="280"
  />
</a>

</div>

# Rails Example

A simple **Ruby on Rails** application published as a **sample deployment project for [Nife.io](https://nife.io)**.

This repository demonstrates how to run a lightweight Rails application locally, package it with Docker, and deploy it on [Nife.io](https://nife.io). It is intended as a practical sample for validating Rails deployment workflows, container-based delivery, and basic platform configuration.[1] [2] [3]

## Recommended README

```md
# Rails Example

A simple **Ruby on Rails** application published as a **sample deployment project for [Nife.io](https://nife.io)**.

This repository demonstrates how to run a lightweight Rails application locally, package it with Docker, and deploy it on [Nife.io](https://nife.io). It is intended as a practical sample for testing Rails deployment workflows and showcasing a straightforward Ruby on Rails deployment path.

## Overview

This project is a basic Rails application with a standard project structure, backend logic, and database integration through Active Record. It is designed to be small enough for learning and deployment experiments while still reflecting the conventions of a real Rails application.[3]

If you want a simple backend-oriented sample to test deployment on [Nife.io](https://nife.io), this repository is a good starting point.

## Features

| Feature | Description |
| --- | --- |
| Ruby on Rails app | Built with the standard Rails application structure |
| MVC architecture | Uses the conventional Rails model-view-controller pattern |
| Database integration | Supports database-backed application workflows through Active Record |
| Docker support | Includes a `Dockerfile` for containerized execution |
| Deployment-ready setup | Can be deployed using Git-based or Docker-based workflows |
| Nife.io sample use case | Suitable as a reference project for [Nife.io](https://nife.io) deployments |

## Tech Stack

| Technology | Purpose |
| --- | --- |
| Ruby | Runtime environment |
| Ruby on Rails | Web framework |
| Bundler | Dependency management |
| SQLite or PostgreSQL | Database layer, depending on configuration |
| Docker | Container packaging |
| Nife.io | Deployment platform |

## Prerequisites

Before running the project locally, make sure the following are installed.

| Requirement | Notes |
| --- | --- |
| Ruby | Use the version specified in `.ruby-version` |
| Bundler | Required to install Ruby gems |
| Rails | Required for Rails commands |
| Database | SQLite or PostgreSQL depending on your environment |
| Git | Required to clone the repository |

## Getting Started

### Clone the repository

```bash
git clone https://github.com/nifetency/rails-example.git
cd rails-example
```

### Install dependencies

```bash
bundle install
```

### Set up the database

```bash
rails db:create
rails db:migrate
```

### Start the application

```bash
rails server
```

Then open the application at `http://localhost:3000`.

## Run with Docker

This project includes a Dockerfile for container-based execution.

### Build the image

```bash
docker build -t rails-example .
```

### Run the container

```bash
docker run -p 3000:3000 rails-example
```

After the container starts, open the app at `http://localhost:3000`.

## Deploy on Nife.io

You can deploy this application on [Nife.io](https://nife.io) using either a Docker image, the source repository, or the CLI.[1] [2]

### Option 1: Deploy from a Docker image

First, build and push the image to your preferred container registry.

```bash
docker build -t rails-example .
docker tag rails-example <username>/rails-example:latest
docker push <username>/rails-example:latest
```

Then configure a new application in Nife.io with the following settings.

| Setting | Value |
| --- | --- |
| Source | Docker Image |
| Registry | Docker Hub or another supported registry |
| Image | `<username>/rails-example:latest` |
| Internal Port | `3000` |
| External Port | `80` |
| Suggested Replicas | `1` |

### Option 2: Deploy from the Git repository

You can also deploy the project directly from GitHub.

| Setting | Value |
| --- | --- |
| Source | Git Repository |
| Provider | GitHub |
| Branch | `main` |
| Internal Port | `3000` |
| External Port | `80` |
| Build Mode | Auto-Dockerize with runtime |

### Option 3: Deploy with `nifectl`

If you prefer the command line, use the following workflow.

```bash
nifectl auth login
nifectl init
nifectl deploy
```

For step-by-step instructions, see the [Nife.io Quick Deploy documentation](https://docs.nife.io/overview/quick-deploy) and the [nifectl quick start guide](https://docs.nife.io/Quick-Start/Nifectl).


## Environment Variables

The following variables are commonly relevant for deployment.

| Variable | Description | Example |
| --- | --- | --- |
| `RAILS_ENV` | Rails execution environment | `production` |
| `DATABASE_URL` | Database connection string | `postgres://user:pass@host/db` |
| `PORT` | Application port, if overridden by environment | `3000` |

## Repository Structure

| Path | Purpose |
| --- | --- |
| `app/` | Main Rails application code |
| `config/` | Framework and environment configuration |
| `db/` | Database schema and migrations |
| `lib/` | Library and support code |
| `public/` | Static public assets |
| `test/` | Test files |
| `Dockerfile` | Container build instructions |
| `Gemfile` | Ruby gem dependencies |
| `config.ru` | Rack configuration entry point |

## Troubleshooting

| Issue | Suggested fix |
| --- | --- |
| Bundler install fails | Verify your Ruby version and rerun `bundle install` |
| Database is not created | Run `rails db:create db:migrate` |
| Port `3000` is already in use | Stop the conflicting process or remap the port |
| Docker build fails | Recheck the Dockerfile and local Ruby environment |
| Deployment fails on Nife.io | Verify ports, environment variables, and build settings |
| Application is unreachable | Check routing, service exposure, and deployment logs |

## Acknowledgements

This repository is maintained by **Nifetency** as a sample deployment project for [Nife.io](https://nife.io).

If this repository is derived from an earlier template or upstream example, it is good practice to retain visible credit to the original author or source repository.

## License

This project is licensed under the **MIT License**.

---

## References

1. (https://nife.io)
2. (https://docs.nife.io/overview/)
3. (https://github.com/nifetency/rails-example)
4. (https://docs.nife.io/Quick-Start)
