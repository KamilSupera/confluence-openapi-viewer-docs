# Security — OpenAPI (Swagger) Viewer for Confluence

## Architecture

- Built on Atlassian Forge. The app has no servers, databases or backend functions of its own; it consists only of two static UI bundles (the macro viewer and its configuration form) hosted by Atlassian.
- Forge scope: `read:attachment:confluence` only, used to read the attachment selected in the macro on the current page. The app cannot read page content and cannot write to Confluence.
- Requests to Confluence go through the Forge bridge and run with the permissions of the user viewing the page.

## Data handling

- Macro settings (definition URL or attachment name, display options) are stored by Atlassian in the Confluence page, under your site's data residency.
- The app stores no secrets. It does not accept usernames, passwords or tokens; definitions behind authentication should be published as a page attachment instead.
- The definition is fetched by the reader's browser directly from the configured URL, or from the page attachment through the Confluence API. It is rendered in the browser and never sent to the vendor or any third party.
- No analytics, telemetry, logging or third-party processors.
- The optional online validator is off by default. When an admin enables it, the reader's browser sends the definition URL to the validator they configure.

## Encryption

- All traffic between the browser, Atlassian and Confluence uses HTTPS (TLS), enforced by the Forge platform.
- Data at rest (page content and attachments) is encrypted by Atlassian as part of Confluence Cloud.

## Egress

The app declares `fetch.client: *` and `images: *` because the definition URL is chosen by the customer. These requests are made only by the reader's browser, only to the URL configured in the macro and to the server URLs inside the definition when *Try it out* is enabled (disabled by default).

## Vulnerability management

- Dependencies are pinned in `package-lock.json` and checked with `npm audit` before every release.
- Security fixes are released as Forge minor versions and roll out automatically to all installations.
- Confirmed vulnerabilities are prioritised by severity and fixed as soon as practicable.

## Reporting a vulnerability

Email kamil.supera.ks@gmail.com with the subject "Security". We acknowledge reports within two business days and keep reporters informed until a fix is released.
