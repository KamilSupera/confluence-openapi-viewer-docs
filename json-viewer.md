# JSON & YAML Viewer for Confluence

Renders JSON or YAML as a collapsible tree, or as formatted text, inside a Confluence Cloud page.

- [Privacy policy](privacy.md) · [Support](support.md)

## Getting started

1. Install the app from the Atlassian Marketplace.
2. Edit a page, type `/JSON` and insert **JSON & YAML Viewer**.
3. Paste your JSON or YAML into the macro body. For YAML, paste into a code block (type ` ``` ` inside the macro first) so indentation is kept.
4. Optional: open the macro settings to switch to a URL or a page attachment, change the collapse depth, show item counts, sort keys, limit the height, or switch to formatted text.

## Sources

- **Macro body** (default): the content lives in the page. Readers never fetch anything.
- **URL**: the reader's browser fetches the file; the host must allow cross-origin requests. Optional basic or bearer authentication.
- **Page attachment**: upload the file to the page; your CI can update it with one `curl` call, see [Publish from CI](ci.md).

## Migrating from JSON Viewer & Editor (Connect)

Insert JSON & YAML Viewer next to the old macro, paste the same content into its body, remove the old macro.

## Limits

- Very large documents (thousands of nodes) render, but start collapsed; set "Collapse below depth" to 1 or 2.
- Editing values in place is not supported.
