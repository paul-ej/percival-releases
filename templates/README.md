# Percival deployment templates

These are editable starting points. Download the raw file rather than copying a GitHub HTML page. Replace `company.example`, all sample service URLs and SSO placeholders. Confirm the service is provisioned before rollout.

## Files and scope

| File | Destination |
| --- | --- |
| `macos/com.paul-ej.percival.mac.plist` | Raw preference settings; upload for domain `com.paul-ej.percival.mac` in Intune Preference file or Jamf Application & Custom Settings. |
| `macos/percival-system.mobileconfig` | Complete system-scope forced-preference profile, including Iru Custom Profile workflows. |
| `macos/percival-user.mobileconfig` | Complete user-scope profile; use only when the enrollment and MDM support the intended user channel. |
| `macos/require-declarative-policy.plist` | Advanced bootstrap dictionary; merge into forced legacy preferences only when a working declarative policy is required and ready. |
| `ios/appconfig.plist` | Managed iOS/iPadOS app configuration dictionary, currently for `com.paul-ej.percival`. |
| `sso/*-connection-sheet.json` | Human-readable setup handover, not an import schema. |

Replace profile identifiers and payload UUIDs with organisation-owned values when creating a profile. Preserve the intended identity on later updates according to your MDM's rules. System and User are alternatives; do not deploy both for the same keys. A raw plist is not a complete mobileconfig and copying preferences onto disk does not establish administrator enforcement.

## Defaults and keys

The examples configure `ServerURL` and exact `SignInDomains`, hide Organization setup with Boolean `ShowOrganizationSetup=false`, and leave remote generation disabled. They omit environment restrictions. An empty `AllowedEnvironmentIDs` array denies every environment; obtain real UUIDs before adding an allowlist. `DefaultEnvironmentID` must be within it when supplied.

The URLs identify the Percival authentication/workspace service, not an Entra/Google login page or SAML ACS. Domain discovery finds a destination and does not authenticate or grant membership. Use real Booleans, not strings such as `"true"`.

`RequireDeclarativePolicy=true` can prevent launch and cold intent access until valid declarative policy arrives. Do not enable it as part of an ordinary legacy-only rollout. The bootstrap and declarative policy are delivered separately; do not place the bootstrap key inside the ManagedApp data asset. Test startup, update and removal on an enrolled physical device.

No passwords, OAuth client secrets, session tokens, signing private keys or actual customer data belong in these files. Review your customised files before MDM assignment; test pilot and rejected users and record certificate renewal ownership.
