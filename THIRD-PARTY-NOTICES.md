# Third-party notices

This repository redistributes the skill content listed below. Each item stays under its
own license; the terms are reproduced or pointed to here. The rest of the repository —
the bundle manifest, `cordis.patch.yml`, `locale/`, the README and the packaging — is
original work released under the MIT license in [LICENSE](LICENSE).

## Components

| Path | Origin | License |
| --- | --- | --- |
| `skills/frontend-design` | [anthropics/skills](https://github.com/anthropics/skills/tree/main/skills/frontend-design) | Apache License 2.0 — full text shipped at `skills/frontend-design/LICENSE.txt` |
| `skills/vercel-react-best-practices` | [vercel-labs/agent-skills](https://github.com/vercel-labs/agent-skills) | MIT — `license: MIT`, `metadata.author: vercel` in the skill |
| `skills/web-design-guidelines` | [vercel-labs/agent-skills](https://github.com/vercel-labs/agent-skills) | MIT — stated upstream in the project README |
| `skills/reactuse` | Siberiacancode — `metadata.json`: `organization: Siberiacancode`, version 1.0.16 | MIT — `license: MIT` in the skill frontmatter |
| `skills/react-hooks-best-practices` | Siberiacancode — `metadata.json`: `organization: siberiacancode` | MIT — per the originating project's metadata |
| `skills/frontend-design-direction` | [affaan-m/ECC](https://github.com/affaan-m/ECC) — the skill describes itself as ECC-specific | MIT — ECC is MIT, Copyright (c) 2026 Affaan Mustafa |
| `skills/make-interfaces-feel-better` | vendored in ECC; no upstream origin or license is recorded in the files shipped here | not stated upstream |
| `skills/commit-message-format` | this repository | MIT (this repository's license) |

## MIT License

Applies to the components marked MIT above. Attribution lines are taken from each
component's own metadata; the corresponding copyright lines belong to the respective
upstream projects.

```
MIT License

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

## Apache License 2.0

`skills/frontend-design` carries the complete Apache License 2.0 text in its own
directory as `LICENSE.txt`. That file is reproduced unchanged, and the skill's own
`SKILL.md` refers to it (`license: Complete terms in LICENSE.txt`). The Apache 2.0 terms
require retaining the license and any notices and stating changes; no changes were made
to the files of this skill beyond being copied here verbatim.

## Maintenance notes

- Attribution was assembled from the metadata shipped inside each skill and from public
  licensing audits of the upstream projects. Copyright lines, years and any upstream
  `NOTICE` file should be confirmed against the upstream repositories before relying on
  this file.
- Two components need upstream verification before you redistribute them further:
  `make-interfaces-feel-better`, whose license is not stated in the shipped files, and
  the Vercel skills, whose upstream repository states MIT in its README while carrying no
  separate license file.
- This file is documentation, not legal advice.
