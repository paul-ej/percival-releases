# Percival downloads

Public release assets and configuration templates for Percival. Application source and internal operations documentation are maintained separately.

## Mac installer

Choose a published version from [Releases](https://github.com/paul-ej/percival-releases/releases). If no release is listed, no production installer is available yet. Public installers are intended for Apple silicon on macOS 26 or later and are Developer ID signed and notarized.

Each production release contains:

- `Percival-macOS-arm64.pkg` — stable asset name, available through [the latest release download](https://github.com/paul-ej/percival-releases/releases/latest/download/Percival-macOS-arm64.pkg) once a release exists.
- `Percival-VERSION-macOS-arm64.pkg` — versioned asset for pinned MDM deployments.
- `SHA256SUMS` and `release.json` — release metadata and checksums.
- `Percival-deployment-templates.zip` — the templates accompanying that release.

Quit Percival before updating. Record a versioned package and its checksum for your organisation's rollout. A new public release does not automatically update packages already uploaded to Intune, Iru, Jamf or Fleet. No built-in automatic updater is implied.

## Template directories

- [macOS](templates/macos): raw preference plist, system and user mobileconfig variants, optional declarative-policy bootstrap.
- [iOS/iPadOS](templates/ios): managed AppConfig dictionary; the Mac PKG does not install on iOS.
- [SSO](templates/sso): Entra, Google Workspace and other IdP connection worksheets.
- [Template instructions](templates/README.md): replacement values, types, scope and policy boundaries.

Templates contain example domains and service addresses. Replace them before assignment. Do not add credentials or private keys. SSO worksheets are handover documents, not a supported import API. The template licence applies to the templates, not to the Percival application.
