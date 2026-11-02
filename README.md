<div align="center">

# BibekSec: Offensive Security Master Tree

**A 150-topic, 15-phase roadmap for learning to find, prove and report vulnerabilities, in authorized environments only.**

![Topics](https://img.shields.io/badge/topics-150-ff5c39?style=flat-square)
![Phases](https://img.shields.io/badge/phases-15-2fe0c0?style=flat-square)
![Stages](https://img.shields.io/badge/stages-6-a98bff?style=flat-square)
![Single file](https://img.shields.io/badge/single%20file-HTML-4fb4ff?style=flat-square)
![No build](https://img.shields.io/badge/build%20step-none-b4e34d?style=flat-square)

[Live demo](#live-demo) · [Features](#features) · [Curriculum](#curriculum) · [Run locally](#run-locally) · [Customize](#customize)

</div>

---

## About

The Master Tree is an interactive study guide for offensive security. It takes you from reading a web server's responses to writing professional vulnerability reports, in a single order: **Build, Discover, Validate, Exploit, Report.**

It is one self-contained HTML file. There is no framework, no build step and no server, so you can open it in a browser, host it on GitHub Pages, or keep it offline.

> Add a screenshot here once the project is live:
> `![BibekSec Master Tree](docs/screenshot.png)`

## Live demo

Replace with your own link after publishing:
https://cybertree.netlify.app
<a href="https://cybertree.netlify.app">
## Features

- **Route map.** Six colored lines (stages) with fifteen stations (phases), like a transit map. Each station fills as you learn its topics.
- **Explorer.** A collapsible tree on the left and a detail panel on the right, covering stages, phases, branches and individual topics.
- **Progress tracking.** Mark topics as learned, or mark a whole phase at once. Progress is saved in your browser with `localStorage`, so nothing leaves your device.
- **Operator rank.** Your rank rises with progress: Recruit, Analyst, Operator, Red Teamer, Researcher.
- **Instant search.** Filter every topic and description as you type.
- **Continue button.** Jumps straight to the next topic you have not learned.
- **Per-phase detail.** Objective, tools, diagrams, topics grouped by branch, and exit criteria for each phase.
- **Numbered topics.** Topics are numbered `#001` to `#150`, matching the ranges shown on each phase.
- **Deep links.** Every stage, phase, branch and topic has its own URL hash, for example `#p8` opens Phase 8.
- **Light and dark themes.** Follows your system setting, with a manual toggle.
- **Responsive and accessible.** Works on phones, supports keyboard navigation and respects reduced-motion settings.

### Keyboard shortcuts

| Key | Action |
| --- | --- |
| `/` | Focus the search box |
| `↑` `↓` | Move through the tree |
| `→` `←` | Expand or collapse a node, or go to its parent |
| `Enter` / `Space` | Mark the selected topic as learned |
| `Esc` | Close the image viewer |

## Curriculum

| Stage | Focus | Phases | Topics |
| --- | --- | --- | ---: |
| **1. Web reconnaissance and configuration** | Discover technologies, services and exposed information | 1 | 15 |
| **2. Application trust and input security** | Access control, XSS, injection and authentication | 2 to 6 | 44 |
| **3. Complex web and API behavior** | Server-side requests, file handling, APIs, advanced HTTP | 7 to 10 | 36 |
| **4. Operating system and network security** | Services, Linux, Windows and Active Directory | 11 to 13 | 30 |
| **5. Low-level research** | Reverse engineering, memory behavior, fuzzing, exploit development | 14 | 13 |
| **6. Independent research** | Discover, reproduce, explain, report and verify | 15 | 12 |

<details>
<summary><b>All 15 phases</b></summary>

| # | Phase | Topics |
| --: | --- | --- |
| 01 | Information Disclosure & Misconfiguration | #1 to 15 |
| 02 | IDOR & Broken Access Control | #16 to 25 |
| 03 | Cross-Site Scripting | #26 to 33 |
| 04 | SQL Injection | #34 to 42 |
| 05 | Authentication & Session Security | #43 to 53 |
| 06 | CSRF & Open Redirect | #54 to 59 |
| 07 | File Upload & Path Traversal | #60 to 67 |
| 08 | SSRF & Server-Side Injection | #68 to 74 |
| 09 | API Security | #75 to 84 |
| 10 | Advanced Web Exploitation | #85 to 95 |
| 11 | Network & Service Exploitation | #96 to 105 |
| 12 | Linux & Windows Privilege Escalation | #106 to 116 |
| 13 | Active Directory | #117 to 125 |
| 14 | Exploit Development & Reverse Engineering | #126 to 138 |
| 15 | Professional Vulnerability Research | #139 to 150 |

</details>

**Core environment:** Bash, Burp Suite, Nmap, Wireshark, Git, GDB

**Practice environments:** PortSwigger Academy, TryHackMe, Hack The Box, local labs, authorized bug bounty programs

## Run locally

No installation is needed.

```bash
git clone https://github.com/<your-username>/<repo-name>.git
cd <repo-name>
open index.html        # macOS
xdg-open index.html    # Linux
start index.html       # Windows
```

Or serve it with any static server:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

The fonts load from Google Fonts. Offline, the page falls back to your system fonts and everything else still works.

## Deploy to GitHub Pages

1. Rename the HTML file to `index.html` and commit it to your repository.
2. Go to **Settings, then Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, select `main` and `/ (root)`, then save.
4. After a minute your site is live at `https://<your-username>.github.io/<repo-name>/`.

## Project structure

```
.
├── index.html     # the whole app: styles, roadmap data and logic
└── README.md
```

Inside `index.html`:

| Part | What it holds |
| --- | --- |
| `<style>` | Design tokens (light and dark), layout and components |
| `const D = {...}` | All roadmap content: site info, stages, phases, branches, topics, embedded images |
| Script below `D` | Tree builder, route map, detail views, search, progress and keyboard handling |

## Customize

All content lives in the `D` object inside the script.

```js
D.stages[i].phases[j] = {
  n: 1,                       // phase number
  title: "…",
  range: "#1–15",             // topic number range shown in the UI
  objective: "…",
  test: "…",                  // exit criteria
  tools: ["curl", "Nmap"],
  img: "misconfiguration.png",// key into D.imgs (optional)
  caption: "…",
  branches: [
    { title: "Information exposure",
      topics: [{ name: "…", desc: "…", id: "information-disclosure" }] }
  ]
}
```

- **Change colors:** edit the `--acc` and `--c1` to `--c6` variables at the top of the stylesheet. The `:root[data-theme="dark"]` block holds the dark palette.
- **Add or remove topics:** edit the `branches` array. Counts, progress and numbering update automatically.
- **Reset progress:** run `localStorage.removeItem("bs-learned")` in the browser console.

## Tech

Plain HTML, CSS and JavaScript. No dependencies, no bundler. Fonts: IBM Plex Sans and IBM Plex Mono via Google Fonts.

## Responsible use

This roadmap is for education. Practice only on systems you own or are explicitly authorized to test, such as your own labs, intentionally vulnerable platforms, and bug bounty programs within their stated scope. Unauthorized testing is illegal and harmful. You are responsible for how you use what you learn.

## Contributing

Suggestions are welcome: fixes to topic descriptions, better exit criteria, new diagrams, or accessibility improvements. Open an issue to discuss a change, or submit a pull request with a short description of what you changed and why.

## License

Choose a license for your project, for example [MIT](https://choosealicense.com/licenses/mit/), and add a `LICENSE` file to the repository.

---

<div align="center">

© 2026 BibekSec

</div>
