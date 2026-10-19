# 🤖 Job Search AI Toolkit — France

A portable set of AI skills for job seekers in France: zero-to-one Notion tracking setup, job discovery and recurring audits, CV tailoring, and evidence-based cover letters.

The same `SKILL.md` sources work with **Claude** and **Codex**. The instructions are written in French and can be adapted to other markets.

## What you get

| Skill | Purpose |
|---|---|
| [`job-search`](skills/job-search/) | Build or connect a complete Notion job-search system, collect and audit offers, run recurring checks, and synchronize tracking under a configurable authorization mode |
| [`cv-tailoring`](skills/cv-tailoring/) | Analyse a job description and tailor a real CV without inventing experience |
| [`cover-letter`](skills/cover-letter/) | Draft a specific 250–320 word cover letter from verified CV or portfolio facts |

## Quick start

Start with the [complete setup guide](guide/job-search-ai-setup.md), then choose your environment.

### Claude

1. Download this repository.
2. For each skill you want, create a ZIP whose top-level folder is the skill folder itself. For example, the ZIP for `job-search` must contain `job-search/SKILL.md`.
3. In Claude, open **Customize → Skills**, choose **Create skill → Upload a skill**, and upload the ZIP.
4. Enable the uploaded skill and test it with one of the prompts in the guide.
5. Upload your CV and profile material to a Claude Project if you want persistent candidate context.

Claude custom skills require code execution and file creation to be enabled. Project files and custom skills serve different purposes: the Project stores the candidate's facts; the skills define the reusable workflow.

### Codex

The repository is packaged as a skills-only plugin. After this version is pushed to GitHub:

1. Run `codex plugin marketplace add reighly-cant-frontflip/Job-search-ai-toolkit-fr`.
2. Open the Plugins directory in Codex.
3. Select the **Job Search AI Toolkit — France** marketplace and install `job-search-ai-toolkit-fr`.

During local development, add the repository folder itself as a local marketplace, or copy individual folders from `skills/` into the Codex skills directory.

After installation, start a new task so Codex refreshes the available skill list.

## Repository structure

```text
Job-search-ai-toolkit-fr/
├── plugin.json                         # Portable plugin manifest
├── .codex-plugin/
│   └── plugin.json                    # Codex compatibility manifest
├── .agents/plugins/
│   └── marketplace.json               # Codex repository marketplace
├── guide/
│   └── job-search-ai-setup.md         # Complete setup and usage guide
├── skills/
│   ├── job-search/
│   │   ├── SKILL.md
│   │   └── references/
│   │       ├── notion-schema.md
│   │       ├── notion-site-setup.md
│   │       └── recurring-audit.md
│   ├── cv-tailoring/
│   │   └── SKILL.md
│   └── cover-letter/
│       └── SKILL.md
├── README.md
├── CHANGELOG.md
└── LICENSE
```

The dated Markdown files in the repository root are retained temporarily for users of earlier releases. New installations should use the canonical files under `skills/`.

### Zero-to-one Notion setup

Ask the `job-search` skill to build a complete job-search system in Notion. It can create or connect a `Job Search Dashboard`, use one `Jobs` database as the source of truth, add action-oriented views, and prepare pages for search sessions, market observations, source management and operating rules.

The skill verifies the resulting properties and views instead of assuming that a successful request created every component. When a connection cannot create a view or template, it reports the partial deployment and gives exact manual steps. Installing the toolkit does not create or modify a Notion workspace by itself.

### Job-search authorization modes

When a user explicitly starts or configures the job-search workflow, `continuous authorization` is the default for synchronizing unambiguous, qualified offers with the approved tracker and source. On first launch, the skill tells the user that they can switch at any time to `per-session validation`.

Installing the toolkit alone never authorizes an external write or creates a scheduled task. Neither mode permits submitting applications, sending messages, changing a profile, or bypassing authentication.

## Design principle

Candidate-specific information—CV facts, target roles, locations, tracker IDs and private search URLs—must stay outside the public skills. The skills contain only reusable decision rules. This prevents personal data from leaking into the repository and lets one installation support different candidates.

## License

CC BY-SA 4.0 — free to use, including commercially, as long as you credit the source and share modified versions under the same license.

Job Search AI Toolkit © 2026 by Xiangrui Chen is licensed under CC BY-SA 4.0.

## Contributing

Feedback, corrections and adaptations to other French-speaking markets are welcome through issues or pull requests.

---

*Built by Ray (Xiangrui Chen) — Hospitality Finance & Cost Control*
