# SuiteCRM Docker Guide - Fast Evaluation Route

This route is meant only for a short local class evaluation. It uses Bitnami's **legacy** SuiteCRM image because SuiteCRM does not provide a current official free Docker image. Docker Hub states that the legacy image is no longer updated or supported. Do not expose it to the internet or use it for real customer data.

## Time target

Allow about 15-30 minutes, mostly for downloading the images and first startup.

## 1. Install Docker Desktop

Download Docker Desktop from the official Docker website, install it, and wait until it says the engine is running.

## 2. Create a folder

Create a folder named `suitecrm-evaluation`. Inside it, create a file named `compose.yaml` with this content:

```yaml
services:
  database:
    image: mariadb:10.11
    restart: unless-stopped
    environment:
      MARIADB_DATABASE: suitecrm
      MARIADB_USER: suitecrm
      MARIADB_PASSWORD: suitecrm_local_only
      MARIADB_ROOT_PASSWORD: root_local_only
    volumes:
      - suitecrm_db:/var/lib/mysql

  suitecrm:
    image: bitnamilegacy/suitecrm:8.8.1-debian-12-r3
    restart: unless-stopped
    depends_on:
      - database
    ports:
      - "8080:8080"
    environment:
      SUITECRM_DATABASE_HOST: database
      SUITECRM_DATABASE_PORT_NUMBER: 3306
      SUITECRM_DATABASE_NAME: suitecrm
      SUITECRM_DATABASE_USER: suitecrm
      SUITECRM_DATABASE_PASSWORD: suitecrm_local_only
      SUITECRM_USERNAME: admin
      SUITECRM_PASSWORD: ChangeMeLocal123!
      SUITECRM_EMAIL: mubarekidris.r@gmail.com
      SUITECRM_HOST: localhost:8080
      SUITECRM_SKIP_BOOTSTRAP: "no"
      ALLOW_EMPTY_PASSWORD: "no"
    volumes:
      - suitecrm_data:/bitnami/suitecrm

volumes:
  suitecrm_db:
  suitecrm_data:
```

The password is only a local evaluation default. Do not reuse it for any real account.

## 3. Start SuiteCRM

Open PowerShell or Terminal in that folder and run:

```powershell
docker compose up -d
```

Watch startup:

```powershell
docker compose logs -f suitecrm
```

The first start may take several minutes. Press `Ctrl+C` when the log becomes quiet, then open:

http://localhost:8080

Sign in with:

- Username: `admin`
- Password: `ChangeMeLocal123!`

If the page is not ready, wait two minutes and run:

```powershell
docker compose ps
docker compose logs --tail 100 suitecrm
```

## 4. Create safe sample records

Use made-up class data only.

1. Open **Contacts** and create `Jordan Lee`, email `jordan@example.test`.
2. Open **Leads** and create `Taylor Morgan`, company `North Star Demo`.
3. Add one Opportunity if the dashboard needs data.
4. Open the dashboard and add a Leads or Opportunities dashlet if the page is empty.
5. Open **Reports**, create a simple Leads report, and display it as a table or chart.

## 5. Capture the five screenshots

Use Windows Snipping Tool (`Windows + Shift + S`) or the macOS screenshot shortcut. Save as PNG with these exact names:

1. `login.png` - capture before signing in
2. `dashboard.png`
3. `contacts.png`
4. `leads.png`
5. `reports.png`

Copy the five files into this repo's `screenshots/` folder and replace the placeholders. Keep the page title visible. Do not show passwords, real customer data, bookmarks, or unrelated tabs.

## 6. Finish the worksheet

Open `open_source_evaluation.md` and replace every bracketed prompt with what actually happened. Check off all five screenshot items.

## 7. Stop or reset the evaluation

Stop it without deleting data:

```powershell
docker compose down
```

Remove the local containers and all evaluation data:

```powershell
docker compose down -v
```

## Troubleshooting

### Port 8080 is already in use

Change this line:

```yaml
- "8080:8080"
```

to:

```yaml
- "8081:8080"
```

Change `SUITECRM_HOST` to `localhost:8081`, restart, and open `http://localhost:8081`.

### The site keeps loading or shows a database error

Run:

```powershell
docker compose ps
docker compose logs --tail 150 database
docker compose logs --tail 150 suitecrm
```

Wait until MariaDB has finished initializing. If this is a brand-new install and the volumes contain a failed partial setup, reset with `docker compose down -v`, then start again.

### Apple Silicon warning

The chosen tag may run through emulation depending on the image architecture. If Docker reports an unsupported platform and will not start, use the XAMPP route instead rather than changing to an unverified image.

## Important limitation

This Docker route is convenient for screenshots, but the image is frozen and receives no security updates. The assignment evaluation is not evidence that it is safe for production.
