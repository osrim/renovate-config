# renovate-config

This repository holds the shared Renovate preset for osrim repositories. The
preset lives in `default.json`, and the `description` field in that file
explains the reason for each rule.

## What the preset does

The preset extends `config:recommended` and adds these behaviors:

- **Release age:** Renovate proposes a version only after it has been public
  for 7 days. A version without a release timestamp counts as too new.
- **Commit type:** Every update uses the `chore` commit type, so a changelog
  built from commit types leaves updates out.
- **Digest pinning:** Renovate pins GitHub Actions and Docker images to a
  digest, and updates the digest and its version comment together.
- **Automerge:** Updates merge on their own once they pass the release age and
  every status check. Major updates wait for review.

## Use the preset

To use the preset, put this in your repository's `renovate.json`:

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": ["github>osrim/renovate-config"]
}
```

## Add project-specific rules

Add project-specific rules, such as package groups, to the same
`renovate.json`. Your settings override the preset's, and your `packageRules`
apply after the preset's rules.
