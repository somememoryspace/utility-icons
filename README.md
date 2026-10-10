# authentik-icons
Generic Repository for Hosting Authentik Icons

## Secret scan
`gitleaks` with `.gitleaks.toml` (default rules, narrow commented allowlists) is staged in `.forgejo/workflows/secret-scan.yaml` (pull requests and pushes to `main`, no secrets); Actions is off for this repository until `actions = true` in `px-tofu/tofu/forgejo/locals.tf` (STD-WLD-04.R9). Locally, `scripts/hooks/pre-commit` scans staged changes; it needs `gitleaks` on PATH (`brew install gitleaks`). Fix a false positive in `.gitleaks.toml` or `.gitleaksignore` with a reason, never with `--no-verify`; a real finding is rotated first, then removed.

```bash
git config core.hooksPath scripts/hooks   # once per clone
gitleaks git . --log-opts=HEAD --redact   # whole history of the current branch
```
