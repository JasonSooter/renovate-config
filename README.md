# renovate-config

Shared [Renovate](https://docs.renovatebot.com/) preset for my repositories.

In a repo, `renovate.json`:

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": ["local>JasonSooter/renovate-config"]
}
```

What it sets: weekly schedule (Europe/Berlin), semantic commits, one grouped
PR for minor and patch updates, weekly lockfile maintenance, and security PRs
outside the schedule.

Security works in tandem with GitHub:

- **Dependabot alerts: on.** They cover the whole dependency graph, transitive
  packages included. Renovate's `vulnerabilityAlerts` reads them and opens
  fix PRs labelled `security`.
- **Renovate `osvVulnerabilityAlerts`: on.** Covers direct dependencies from
  the OSV database.
- **Dependabot version and security updates: off.** Renovate does all updates.
