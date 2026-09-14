# Support

Email: kamil.supera.ks@gmail.com

Include your Confluence site URL, the page where the macro is used, and the error text shown by the macro. Response within two business days.

## Common issues

**"The host probably does not allow cross-origin requests (CORS)"** — the server hosting your definition does not send `Access-Control-Allow-Origin`. Upload the file as a page attachment and switch the macro to *Page attachment*, or publish the file on a host that allows cross-origin requests (GitHub raw, GitHub Pages, S3 with CORS).

**"Attachment … not found on this page"** — the file name must match the attachment on this exact page, including extension.

**Export to PDF / Word shows a placeholder** — export rendering is not supported in this version.
