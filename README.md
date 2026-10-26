# OpenBooks on GitHub Actions

Temporary OpenBooks web UI hosted on a GitHub Actions runner and exposed through ngrok. Start it only when needed, download files directly through the browser, then cancel the workflow.

## One-time setup

1. In your ngrok account, copy your auth token.
2. In this repository, open **Settings → Secrets and variables → Actions → New repository secret**.
3. Add these repository secrets:
   - `NGROK_AUTHTOKEN` — your ngrok auth token.
   - `OPENBOOKS_PASSWORD` — a strong password for the public tunnel. The tunnel uses HTTP Basic Authentication with username `openbooks`.

Do not put either secret in workflow files or commit them to the repository.

## Start a session

1. Open the repository's **Actions** tab.
2. Select **OpenBooks (temporary)**.
3. Click **Run workflow**.
4. Open the running job's **Summary**. Use the HTTPS URL shown there.
5. Authenticate with username `openbooks` and the password stored in `OPENBOOKS_PASSWORD`.
6. Search and download books through the OpenBooks UI. Downloads are delivered to your browser; the runner does not keep a persistent library.
7. When finished, return to Actions and cancel the workflow.

## Notes

- The instance exists only while the workflow is running.
- The URL is temporary and changes between runs.
- The tunnel is protected with HTTP Basic Authentication.
- GitHub-hosted jobs have a finite maximum runtime; this workflow is configured for 350 minutes.
- OpenBooks requires an IRC nickname; this workflow uses `githubactions`.
- The workflow requires outbound connectivity to ngrok and the IRC network used by OpenBooks.
