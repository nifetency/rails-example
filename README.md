# Rails Example

##  Overview

This is a Ruby on Rails application demonstrating a basic web app structure.
It includes backend logic, database integration, and a standard Rails project setup.

This project can be used for learning Rails fundamentals, deployment, and development workflows.

---

##  Features

* Built with Ruby on Rails
* MVC architecture
* Database integration (via ActiveRecord)
* Docker support (Dockerfile included)
* Ready for deployment using nifectl

---

##  Requirements

Make sure you have the following installed:

* Ruby (check `.ruby-version`)
* Rails
* Bundler
* SQLite / PostgreSQL (depending on config)
* Git

---

##  Installation

### 1. Clone the repository

```bash
git clone https://github.com/nifetency/rails-example.git

cd rails-example
```

---

### 2. Install dependencies

```bash
bundle install
```

---

### 3. Setup the database

```bash
rails db:create
rails db:migrate
```

---

### 4. Run the application locally

```bash
rails server
```

 Open in browser:
http://localhost:3000

---

##  Run with Docker (Optional)

```bash
docker build -t rails-app .
docker run -p 3000:3000 rails-app
```

---
## Deployment on NIFE

Deploy your application using the NIFE platform:

https://launch.nife.io/

Deployment flow:

```id="lq3k8p"
Source → Build → Resources → Review → Deploy
```

Prerequisite: Ensure a workload (Deployment, CronJob, or StatefulSet) exists.

---

## Method 1: Deploy via Docker Image (Recommended)

### Step 1: Build and Push Image

```bash id="2m8c9a"
docker build -t rails-example .
docker tag rails-example <username>/rails-example:latest
docker push <username>/rails-example:latest
```

---

### Step 2: Configure Source

* Source: Docker Image
* Registry: Docker Hub
* Image: `<username>/rails-example:latest`
* Tag: `latest`

---

### Step 3: Build Configuration

* Internal Port: `3000`
* External Port: `80`

Environment variables (optional):

| Key          | Value             |
| ------------ | ----------------- |
| RAILS_ENV    | production        |
| DATABASE_URL | your-database-url |

---

### Step 4: Resources Configuration

* Region: e.g., `ap-south-1`
* Resource Type: CPU

Recommended settings:

* CPU Request: `250m`
* Memory Request: `512MB`
* CPU Limit: `500m`
* Memory Limit: `1GB`

---

### Step 5: Deploy

* Strategy: Rolling
* Workload: Deployment
* Routing Policy: Latency
* Replicas: 1–2

Click Deploy.

---

## Method 2: Deploy via Git Repository

### Step 1: Select Source

* Source: Git Repository
* Provider: GitHub
* Branch: `main`

---

### Step 2: Build Configuration

* Internal Port: `3000`
* External Port: `80`

Enable:

```id="o2f7zm"
Auto-Dockerize with Runtime
```

---

### Step 3: Build and Security

NIFE automatically performs:

* SAST
* SCA
* Container scan
* IaC scan

Resolve any critical issues before proceeding.

---

### Step 4: Resources and Deploy

Use the recommended configuration above and deploy.

---

## Deployment using nifectl (CLI)

You can deploy the application using the nifectl CLI.

---

### Install nifectl CLI (Windows)

#### 1. Download

https://github.com/nifetency/nifectl/releases/tag/v4.1.3-dev

Download:

```id="zv6k1a"
nifectl-windows-amd64.zip
```

---

#### 2. Extract

* Right-click the ZIP file
* Select Extract All
* Open the extracted folder

---

#### 3. Open Terminal

* Type `cmd` in the address bar
  or
* Right-click and select Open in Terminal

---

#### 4. Verify Installation

```bash id="g2x5hd"
nifectl --help
```

---

### Step 1: Login

```bash id="8m2f5n"
nifectl auth login
```

---

### Step 2: Initialize Project

```bash id="1v7p9q"
nifectl init
```

Provide:

* Application name
* Organization
* Repository URL
* Branch (`main`)

---

### Step 3: Configure Deployment

* Deployment Type: Deployment
* Resource Type: CPU
* Replicas: 1

Ports:

* Internal: `3000`
* External: `80`

---

### Step 4: Deploy

```bash id="q3n8ru"
nifectl deploy
```

---

### Step 5: Select Region

Example:

```id="k4d7pl"
IND - Mumbai
```

---

### Step 6: Monitor Deployment

Monitor logs for:

* Validation
* Build
* Deployment

---

### Step 7: Access Application

```id="p9x2mj"
https://<your-nife-url>
```

---

## Dependencies

| Dependency          | Purpose             |
| ------------------- | ------------------- |
| Ruby                | Runtime environment |
| Rails               | Web framework       |
| Bundler             | Dependency manager  |
| SQLite / PostgreSQL | Database            |

---

## Environment Variables

| Variable     | Description                | Example                      |
| ------------ | -------------------------- | ---------------------------- |
| RAILS_ENV    | Application environment    | production                   |
| DATABASE_URL | Database connection string | postgres://user:pass@host/db |

---

## Troubleshooting

| Issue                     | Solution                             |
| ------------------------- | ------------------------------------ |
| Port already in use       | Change port or stop running process  |
| Rails not installed       | Install using `gem install rails`    |
| Bundle install fails      | Run `bundle install` again           |
| Database not created      | Run `rails db:create db:migrate`     |
| App not starting          | Check logs and dependencies          |
| Docker build fails        | Verify Dockerfile and Ruby version   |
| Deployment fails on NIFE  | Check logs, ports, and env variables |
| App not accessible        | Verify port mapping and routing      |
| Database connection error | Check DATABASE_URL and DB service    |

---
