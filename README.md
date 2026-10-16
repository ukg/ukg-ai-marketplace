# UKG AI Marketplace

Public facing marketplace compatible with Claude.ai and Claude Code

## The `UKG Bryte` plugin

UKG Bryte for Claude — Bring your HR and workforce data into Claude via the public UKG MCP server. Skills: UKG Directory (read-only employee directory, employment details, work location, email, and org-chart/reporting views), and Time Off & Accruals (check balances, submit and track time-off requests, review accrual history, and manager time-off/schedule views)

Its capabilities come from the bundled skills:

| Skill | What it does |
|---|---|
| **UKG Directory** | Read-only UKG HR data — employee directory, employment details, work location, email addresses, and org-chart / reporting-hierarchy views. |
| **Time Off & Accruals** | Check balances, submit and track time-off requests, review accrual history, and (for managers) view team time-off and schedules. |

What you can see and do depends on your organization's UKG configuration and your permissions.

The Time Off skill can submit requests, and only does so after you confirm the details. The other skills are read-only.

## Before you start

The UKG Bryte Plugin for Claude is in Beta Early Access. UKG Customer administrators can apply for access [here](https://forms.cloud.microsoft/r/YW9VYAREkN).

You need:

- An active UKG account at an organization that is a UKG customer.
- UKG Customer Admin must approve and enable MCP / AI access.
- Claude Admin cascades access to users through Claude.ai distribution.
- Sign-in method: Users must authenticate through UKG before using.

## What's here

This repo **is** the plugin: its root is the plugin root, so Claude can install it straight from GitHub or through the Claude Marketplace.

| Path | Contents |
|---|---|
| `.claude-plugin/plugin.json` | Plugin manifest (name, version, description) |
| `.claude-plugin/marketplace.json` | Marketplace catalog listing this plugin |
| `.mcp.json` | MCP servers the plugin brings with it |
| `skills/<name>/SKILL.md` | One folder per skill |

Install it:

```bash
claude plugin marketplace add ukg/ukg-ai-marketplace
claude plugin install ukg-bryte@ukg
```

## License

Copyright 2026 UKG Inc.

This repository is licensed under the [Apache License, Version 2.0](LICENSE)
(`SPDX-License-Identifier: Apache-2.0`). See the APPENDIX in [LICENSE](LICENSE) for attribution, which must be retained in redistributions.

| Component | Files | Licensing |
|---|---|---|
| Plugin: UKG Bryte (`ukg-bryte`) | `.claude-plugin/plugin.json`, `.claude-plugin/marketplace.json`, this README | Apache License 2.0 with UKG-specific attributions, through the root ([LICENSE](LICENSE)) |
| Skills: UKG Directory (`ukg-directory-skill`), Time Off and Accruals (`time-off-skill`) | `skills/<name>/SKILL.md` | Apache License 2.0 with UKG-specific attributions, through the root ([LICENSE](LICENSE)) |
| MCP connector configuration: UKG Bryte | `.mcp.json` | Apache License 2.0 with UKG-specific attributions, through the root ([LICENSE](LICENSE)) |

The **public UKG MCP server** (UKG Bryte) that `.mcp.json` points to, including its tools, tool descriptions, schemas, and data, is part of the UKG Services and is **not** licensed by this repository. Access requires authorization and is governed by your organization's agreement with UKG.

"UKG", "UKG Bryte", and other marks listed at https://www.ukg.com/trademarks are trademarks or registered trademarks of UKG Inc. or its affiliates. The Apache License does not grant rights to use these marks.
