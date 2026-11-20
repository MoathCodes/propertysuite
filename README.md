# Property Suite

Property management that runs on your own computer. Track buildings, tenants,
leases, rent and maintenance, in English or Arabic. Your records stay on your
machine.

This repository holds the releases: the Docker setup file and the signed
update notices. The source code is not public.

## Run it with Docker

You need Docker: Docker Engine on Linux, Colima or Docker Desktop on a Mac,
Docker Desktop on Windows.

1. Make a folder and save [`compose.yaml`](compose.yaml) inside it.
2. In that folder, run:

   ```bash
   docker compose up -d
   docker compose logs propertysuite
   ```

3. Open the setup link from the log. Pick a language, enter your company name
   and the owner's details. "Start with sample data" loads a ready-made company
   to explore.

Then open <http://localhost:8080>. It starts by itself whenever the computer
starts. Your data lives in the `propertysuite-data` Docker volume.

## Update

When the System page says a new version is ready:

1. Press "Back up now" on the System page.
2. In the folder, run:

   ```bash
   docker compose pull
   docker compose up -d
   ```

Your data stays in its volume. Docker installs have no automatic rollback, so
always take the backup first.

## Settings

Put any of these in a `.env` file next to `compose.yaml`, one per line.

| Setting | Default | What it does |
| --- | --- | --- |
| `PS_HTTP_PORT` | `8080` | The port on your computer |
| `PS_BASE_URL` | `http://localhost:8080` | The address people type, used in the setup link |
| `PS_IMAGE` | `ghcr.io/moathcodes/propertysuite:latest` | Which version to run |

Free for up to 50 units. A licence file adds reports.
