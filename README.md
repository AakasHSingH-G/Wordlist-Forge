<div align="center">
⚡ Wordlist Forge
A browser-based VAPT toolkit — wordlist generation, code review, and CLI-style docs, in one file.

Made with JS Runs 100% Client-Side Single File License: MIT

Stars Forks Last Commit
<img src="https://img.shields.io/badge/status-active-brightgreen?style=flat-square" alt="status"/> <img src="https://img.shields.io/badge/for-authorized%20testing%20only-critical?style=flat-square" alt="scope"/> </div>
🖥️ Preview

    Kali-terminal aesthetic. No install, no backend, no build step — just open the HTML file.

$ ./forge --init  [ OK ]

 __      __            _ _ _     _     ___
 \ \    / /___ _ _ __| | (_)__| |_  | __|__ _ _ __ _ ___
  \ \/\/ / _ \ '_/ _` | | (_-<  _| | _/ _ \ '_/ _` / -_)
   \_/\_/\___/_| \__,_|_|_/__/\__| |_|\___/_| \__, \___|
                                               |___/
v2.0 — bug-bounty / VAPT wordlist engine

<!-- Drop a real screenshot/GIF here once you've got one — this is the section people judge your repo by --> <!-- ![screenshot](docs/screenshot.png) -->
✨ What's inside
Module	What it does
🔀 Random	Charset + length-based brute-force wordlist generation
🎯 Pattern	Hashcat-style mask attacks (?l?u?d?s?a)
🧬 Mutate	Turns seed words into realistic variants (l33t, case, +years, +symbols)
🔗 Combine	Chains 2–3 seed words the way real passwords get built
📋 Presets	Curated OSINT-style seed lists (common passwords, usernames, network defaults…)
🕵️ Code Review	VAPT-minded static scanner — secrets, injection sinks, XSS/CSRF/tabnabbing, attack-surface mapping, taint correlation
💻 Sandbox	Built-in CLI (<mode> -h, man, use, charsets…) — no external docs needed
🕵️ Code Review highlights

    Detects branded secrets: AWS keys, GitHub tokens, Slack tokens/webhooks, Stripe live keys, Google/Firebase keys, Mailgun keys
    Flags injection sinks: eval(), SQL string concat, unsafe YAML/pickle deserialization, command execution
    Catches XSS/CSRF/tabnabbing patterns: innerHTML, dangerouslySetInnerHTML, missing rel="noopener", CSRF-less forms, postMessage without origin checks
    Taint correlation: auto-escalates a sink to Critical when user-controlled input (req.query, e.data, etc.) is found flowing directly into it
    Attack-surface mapping: lists every form, API call, and third-party domain referenced — a ready-made recon checklist
    Plain-English mode: toggle "Explain in simple English" to get every finding translated out of security jargon

🚀 Quick Start

No dependencies. No build. No server.
bash

git clone https://github.com/AakasHSingH-G/wordlist-forge.git
cd wordlist-forge

Then just open it:
bash

# Linux
xdg-open wordlist-forge.html

# macOS
open wordlist-forge.html

# or just double-click it

That's it — it runs entirely in your browser. Nothing is uploaded, nothing calls home.
🧭 Usage

Every mode has a left-side card. Click one, or use the Sandbox tab for CLI-style help:

$ combine -h

COMBINE — combine [-h]
Chains 2-3 seed words the way real passwords are built ("name+pet+year"),
then optionally mutates the merged result.

FIELDS
  base words               one seed word per line
  chain length              1, 2, or 3 words joined per candidate
  separators tried          none, _ , - , .
  apply on top              case/+nums/+years/+symbols run on the merged word

EXAMPLE
  words john/admin/2024, chain 2 → john_admin, admin-2024, john.2024 ...

Try help, man <mode>, use <mode>, or charsets in the Sandbox.
⚠️ Scope & Ethics

    Run generated wordlists — and the Code Review scanner — only against systems you own or hold explicit written authorization to test: a CTF box, your own lab, or a signed pentest / bug-bounty scope.

    This is a heuristic tool. Every Code Review finding is a lead, not a confirmed vulnerability — verify manually before it goes in a report.
    Brute-forcing or scanning anything outside your authorized scope is illegal. Don't.

🛠️ Tech Stack

    Vanilla JavaScript — no frameworks, no build tooling
    Single .html file — CSS + JS inline, zero dependencies
    100% client-side — works offline once downloaded

🤝 Contributing

PRs welcome — especially new Code Review detection rules. Before submitting:

    Fork the repo
    Add your rule to SCAN_RULES / CUSTOM_CHECKS
    Write a matching SIMPLE_NOTES / SIMPLE_TITLES entry (plain-English mode should cover every rule)
    Test against a real (or synthetic) sample before opening the PR

bash

git checkout -b feature/new-detection-rule
git commit -m "Add detection for <thing>"
git push origin feature/new-detection-rule

📄 License

MIT — do what you want, just don't sell it as-is and pretend you built it from scratch. Credit appreciated.
<div align="center">

Built by a security researcher, for security researchers.

If this saved you time during a VAPT engagement or CTF, drop a ⭐ — it helps.
</div>
Failed to download files
