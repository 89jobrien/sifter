# Sifter

> Evidence-driven portfolio triage for public repositories.

Sifter collects observable public evidence from GitHub repositories, evaluates it against a versioned policy, and produces explainable project assessments. It helps maintainers decide which projects to promote, support, incubate, retain as reference, consolidate, or archive.

## Why Sifter

Public GitHub profiles often mix flagship products, active experiments, reusable components, historical artifacts, and superseded prototypes. GitHub gives each repository similar visual weight, while repository metadata alone rarely proves whether a project is usable, maintained, safely adoptable, or strategically distinct.

Sifter turns repository evidence into a deliberate portfolio-maintenance workflow. It is not a popularity leaderboard and does not judge developers.

## Principles

- Evidence outranks claims.
- Verified, declared, unknown, failed, and not-applicable evidence remain distinct.
- Technical evidence score and portfolio fit are separate decisions.
- Adoption signals are capped and cannot disqualify early projects.
- Every score, maturity class, finding, and recommendation must be explainable.
- Sifter operates read-only by default.

## Intended workflow

```text
GitHub evidence
  → normalized snapshot
  → versioned policy
  → assessment and findings
  → portfolio action
```

```text
sifter scan --account <github-login>
sifter assess --policy policy.yml
sifter report --format markdown
sifter diff --before <snapshot> --after <snapshot>
```

## Assessment outputs

Sifter will produce:

- An evidence score with a traceable per-dimension breakdown
- A maturity class: Flagship, Supported, Incubating, Reference, Needs Triage, or Archive/Consolidate
- A separate portfolio-fit assessment
- Hard-gate findings for conditions such as missing licenses, no usable README, no quality evidence, stale support claims, exposed secrets, or unacknowledged supersession
- Recommended actions: promote, support and improve, incubate with scope, triage, consolidate, or archive with redirect
- Immutable snapshots and drift reports

## Status

**Proposed.** Initial work is design-first. The first implementation will be a read-only Rust CLI with GitHub collectors, a versioned policy engine, immutable snapshots, and JSON/Markdown reports.

## Scope boundaries

Sifter v1 will not:

- Create issues or pull requests
- Modify repository metadata, labels, or archive state
- Execute arbitrary commands declared by scanned repositories
- Analyze private repositories
- Treat stars, forks, or recency as primary quality indicators

## License

License selection is intentionally pending before implementation begins.
