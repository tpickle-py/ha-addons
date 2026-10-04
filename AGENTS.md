# Developer & AI Agent Guidelines for Home Assistant Add-ons Catalog (`ha-addons`)

This document provides instructions for AI agents and human maintainers on how to maintain, update, and add add-ons to this catalog repository.

---

## 1. Repository Purpose & Architecture

This repository (`tpickle-py/ha-addons`) is a **Home Assistant Add-on Catalog Repository**.
It does **not** contain application business logic or backend code. Instead, it:
1. Presents an add-on catalog to Home Assistant Supervisor via `repository.yaml`.
2. Hosts manifests, icons, documentation, and build specifications for each add-on.
3. Automatically synchronizes with upstream application releases (such as `tpickle-py/security-hawk`) via `hassio-addons/repository-updater`.

---

## 2. Repository Layout

```
ha-addons/
├── .github/
│   └── workflows/
│       ├── lint.yaml                # Pre-commit & style linting
│       └── repository-updater.yaml  # Automated catalog synchronization workflow
├── .addons.yml                      # Configuration mapping for repository-updater
├── repository.yaml                  # HA Catalog metadata (name, url, maintainer)
├── README.md                        # Catalog overview and one-click My HA installation
├── AGENTS.md                        # This documentation file
└── security_hawk/                   # Add-on directory for Security Hawk
    ├── config.yaml                  # Add-on configuration manifest (options, schema, ports)
    ├── build.yaml                   # Build targets and multi-arch base images
    ├── DOCS.md                      # In-depth usage documentation displayed in HA
    ├── CHANGELOG.md                 # Add-on release changelog
    ├── icon.png                     # Square icon for the Add-on Store
    ├── logo.png                     # Wide logo banner
    └── translations/                # Configuration schema i18n
        └── en.yaml
```

---

## 3. How Automated Updates Work (`repository-updater`)

The workflow `.github/workflows/repository-updater.yaml` is triggered by:
- **`repository_dispatch`** with event type `update` (sent by upstream app repos like `security-hawk`).
- **`workflow_dispatch`** for manual runs.
- **Scheduled cron** (every Sunday at 03:00 UTC).

### The `.addons.yml` Configuration:
```yaml
security_hawk:
  repository: "tpickle-py/security-hawk"
  target: "security_hawk"
  image: "ghcr.io/tpickle-py/security-hawk/{arch}"
```

- `repository`: The GitHub repository where releases and source files live.
- `target`: The subfolder within the upstream repository that contains the add-on files (`config.yaml`, `DOCS.md`, etc.).
- `image`: The GHCR multi-arch image pattern that Home Assistant pulls.

### Key Requirements for `repository-updater` to Succeed:
1. **GitHub Releases Required**: `repository-updater` only pulls files from the commit associated with the **latest published GitHub Release** (`get_releases()`). Unreleased tags or commits on `master` are ignored.
2. **Matching Target Path**: The files must exist inside the `target:` subdirectory (`security_hawk/`) of the upstream repository.
3. **Repository Secrets**: `UPDATER_TOKEN` must be configured with write access to push commits to `ha-addons`.
4. **GitHub Profile Display Name**: PyGithub requires the committing GitHub user to have a non-empty Profile Name set.

---

## 4. How to Add a New Add-on to This Catalog

To add a new application to this catalog:

1. **Create the Add-on Directory**:
   ```bash
   mkdir -p my_addon/translations
   ```
2. **Add Required Files**:
   - `my_addon/config.yaml`: Define name, slug, version, description, options, schema, `init: false`, `hassio_api: true`.
   - `my_addon/build.yaml`: Define base images and architecture mapping.
   - `my_addon/DOCS.md`: Comprehensive user guide.
   - `my_addon/icon.png` (square PNG) and `my_addon/logo.png` (rectangular PNG).
   - `my_addon/translations/en.yaml`: English labels and descriptions for options.

3. **Register in `.addons.yml`**:
   ```yaml
   my_addon:
     repository: "tpickle-py/my-addon-repo"
     target: "my_addon"
     image: "ghcr.io/tpickle-py/my-addon-repo/{arch}"
   ```

4. **Update `README.md`**:
   - Add the new add-on entry under the **Add-ons Provided by this Repository** table.

5. **Commit and Push**:
   ```bash
   git add -A
   git commit -m "feat: add my_addon to catalog"
   git push origin main
   ```
