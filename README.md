# Home Assistant Add-on Repository

![Project Stage][project-stage-shield]
![Maintenance][maintenance-shield]
[![License][license-shield]](LICENSE.md)

[![Open your Home Assistant instance and show the add-on store with this repository pre-filled.][my-ha-badge]][my-ha-url]

## About

This repository provides Home Assistant Add-ons for **Security Hawk** and related security monitoring tooling.

Home Assistant allows users to add custom add-on repositories to easily install, configure, and maintain community apps directly from the Supervisor Add-on Store.

## Installation

### Method 1: My Home Assistant (Recommended)

Click the button below to automatically open your Home Assistant instance and add this repository:

[![Open your Home Assistant instance and show the add-on store with this repository pre-filled.][my-ha-badge]][my-ha-url]

### Method 2: Manual Installation

1. In your Home Assistant UI, navigate to **Settings** &rarr; **Add-ons** &rarr; **Add-on Store**.
2. Click the three dots (overflow menu) in the top-right corner and select **Repositories**.
3. In the repository URL field, paste:
   ```txt
   https://github.com/tpickle-py/ha-addons
   ```
4. Click **Add**, then close the dialog.
5. Reload the Add-on Store or wait a few seconds. **Security Hawk** will now appear in your add-on store list!

---

## Add-ons Provided by this Repository

### &#10003; [Security Hawk][addon-security-hawk]

![Latest Version][security-hawk-version-shield]
![Supports aarch64 Architecture][security-hawk-aarch64-shield]
![Supports amd64 Architecture][security-hawk-amd64-shield]

Interactive multi-floor plan viewer and security monitoring hub for Home Assistant. Features live entity state, low-latency camera streaming, motion traversal trails, building roll-ups, alert rules, and direct full-screen kiosk mode for wall displays and TVs.

[:books: Security Hawk Add-on Documentation][addon-doc-security-hawk]

---

## Architecture Support

| Architecture | Supported |
| :--- | :---: |
| `amd64` (x86_64, standard PC/Intel NUC/VM) | :white_check_mark: |
| `aarch64` (Raspberry Pi 4/5 64-bit, ODROID, etc.) | :white_check_mark: |

---

## Releases & Versioning

Releases follow [Semantic Versioning][semver] (`MAJOR.MINOR.PATCH`):

- **MAJOR**: Incompatible or breaking changes.
- **MINOR**: Backwards-compatible new features and enhancements.
- **PATCH**: Backwards-compatible bug fixes and package updates.

---

## Support & Feedback

- For issues and feature requests regarding the **Security Hawk Add-on**, open an issue on the [Security Hawk repository][security-hawk-issues].
- For issues regarding this **Add-on repository catalog** or packaging, open an issue in this repository.

---

## License

MIT License &copy; 2026 Travis Pickle. See [LICENSE.md](LICENSE.md) for details.

[my-ha-badge]: https://my.home-assistant.io/badges/supervisor_add_addon_repository.svg
[my-ha-url]: https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https%3A%2F%2Fgithub.com%2Ftpickle-py%2Fha-addons
[project-stage-shield]: https://img.shields.io/badge/project%20stage-production%20ready-brightgreen.svg
[maintenance-shield]: https://img.shields.io/maintenance/yes/2026.svg
[license-shield]: https://img.shields.io/github/license/tpickle-py/ha-addons.svg
[addon-security-hawk]: security_hawk/
[addon-doc-security-hawk]: security_hawk/DOCS.md
[security-hawk-issues]: https://github.com/tpickle-py/security-hawk/issues
[security-hawk-version-shield]: https://img.shields.io/badge/version-v0.3.4-blue.svg
[security-hawk-aarch64-shield]: https://img.shields.io/badge/aarch64-yes-green.svg
[security-hawk-amd64-shield]: https://img.shields.io/badge/amd64-yes-green.svg
[semver]: https://semver.org/
