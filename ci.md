# Publish the definition from CI

Set the macro to **Page attachment** with the file name your pipeline uploads (for example `openapi.yaml`). Each pipeline run uploads a new version through the Confluence REST API; the macro renders the newest version on the next page view.

1. Create an Atlassian API token for a user who can edit the page: https://id.atlassian.com/manage-profile/security/api-tokens
2. Store `CONFLUENCE_USER` (email) and `CONFLUENCE_TOKEN` as CI secrets.
3. Find the page ID in the page URL.
4. Add one step:

```bash
curl --fail -u "$CONFLUENCE_USER:$CONFLUENCE_TOKEN" -X PUT \
  -H "X-Atlassian-Token: nocheck" -F "file=@openapi.yaml" -F "minorEdit=true" \
  "https://<site>.atlassian.net/wiki/rest/api/content/<pageId>/child/attachment"
```

Same file name = new attachment version. Works from GitHub Actions, GitLab CI, Bitbucket Pipelines or any shell.
