# MijnRelaxNow

**MijnRelaxNow** is the customer self-service portal for **Relax Now Verzekeringen Nederland B.V.** (fictional).  
Customers use MijnRelaxNow to submit and track service requests, upload documents, and communicate with support teams.

This repository is intentionally used as a **realistic test application** for:
- Custom packaging experiments
- CI/CD integration
- Application security scanning (e.g. Veracode)


---

## Purpose

MijnRelaxNow represents a typical insurer customer portal where policyholders can:

- Submit support requests (policy questions, claim follow-ups, document uploads)
- Attach files (PDFs, images)
- Track request status (Open / Pending / Closed)
- Communicate with service staff via request comments
- Access a branded portal aligned with the `relaxnow.nl` domain

The application is **not production software**, but a credible stand-in for demos, tooling tests, and security workflows.

---

## Technology Stack

- **Language / Runtime:** PHP 8.x
- **Dependency management:** Composer
- **Web server:** Apache or Nginx
- **Architecture:** Traditional MVC-style PHP app
- **Templates:** Server-side rendered templates
- **Storage (dev):** File-based / lightweight DB
- **Local dev:** Docker & Docker Compose

---

## Repository Structure

    .
    ├── bin/                 CLI helpers
    ├── config/              Application configuration
    ├── docker/              Docker-related files
    ├── public/              Web root
    ├── src/                 Application code
    ├── templates/           UI templates
    ├── tests/               Test code
    ├── uploads/             User-uploaded files
    ├── composer.json
    ├── composer.lock
    ├── Dockerfile
    └── docker-compose.yml

---

## Prerequisites

- PHP **8.0+**
- Composer
- Apache or Nginx  
- (Optional) Docker and Docker Compose

---

## Local Installation

### 1. Clone the repository

    git clone https://github.com/relaxnow-nl/mijnrelaxnow.git
    cd mijnrelaxnow

### 2. Install dependencies

    composer install

### 3. Configure environment

    cp .env.example .env

Update `.env` with appropriate local values (paths, secrets, branding).

### 4. Prepare runtime directories

    mkdir -p data uploads logs tmp/cache
    chmod 755 data uploads logs tmp/cache

### 5. Run locally

Using PHP’s built-in web server:

    php -S localhost:8080 -t public

Open the portal at:  
http://localhost:8080

---

## Running with Docker

For a fully isolated and repeatable setup:

    docker compose up --build

This approach is recommended for CI/CD and packaging tests.

---

## Packaging Notes (for security tooling)

This project is well suited for custom packaging experiments:

- Composer lockfile ensures repeatable dependency resolution
- Clear separation of `public/` (web root) and application code
- Includes file upload paths and form handling
- Typical exclusions during packaging:
  - `tests/`
  - `docker/`
  - Local runtime folders (`logs/`, `tmp/`, `uploads/`)

Example production-style dependency install:

    composer install --no-dev --prefer-dist --no-interaction

---

## Intended Usage

- Demonstrating secure SDLC practices
- Testing custom packagers and build scripts
- Validating CI/CD and security scanning integrations
- Training and demo environments

---

## License

This is a **fictional internal demo project**.  
If redistributed, ensure licensing aligns with your intended use.

---

## Reference / Upstream Inspiration

This project is based on and inspired by the open-source **Support Portal** project:

https://github.com/jeffcaldwellca/support-portal

