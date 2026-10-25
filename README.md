# renovate-apm-test

## Current behavior

In fresh CI, Renovate updates `find-skills` from `v1.7.3` to `v1.7.4`. APM targets Copilot but reports `no trustworthy local deployment baseline` and skips deployment; [PR #1](https://github.com/juancarlosjr97/renovate-apm-test/pull/1) deletes the committed `.agents/skills/find-skills/SKILL.md`.

[Reproduction log](https://developer.mend.io/github/juancarlosjr97/renovate-apm-test/-/job/714e153c-2128-42dd-9c5e-0d24ff3687b8).

Error is 

```
{
  "durationMs": 2202,
  "stdout": "[>] Installing dependencies from apm.yml...\n[>] Resolving skills-find-skills...\n[i] Targets: copilot  (source: apm.yml)\n  [+] github.com/vercel-labs/skills/skills/find-skills#v1.7.4 #v1.7.4 @a80e4c9d\n  |-- (files unchanged)\n[i] Cleaned 2 stale deployed files for vercel-labs/skills/skills/find-skills\n  [!] Skipped .agents/skills/find-skills/SKILL.md: no trustworthy local \ndeployment baseline. Preserve your changes before reinstalling with --force.\n  [i] Skipped inactive experimental resolver for target 'copilot-app' during \nlockfile reconciliation.\n  [i] Skipped inactive experimental resolver for target 'copilot-cowork' during \nlockfile reconciliation.\n[*] Installed 1 APM dependency (2 stale files cleaned) in 1.1s.\n",
  "stderr": "WARNING apm_cli.policy.discovery Policy repo juancarlosjr97/.github-private not found (or [REDACTED] private-repo read scope). If your org publishes policy in .github-private, ensure the token has Contents:read permission on that repo.\n"
}
```

## Expected behavior

Update the dependency and its generated Copilot skill without deleting the committed skill or requiring manual cleanup.

## Link to the Renovate issue or Discussion

Not opened yet.