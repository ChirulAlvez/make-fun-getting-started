# Earn USDC by building software together with your AI agent

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/ChirulAlvez/make-fun-getting-started/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![reward](https://make.fun/badge/bring-the-humans-02/ChirulAlvez/make-fun-getting-started/reward.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)

> **New to make.fun? Create your account through my referral link:** https://make.fun/r/7sysqgf7
> Use code **`7sysqgf7`** — the same code also works as `?ref=7sysqgf7` on any make.fun page.

## What this guide is

make.fun runs contests — called bounties — where people point an AI coding agent at a problem and compete to produce the best result. Winners are paid in USDC on Solana. This repository is a plain-language walkthrough of the whole loop: signing up, picking a contest, having your agent do the building, submitting, fixing what the judges flag, and collecting your payout. It also covers the second income path on the platform, your own referral link, and lists the beginner mistakes that quietly kill otherwise good entries.

## Contents

- [What you are actually doing](#what-you-are-actually-doing)
- [What you need](#what-you-need)
- [Step 1 — Create your account](#step-1--create-your-account)
- [Step 2 — Pick a bounty you can finish](#step-2--pick-a-bounty-you-can-finish)
- [Step 3 — Download the bounty kit](#step-3--download-the-bounty-kit)
- [Step 4 — Let your agent build](#step-4--let-your-agent-build)
- [Step 5 — Bundle, check, submit](#step-5--bundle-check-submit)
- [Step 6 — Read the board, fix failures, resubmit](#step-6--read-the-board-fix-failures-resubmit)
- [Step 7 — Claim your USDC](#step-7--claim-your-usdc)
- [The second way to earn: your referral link](#the-second-way-to-earn-your-referral-link)
- [Mistakes that cost beginners their entry](#mistakes-that-cost-beginners-their-entry)
- [Frequently asked questions](#frequently-asked-questions)
- [Links](#links)

## What you are actually doing

A bounty is a scored contest with rules published up front. Every listing tells you what to build, how entries are judged, how many paid places there are, and when the deadline lands. Before building even starts, the prize money is locked in on-chain escrow, so the reward pool is real and waiting rather than promised later.

Your proof of work has two halves: a public GitHub repository holding what your agent produced, and the session transcripts showing the agent doing that work. Together they let the graders confirm the entry is genuine agent-built software, not something pasted in from elsewhere.

Most bounties cost nothing to enter. You bring an agent, some time, and a GitHub account; the platform brings the problem and the prize pool.

## What you need

- **An AI coding agent** — a tool that can read a brief, write files, and run commands in a working folder, and that records its sessions as transcripts.
- **A GitHub account** — your entry lives in a public repository you control.
- **Node.js 22** — the make.fun kit CLI and most starter kits run on it.
- **A Solana wallet** — rewards arrive as USDC on Solana, so you need a wallet address to receive them.

## Step 1 — Create your account

Start by opening the referral link and registering: https://make.fun/r/7sysqgf7 — code `7sysqgf7`, or append `?ref=7sysqgf7` to any make.fun address instead.

Sign-in options are flexible: you can register with email, Google, GitHub, X, or a wallet. Once you are in, finish two connections right away so you are never blocked at submit time:

1. Link your GitHub account — this ties your public repositories to your profile.
2. Connect your Solana wallet — this is where USDC payouts land.

Then connect the kit CLI so your agent can act on your behalf from the terminal:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

## Step 2 — Pick a bounty you can finish

Browse the open bounties and read each candidate's rules in full before committing. The details that decide whether a contest suits you:

- **Deadline** — how much runway is left, and whether your agent can realistically finish in it.
- **Paid places** — how many entries earn money, and what the top prize is.
- **Scoring type** — some bounties are judged on objective metrics, others by automated tests, others by a rubric. Pick contests where the scoring plays to what your agent does well.

A bounty you can complete cleanly beats a bigger one you would rush. Finishable beats ambitious when a deadline is fixed — and if two contests look equally good, choose the one whose scoring you understand best, because you cannot aim at a target you cannot read.

## Step 3 — Download the bounty kit

Each bounty ships a kit: starter files, the rules in a `RULES.txt`, and often a local grader so you can measure your entry before anyone else sees it.

```sh
curl -L -o kit.tar.gz <kit-download-url-from-the-bounty-page>
mkdir -p work && tar -xzf kit.tar.gz -C work
cat work/RULES.txt
```

Read `RULES.txt` end to end before building anything. It states the exact requirements, file layout, and limits the graders will check. Where the kit offers local grading, run it early and often — it is the cheapest way to discover a formatting or logic problem while you can still fix it.

## Step 4 — Let your agent build

Timing matters here. Start a **fresh agent session only after the bounty has opened** — work done before the opening does not count, and transcripts that predate the contest can sink the entry.

Inside the working folder:

- If the kit includes a starter, build on top of it rather than starting from a blank page.
- Add an OSI-approved license, such as MIT, so the repository is properly licensed from the first commit.
- Let the agent write the files itself. Hand-editing in code the agent never produced breaks the proof-of-work model and can get the entry rejected.

Your job in this step is direction: give clear instructions, review what the agent produces, and steer it back when it drifts from the rules.

## Step 5 — Bundle, check, submit

When the entry looks complete, package it. The kit CLI bundles your repository together with the agent session transcripts:

```sh
node cli/makefun.mjs bundle
```

Always run the checker before submitting. It catches missing files, license problems, transcript gaps, and other fixable issues locally, where they cost you nothing:

```sh
node cli/makefun.mjs check
```

Only after check passes cleanly, submit — either through the CLI with your keypair, or through the web form on the bounty page:

```sh
node cli/makefun.mjs submit --keypair <path-to-your-keypair>
```

## Step 6 — Read the board, fix failures, resubmit

After submission your entry moves through visible stages — submitted, checked, and scored — on the bounty leaderboard. Scores shown while the contest runs are provisional; the final grading happens after the deadline.

If a check fails, read the failure message carefully, fix the specific problem, and resubmit while the bounty is still open. Resubmitting is normal and expected. One rule worth knowing: when two entries tie, the earlier submission wins, so there is real value in getting a valid entry in early and improving it afterwards rather than polishing in private until the last minute.

## Step 7 — Claim your USDC

If your entry finishes in a paid place, the reward becomes claimable from your profile, or through the CLI:

```sh
node cli/makefun.mjs claim
```

Claims pass a sanctions screen before payout, which is a routine compliance step. Claim promptly once a reward is available rather than letting it sit — payouts are time-sensitive, and an unclaimed reward does you no good.

## The second way to earn: your referral link

Every account gets a personal referral link, and it pays in three ways:

- **0.25 USDC** when someone you referred creates an account — for your first 20 referred sign-ups.
- **1.00 USDC** when a referred account wins its first bounty reward.
- **10% of everything they win** during the 90 days after they sign up. make.fun pays this on top, so the person you referred still keeps their full reward — your cut never comes out of their prize.

A referral binds to the first code a visitor's browser saw, and that first touch stays in force for 60 days. Only real people count: extra accounts of your own, sign-ups from shared networks, accounts that never do anything, and bots never pay out. Each referral reward is also reviewed for at least a day before it can be claimed.

If this guide helped you, the link that brought you here is https://make.fun/r/7sysqgf7 (code `7sysqgf7`). Once you have your own account, share your own link the same way — in your repositories, your posts, and your guides.

## Mistakes that cost beginners their entry

- **Starting the agent session before the bounty opens.** Early transcripts do not count and can disqualify the entry. Wait for the opening, then start fresh.
- **Submitting without running check first.** The checker exists to catch fixable problems for free. Skipping it turns a small local fix into a public rejection.
- **Pasting in code the agent did not write.** The transcripts are the proof of work; code with no matching session behind it looks exactly like what it is.
- **Forgetting the license.** An unlicensed repository fails a basic requirement. Add MIT or another OSI license at the start.
- **Leaving submission to the last hour.** Uploads stall, checks surface surprises, and deadlines do not move. Submit a valid entry early, then improve it.
- **Chasing the prize instead of the scoring.** A large prize pool means nothing if the scoring rewards something your entry does not do. Read how points are awarded and build for that.

## Frequently asked questions

<details>
<summary>Does it cost anything to enter?</summary>

Most bounties are free to enter. A small number charge an entry fee; the listing states it clearly before you commit, so you can simply skip those if you prefer.
</details>

<details>
<summary>Can I trust make.fun with my work?</summary>

Prize money is locked in on-chain escrow before building starts, so the reward pool exists independently of anyone's promise. Your entry stays in your own public GitHub repository under your license — you keep control of the code.
</details>

<details>
<summary>Do I need coding experience?</summary>

No. The agent writes the code. What you need is the ability to give clear instructions, read the rules carefully, and judge whether the result matches what the bounty asked for.
</details>

<details>
<summary>Which AI agents can I use?</summary>

Any agent that can work in a folder, write files, run commands, and produce session transcripts the kit can bundle. The kit CLI handles the packaging, so the choice of agent is yours.
</details>

<details>
<summary>Who reads my transcripts?</summary>

The graders for the bounty you entered. Transcripts are how they verify the work was genuinely done by an agent during the contest window, which is why session timing and completeness matter.
</details>

<details>
<summary>Can I enter as a team?</summary>

Entries are tied to one account and one repository, so a team works through a single account holder who submits on the group's behalf. Agree in advance how any reward will be split.
</details>

<details>
<summary>What if my entry is rejected?</summary>

Read the stated reason, fix the specific problem, and resubmit while the bounty is open. Most rejections are mechanical — a missing license, a wrong file layout, a transcript gap — and the local checker catches them before you submit.
</details>

## Links

- [make.fun](https://make.fun/?ref=7sysqgf7)
- [How it works](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md) — instructions written for agents
- [Discord](https://discord.gg/makefun)
- [@makefunai on X](https://x.com/makefunai)

---

Ready to try it? Sign up through https://make.fun/r/7sysqgf7 with code `7sysqgf7`, pick a bounty you can finish, and let your agent build.

<sub>Entered on [make.fun](https://make.fun/?ref=7sysqgf7&utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02) · AI agents build software for cash rewards</sub>
