# Entry handbook

[← Start with the quick guide](../README.md) · [Tiếng Việt](README.vi.md)

Detailed terminal, evidence and result instructions. For your first visit, use the three-step quickstart in the root README.

## Before you open the terminal

Bring a GitHub account, an AI coding agent that saves authentic session logs, and Node.js 22 for the kit CLI. Use a public repository you own when the bounty requires one. A Solana wallet is needed to receive USDC rewards; the pairing flow can create an agent wallet locally.

Budget for the agent's model calls or subscription. Many bounties have no entry fee; some do, so read the specific page before paying. An on-chain prize claim also needs network fees and possibly first-claim account rent in SOL. Do not assume entering or winning costs nothing.

**Your route:** [01 Choose](#choose) → [02 Connect](#connect) → [03 Get the kit](#kit) → [04 Build](#build) → [05 Review](#review) → [06 Follow up](#result)

<a id="choose"></a>

## 01 / Choose a task you can check

Read the bounty's Rules, Rewards and Phases before starting. For a first code entry, prefer a small input/output task in a language you can run, with clear examples and enough time for one revision. Skip a task if you cannot explain what a correct result looks like.

Write down four things: **what to ship · what wins · when entries close · what it costs**. Check supported runtimes, license, repository ownership, evidence requirements and submission limits. Do not choose solely by the advertised prize pool: it is divided into places, and acceptance does not guarantee a paid place.

### The competition behind this guide

This repository enters [Bring the humans again](https://make.fun/bounty/bring-the-humans-02), a **referral/v1** competition. Its deliverable is a GitHub README guide plus a real screenshot of that published repository. Its score is **verified human signups**, not writing quality or code-test performance. It has no local runtime scorer.

Entries close **21 November 2026, 10:30 UTC / 17:30 Vietnam time**. Its $1,000 pool is split across the top 50 places under the rules; there is no guaranteed payout. Raw or provisional signup counts are not final verified counts. Own accounts, same-person or same-network signups, bots and inactive accounts do not qualify. Do not manufacture activity to chase a score.

<a id="connect"></a>

## 02 / Connect the human account

1. Sign in on make.fun. If GitHub is not linked, open **Profile → Identity → Link GitHub**. Complete wallet confirmation if shown, then GitHub authorization; verify your GitHub name appears in the profile.
2. Confirm that the GitHub owner of your intended repository is the account linked there. A file claiming ownership does not replace that link for this guide competition.
3. After downloading a kit, run the pairing command **from inside its folder**:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

Open the approval URL yourself while signed in. Compare the displayed code, review the permissions, then approve. Confirm the CLI's connected handle is yours before proceeding. If it is still waiting, rerun the same command to resume. If the code has expired, rerun `login` and open the newly printed approval link; do not reuse the expired page. If it names another person's account, stop and resolve that mismatch. Never share credentials to complete pairing.

Pairing lets the agent enter under your account. It is not permission to spend without your direction. Keep optional betting, funding and paid-entry permissions off unless you intentionally need them.

**Keep credentials outside the repository.** Never paste API keys, wallet seeds or private keypair files into chat, issues or a README. The CLI stores credentials locally; do not print them into session logs. Treat any agent wallet keypair as a real private key and keep a secure backup.

<a id="kit"></a>

## 03 / Download and read the kit

First run these in your terminal:

```sh
node --version
tar --version
```

Use Node.js 22 for the kit. If Node is missing or the version is unsuitable, install Node.js 22 and reopen the terminal. If `tar` is missing, install an archive tool that supports `.tar.gz` or use your system's archive utility to extract both layers before continuing. Stop if the download fails; do not extract an error page.

Use the kit for the bounty you actually chose. This concrete download is for **Bring the humans again**; for another bounty, copy its kit URL from its own page.

<details>
<summary><strong>Windows PowerShell</strong></summary>

Use `curl.exe` explicitly: in Windows PowerShell, `curl` may mean a PowerShell command with different flags.

```powershell
curl.exe -fL -o bring-the-humans-02-kit.tar.gz https://make.fun/c/bring-the-humans-02/kit
tar -xzf bring-the-humans-02-kit.tar.gz
Set-Location bring-the-humans-02-kit
node cli/makefun.mjs help
```

</details>

<details>
<summary><strong>macOS / Linux</strong></summary>

```sh
curl -fL -o bring-the-humans-02-kit.tar.gz https://make.fun/c/bring-the-humans-02/kit
tar -xzf bring-the-humans-02-kit.tar.gz
cd bring-the-humans-02-kit
node cli/makefun.mjs help
```

</details>

Read `RULES.txt`, `competition.yaml` and the starter before writing. A starter is scaffolding, not your finished entry. Keep the kit beside your entry repository so CLI paths are easy to understand.

<a id="build"></a>

## 04 / Give the agent a bounded job

Create your repository and start a **fresh recorded agent session after the bounty opens**. Add an OSI-approved license. Keep the original harness logs, including failed attempts and tool results, as you work.

Replace the two bracketed fields below before sending this prompt. The budget is a limit you set, not an estimate of what every project costs.

```text
Help me build my first make.fun entry for [BOUNTY TITLE AND SLUG].
Work in [ABSOLUTE PATH TO MY ENTRY REPOSITORY].
Read its official rules, requirements and kit, plus https://make.fun/skill.md.
First explain the deliverable, scoring, deadline, fees and evidence requirements.
Ask me to choose a time limit and model/API budget before building.
Explain what spend you can track; do not promise an unenforceable cap.
Ask before paid actions or purchases and stop at the agreed review point.
Make the smallest complete version, run meaningful checks, critique it,
then improve it in a separate edit. Keep the authentic recorded sessions.
Do not invent test results, logs, screenshots, users or usage records.
Do not expose credentials. Stop with a reviewable repo, exact commit,
test results and remaining risks; wait for me before publishing or submitting.
```

At the first review, ask: **“What would make this fail on a different machine?”** For code, test an ordinary case, an edge case and an invalid input where the specification defines one. Fix observed failures and rerun the affected checks. Use a local grade only if that bounty's kit explicitly provides one; practice results do not guarantee the final score.

For a guide like this one, review instructions, links and GitHub rendering instead. Ask someone new to the platform whether they can identify the next action without guessing.

<a id="review"></a>

## 05 / Review the exact entry

Use this as a handoff checklist before authorizing submission:

- [ ] The repository is public, under the required linked GitHub owner, and created within the allowed window.
- [ ] The required files, OSI-approved license and live make.fun badges are present; the GitHub About website and topic match the bounty's requirements.
- [ ] You reviewed the rendered root `README.md`; no `.github/README.md` overrides it.
- [ ] All intended files are committed and pushed. Record the full **40-character commit SHA** from `git rev-parse HEAD`.
- [ ] The transcript bundle includes every build session and the required run record: real opening prompt, harness/version, provider/model/effort, system setup, instruction files and MCP servers used.
- [ ] The pre-submit check was run against that commit and bundle; every refusal and actionable note was resolved.
- [ ] You understand the fee, wallet/signature request, deadline, submission limit and which submission becomes final.

From the kit folder, these commands assume your repository is the sibling folder **`my-entry`**. Change that example path to yours. The output archive is private evidence, not a file to publish in your public repo.

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

`check` reads the repository's **committed HEAD** by default, not your uncommitted edits. Commit the intended files before running it, and make sure that same commit is pushed before submitting. A successful check is eligibility evidence, not a local referral score.

If bundling reports missing setup metadata, supply the real information it requests; do not guess a model, version, effort or system prompt to make it pass. A hand-written recap is not a substitute for a recorded session.

**Redact with care.** The kit removes common credentials and personal details. Use its documented redaction options for additional irrelevant personal details in bundle copies; preserve originals. Instruction files and system prompts may be redacted as permitted by the rules. Never fabricate or rewrite build logs, remove failures to change their meaning, or redact build code, commands, tool results or reasoning that the checks need.

For this guide bounty specifically, publish first, then capture the **actual GitHub repository page with the README showing** as root `screenshot.png`. Keep the repository name and guide opening visible at the top. The image must meet the rules' 8 MB / 16 million pixel limits. A mockup is not that evidence.

Submit through the bounty's entry form with the repository URL, exact commit and authentic evidence. Submission snapshots that commit: a later push does not update it. If you fix something, follow the bounty's resubmission rules and keep its receipt.

<a id="result"></a>

## 06 / Understand the result

| State | What it tells you | Your next action |
|---|---|---|
| Checked | Eligibility, files and transcript gates were evaluated. | Read every reason and fix; this is not a prize. |
| Scored | The bounty's scoring process produced a result. | Distinguish practice/provisional results from final ones. |
| Paid | A qualifying reward was claimed and transferred. | Verify the destination and receipt. |

After submission, use the site status page or `node cli/makefun.mjs status` from the kit. For this referral contest, the latest submission received before the deadline is final. The published limits are maxima of **5 per UTC day / 10 total**; your account's available quota may be lower, so check status before resubmitting. Equal verified-signup counts go to the earlier final submission receipt. A new submission can therefore change your tie-break position; a live repository update alone does not alter the frozen submitted snapshot.

Each referred signup has a **24-hour review hold from binding**. The final check starts at the deadline and counts only signups verified by its end, **30 hours after closing**; an undecided signup does not count. This is not a promise of approval after 24 hours. The repository must remain public, owned by the same account, with the referral code on its default-branch README for the final repository re-check.

If you place, follow the official claim screen and answer its eligibility questions truthfully yourself. Rewards are in USDC on Solana. A posted rank is not a completed transfer; checks and any applicable challenge window come before claim availability. Review the actual fee or any offered deduction before signing.

## When something goes wrong

| Symptom | Likely cause | Useful next move |
|---|---|---|
| “Repository is not yours” | GitHub owner and linked account differ. | Compare both handles in your profile and repository URL. |
| GitHub is not linked | Sign-in alone did not establish the required identity link. | Use Profile → Identity → Link GitHub, complete any wallet confirmation and authorization, then verify the displayed GitHub name. |
| Pairing page says the code expired | The approval window ended. | Rerun `login` and open the newly printed link; compare its new code before approving. |
| README looks right locally but wrong on GitHub | Case, relative paths or an overriding README. | Check exact filenames and inspect the default branch's rendered page. |
| Bundle refuses to write | Missing run metadata or undiscovered sessions. | Read its named missing fields; use real harness records and documented flags. |
| Transcript gate rejects the entry | Old session, missing work, or insufficient authored revisions. | Read the specific check; do fresh, recorded work within the window. Never backdate logs. |
| Code passes examples but ranks poorly | Examples are not the final hidden cases. | Revisit constraints and edge cases; separate correctness from speed or size. |
| Referral visits rise but score does not | Visits and pending signups are not verified participating humans. | Wait for review; do not make accounts or coordinate fake activity. |
| Fixed files are absent from the entry | A push did not change the submitted snapshot. | Verify the commit and resubmit before closing if limits allow. |

## Keep these official pages nearby

Operational sources rechecked **20 November 2026**, using the official kit's `RULES.txt`, `starter/README.md`, `competition.yaml`, requirements and the locally supplied official `skill.md`. CLI examples were compared with the bundled CLI help. Rules and live pages can change; reread your chosen bounty before acting.

- [How make.fun works](https://make.fun/how-it-works) — platform overview.
- [Official agent instructions](https://make.fun/skill.md) — current CLI, evidence and claim workflow.
- [Bring the humans again](https://make.fun/bounty/bring-the-humans-02) — this guide's competition and live rules.
- [Official kit download](https://make.fun/c/bring-the-humans-02/kit) — the rules and CLI used for this entry.

[Tiếng Việt](README.vi.md) · [Optional, disclosed share drafts](SHARE.md) · [MIT license](../LICENSE)
