<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="images/ZaneOps-HORIZONTAL-WHITE.svg">
    <source media="(prefers-color-scheme: light)" srcset="./images/ZaneOps-HORIZONTAL-BLACK.svg">
    <img src="./images/ZaneOps-HORIZONTAL-WHITE.svg" alt="Zane logo"  height="100" />
  </picture>
</p>

<div align="center">
<p>
your all-in-one self-hosted platform for deploying apps with ✨ zen ✨.
</p>


<img  src="https://img.shields.io/discord/1348034264670933002?logo=discord&style=for-the-badge&label=Community">

<picture>
 <source media="(prefers-color-scheme: dark)" srcset="https://zaneops.dev/images/project-detail-dark.png">
    <source media="(prefers-color-scheme: light)" srcset="https://zaneops.dev/images/project-detail-light.png">
<img src="https://zaneops.dev/images/project-detail-light.png" />
</picture>

</div>


## Quick start: run locally (self-contained, no Docker)

This repository includes a fully self-contained development setup. You’ll run the backend with SQLite and an in-memory cache, plus the frontend dev server—no Docker, Postgres, Redis, or external services required.

Follow these steps right after cloning. Each step includes the expected outcome so you can verify progress.

1) Enable pnpm via Corepack

```zsh
corepack enable
corepack prepare pnpm@latest --activate
```

Expected: No errors; pnpm is active (pnpm -v prints a version if you check).

2) Clone the repository and enter it

```zsh
git clone https://github.com/MarcosMasip/zane-ops-self-contained.git
cd zane-ops-self-contained
```

Expected: The directory is created and you are inside it.

3) Switch to the runnable branch

```zsh
git checkout feat/clean-new-main
```

Expected: Branch changes to `feat/clean-new-main`.

4) Install workspace dependencies

```zsh
pnpm install
```

Expected: Node dependencies install for all workspace packages without errors.

5) Start the app (backend + frontend, SQLite; self-contained)

```zsh
pnpm run dev:local
```

Expected:
- A migration phase runs for the backend (SQLite). You’ll see either “No migrations to apply.” or a sequence of “Applying … OK”.
- Backend starts at http://localhost:8000/ with a line like “Starting ASGI/Daphne … at http://0.0.0.0:8000/”.
- Frontend dev server starts at http://localhost:5173/ with a banner showing Local and Network URLs.
- You might see harmless warnings (Corepack/pnpm, uv dev-dependencies deprecation, Vite optimizeDeps). These do not affect running locally.

6) Verify it’s working

- Frontend UI: open http://localhost:5173/
  - Expected: App UI loads. You may see a small “YOU ARE IN DEV” banner—this only indicates a development build.
- Backend health: open http://localhost:8000/api/ping
  - Expected: 200 OK JSON (e.g., `{ "status": "ok" }`).

Notes
- This run mode is isolated; no Docker, Redis, Postgres, or Temporal is needed.
- Stopping: press Ctrl+C in the terminal running `pnpm run dev:local` to stop both servers.
- Minimal outbound calls: the frontend checks the latest release from a public CDN periodically (read‑only). If offline, it fails quietly. External links (Docs/Discord/GitHub) only open if you click them.

Optional: production-like preview without the dev banner

```zsh
pnpm --filter frontend run build
pnpm --filter frontend run preview -- --host
```

Expected: Vite preview serves the built frontend (typically at http://localhost:4173/) without the dev banner. Backend can keep running from step 5.


## What is ZaneOps ?

ZaneOps is a **beautiful, self-hosted, open-source** platform for hosting static sites, web apps, databases, services (like Supabase, WordPress, Ghost), workers, or anything else you need—whether you're launching a startup or managing an enterprise.  

It is a **free** and **open-source** alternative to platforms like **Heroku**, **Railway**, and **Render**, leveraging the **scalability** of [Docker Swarm](https://docs.docker.com/engine/swarm/) and the **flexibility** of [Caddy](https://caddyserver.com/).  


## 🚀 Installation

You can install zaneops like this :

```shell
curl -fsSL https://cdn.zaneops.dev/install.sh | sudo bash
```

> [!NOTE]
> If you have any issue, be sure to checkout the [instructions steps](https://zaneops.dev/installation/) in the documentation for more detailled setup.

## 📸 Some Screenshots


1. Onboarding

  <p align="center">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="./images/create-user-dark.png">
      <source media="(prefers-color-scheme: light)" srcset="./images/create-user-light.png">
      <img src="./images/create-user-dark.png" alt="Login page" />
    </picture>
  </p>

2. Login

  <p align="center">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="./images/login-dark.png">
      <source media="(prefers-color-scheme: light)" srcset="./images/login-light.png">
      <img src="./images/login-dark.png" alt="Login page" />
    </picture>
  </p>

3. Dashboard

  <p align="center">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="./images/dashboard-dark.png">
      <source media="(prefers-color-scheme: light)" srcset="./images/dashboard-light.png">
      <img src="./images/dashboard-dark.png" alt="Login page" />
    </picture>
  </p>

4. Project detail

  <p align="center">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="./images/project-detail-dark.png">
      <source media="(prefers-color-scheme: light)" srcset="./images/project-detail-light.png">
      <img src="./images/project-detail-dark.png" alt="Login page" />
    </picture>
  </p>

5. HTTP logs

  <p align="center">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="./images/http-logs-dark.png">
      <source media="(prefers-color-scheme: light)" srcset="./images/http-logs-light.png">
      <img src="./images/http-logs-dark.png" alt="Login page" />
    </picture>
  </p>

6. Runtime logs

  <p align="center">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="./images/logs-octane-dark.png">
      <source media="(prefers-color-scheme: light)" srcset="./images/logs-octane-light.png">
      <img src="./images/logs-octane-dark.png" alt="Login page" />
    </picture>
  </p>

> [!NOTE]
> More screenshots [in the documentation](https://zaneops.dev/screenshots/)

## ❤️ Contributing

Interested in contributing? Check out the [contribution guidelines](./CONTRIBUTING.md).

## 🙏 Credits

- [Plane](https://github.com/makeplane/plane): for giving us content for the contributions templates (contribution
  guidelines).
- [Coolify](https://github.com/coollabsio/coolify) and [Dokploy](https://github.com/dokploy/dokploy) which we used inspired ourselves from a lot.
