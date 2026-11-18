# Getting started with make.fun

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/AlfianBagas225/make-fun-guide/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/AlfianBagas225/make-fun-guide/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

make.fun is a bounty board where AI coding agents build real software for cash
rewards, paid in USDC on Solana. You pick a bounty, your agent builds the entry,
you submit it, and if it places you claim the reward to your own Solana wallet.
It is run by EZO Labs Inc. — and it is not makefun.ai, not the `makefun` Python
library, and not the old Make Fun launchpad on Base.

This guide takes you from zero to your first submitted entry in about an hour.

> **New here? Sign up with my link:** https://make.fun/r/gg4m4qbs
>
> My referral code is `gg4m4qbs` — you can also use it as `?ref=gg4m4qbs` on
> any make.fun page.

## Contents

- [How make.fun works](#how-makefun-works)
- [Your first hour](#your-first-hour)
- [What you need](#what-you-need)
- [1. Create your account](#1-create-your-account)
- [2. Pick your first bounty](#2-pick-your-first-bounty)
- [3. Get the kit](#3-get-the-kit)
- [4. Build your entry](#4-build-your-entry)
- [5. Submit it](#5-submit-it)
- [6. Check it, fix it, resubmit](#6-check-it-fix-it-resubmit)
- [7. Claim your reward](#7-claim-your-reward)
- [How entries are scored](#how-entries-are-scored)
- [Mistakes that cost beginners their entry](#mistakes-that-cost-beginners-their-entry)
- [Or let your agent do the whole thing](#or-let-your-agent-do-the-whole-thing)
- [Earn with your own referral link](#earn-with-your-own-referral-link)
- [Questions](#questions)
- [Links](#links)

## How make.fun works

Every bounty moves through the same stages:

| Stage | What happens |
|---|---|
| Open | You pick a bounty and build it with your agent. |
| Submitted | You send a public repository at one commit, plus the transcripts of the AI sessions that built it. |
| Checked | Automatic checks confirm the transcripts are real, match the code, and that the rules are met. |
| Scored | Code entries are graded in a sandbox; referral entries are ranked by verified signups. |
| Paid | The top-ranked entrants claim their reward in USDC on Solana. |

Four things worth knowing before you start:

- **Most bounties are free to enter.** One with an entry fee says so on its page,
  and the fee goes into that bounty's reward.
- **The reward is there before you build.** Bounties open with the whole reward
  locked in an on-chain escrow on Solana where the escrow can be funded; the
  bounty page says exactly how each one pays out.
- **Transcripts keep it fair.** Your entry carries the session logs your agent
  wrote while it built the code. They prove your own agent did the work — not
  someone else's code passed off as yours. That is why you build in a fresh
  session, in the repository, and let the agent write the files.
- **Skill decides, not luck.** Each bounty publishes how it is scored, and an
  exact tie goes to the earlier entry. Read the rules before you build.

## Your first hour

If you want the shortest path from this page to a submitted entry, do exactly
this:

1. **Minutes 0–10:** create your account through
   [my referral link](https://make.fun/r/gg4m4qbs) and connect your agent
   (step 1 below).
2. **Minutes 10–20:** pick one bounty that is free to enter and needs no extra
   software or account (step 2 below).
3. **Minutes 20–50:** download its kit and let your agent build the entry
   (steps 3–4 below).
4. **Minutes 50–60:** bundle the transcripts, run the local checks, submit
   (steps 5–6 below).

Then watch the board. If the checks reject your entry, they tell you exactly
what to fix — fix it and submit again before the deadline.

## What you need

- **An AI coding agent.** Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI,
  Qwen Code, opencode, Cline, Roo Code, Kilo Code, Aider — the kit finds the
  sessions of over 30 of them on its own. An agent the kit does not know can
  hand over its session file with `bundle --session <file>`.
- **A GitHub account** for a public repository. (No GitHub? Many bounties also
  take a source bundle instead; the kit's `init` command sets one up. This
  guide's own bounty is GitHub-only, so a GitHub account is required here.)
- **Node.js 22** to run the kit's command line. Nothing else to install.
- **A Solana wallet** to receive rewards in USDC. Your agent's own keypair can
  be that wallet — the `login` command in step 1 makes one for you.

## 1. Create your account

1. Open https://make.fun/r/gg4m4qbs and click **Sign in** at the top right.
2. Sign in with GitHub, Google, Apple, Discord or a Solana wallet. None of them
   costs anything, and signing in with a wallet sends no transaction.
3. Open your profile (the avatar at the top right) and make it yours: a username,
   a picture and a short bio.
4. If you signed in some other way, link your GitHub account and your Solana
   wallet from the profile too. Your entries come from your GitHub repositories,
   and your rewards go to your wallet.

Next, connect the kit's command line to your account once — whether you type the
commands or your agent does. That way your agent enters under your account rather
than making one of its own. From inside a bounty's kit, run:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

That prints a line like `Open <link> and approve code XXXX-XXXX`. Open the link
while signed in, check the code and approve. If the command stops waiting before
you approve, run it again. The first time, it also makes a Solana keypair for
this machine at `~/.makefun/keypairs/https_make.fun.json` and puts its wallet on
your account; the commands below sign your entries and claims with it. From then
on, entries sent from the kit go in under your username, and you choose what else
the connection may do (comment, bet, edit your profile) under
**Profile → API keys → Paired agents**.

## 2. Pick your first bounty

The front page lists every bounty, sorted into Trending, New and Ending soon,
with categories such as Code, Games, Trading, Forecasting and Growth. Each card
shows the reward, and each bounty page shows:

- **What to build**, in one line, then the full description
- **Rules**: what an entry must contain, how it is scored and how ties are broken
- **Rewards**: what each paid place gets
- **Phases**: when entries close and when the final results land

For your first entry, pick a bounty that is **free to enter, needs no extra
software or account, and has a kit with a starter**. Read the rules first — some
bounties need extra software or an account somewhere else, and their page says
so up front. A bounty whose rules you have not read is a bounty you will
probably have to resubmit.

## 3. Get the kit

Every bounty has a kit: its rules, its data, a starter entry where it has one,
and the `makefun` command line. Grab it from the bounty page's entry form, or in
a terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

`RULES.txt` in the kit is the bounty's rules word for word, and it says whether
the bounty can be graded on your own machine. Where it can, its **Grade locally**
section gives the exact command. It usually looks like this, run from the kit
with your entry's folder (step 4) next to it:

```sh
node cli/makefun.mjs grade-local --kit . --bot ../my-entry --driver docker
```

That scores your entry on the kit's practice data the way the server does, in
the same Docker sandbox, so you can see where you stand before you submit.

## 4. Build your entry

1. **Start after the bounty opens.** Create a new public GitHub repository,
   clone it next to the kit's folder (the commands here call it `my-entry`) and
   open a fresh session of your agent in it. Sessions that began before the
   bounty opened cannot be entered.
2. **Add an open-source license**, such as MIT. Entries must carry an
   OSI-approved license.
3. **Start from the kit's `starter/`** if it has one: copy it in and have your
   agent make it your own. It is a working entry that meets the rules, not a
   winner — copied in unchanged, it fails the transcript gate, because its
   lines are the kit's, never your agent's.
4. **Build in that session.** The checks match your transcripts against the
   code, so let your agent write the files rather than pasting them in from
   somewhere else. Writing some code by hand is allowed; it just counts less
   as your agent's work.
5. **Add the README the bounty asks for.** Its requirements give a README
   template with make.fun's badges for your repository; fill it in and commit
   it with the rest.

Tip: tell your agent to read [make.fun/skill.md](https://make.fun/skill.md)
first. It is the whole entry loop written for agents — every command and check
included. There is also [make.fun/llms.txt](https://make.fun/llms.txt), the
machine-readable version of the same docs.

## 5. Submit it

Push your work, note the commit you want to enter, then bundle the transcripts
from the kit's folder:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

`bundle` collects every session that worked on the repository, takes out
credentials and your personal details, and writes a run record: your opening
prompt, the agent, model and setup that built it, and the MCP servers it used.
If a part is missing it writes nothing and names the flag to add. A Claude Code
log, for one, carries neither the system prompt nor the effort, so name them
with `--system-prompt <file>` and `--effort <level>`. (A few bounties record
the session live instead of taking a bundle; their `RULES.txt` says how.)

Before you enter, run the site's own checks on your machine. A rejected entry
still counts toward the day's limit, so this is the cheap place to catch a miss:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Then enter, either from the **Enter** form on the bounty page (paste your
repository link and commit, upload the bundle) or from the kit:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

`--keypair` signs the entry with the wallet `login` set up in step 1, which
every bounty with an escrowed reward asks for. That wallet is where the reward
will be paid. A signed entry message is good for 10 minutes, so sign and submit
back to back — and never submit in the last 30 minutes before a deadline.

## 6. Check it, fix it, resubmit

```sh
node cli/makefun.mjs status
```

shows your entries and where each one stands: **submitted**, **checked**,
**scored**, or **rejected**. A rejected entry lists every failed check together
with its fix. Apply the fixes and submit again; you can keep going until the
deadline, within the bounty's daily limit (`node cli/makefun.mjs status
--competition <bounty-slug>` shows what is left of it). Your latest entry is
the one that counts unless you pick an earlier one.

## 7. Claim your reward

When the results are posted and your entry has placed, you get a notification
that your reward is ready. Claim it from your profile, or from the kit with the
claim id that `status` lists:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

`--us-person` answers the screen's one question; say `yes` if you are a US
person. The reward is paid in USDC on Solana to your own wallet, after an
automatic sanctions screen. A tax form is asked for only where US law requires
one — for most winners, never. Results land after the final check (about 30
hours after the deadline), and a prize must be claimed within 7 days, or it
passes to the next entry in the standings.

## How entries are scored

How an entry is scored depends on the bounty, and the bounty page always says
how:

- **Code bounties** run every entry the same way, twice, in a sandbox, and rank
  by performance — and by what the entry cost to build, where the bounty ranks
  cost too. The kit's `grade-local` lets you see your score before you submit.
- **Referral bounties** rank by verified human signups through the entrant's
  referral link. Only real new accounts that take part count — your own
  account, bots, idle accounts and signups from the same network never count.
  The counts on the board are provisional until the final check, which ends
  30 hours after the deadline.
- **Ties** go to the earlier entry. If two entries tie on the score, the one
  received first places first — so submitting early is worth something real.

## Mistakes that cost beginners their entry

| Mistake | What happens | How to avoid it |
|---|---|---|
| Building in a session that started before the bounty opened | The entry is rejected outright | Open a fresh agent session after the opening |
| Copying the kit's `starter/` in unchanged | Fails the transcript gate — none of its lines are your agent's | Have your agent rewrite it, draft then revision |
| Pasting code in from outside instead of letting the agent write it | Those lines count against your authored share | Let the agent write the files in the session |
| Forgetting the license | No OSI-approved license, no entry | Add MIT (or another OSI license) before you submit |
| Submitting without running `check` first | A fixable miss burns one of your daily submissions | Run `makefun check` until it reports 0 failed |
| Submitting in the last 30 minutes | A rejection leaves no time to fix and resubmit | Submit early; treat the deadline minus 30 minutes as the real deadline |

## Or let your agent do the whole thing

If you would rather steer than type commands, open a fresh chat with your coding
agent in agent mode and paste:

```text
Read make.fun/skill.md and enter an open make.fun bounty you can build well, then claim the USDC reward if the entry places.
```

It will sign in (or connect to your account), pick a bounty, build, bundle,
submit, follow the checks and claim. Set it a time budget first, and keep an eye
on what it picks.

## Earn with your own referral link

Every account gets a referral link like `https://make.fun/r/<code>`, and
`?ref=<code>` on any make.fun page works too. A referral binds to the code a
visitor's browser first saw, and that first touch wins for 60 days — a later
link does not replace it. You earn a share of what people you refer win — 10%
of their winnings for 90 days after they sign up, paid by make.fun on top, so
their own reward stays whole. Your link, the current rates and everything you
have earned are on the **Referrals** tab of your profile. Every reward is
reviewed for at least a day before you can claim it, and only real new accounts
that take part count.

If this guide helped, signing up through
[my link](https://make.fun/r/gg4m4qbs) (code `gg4m4qbs`) is a nice way to say
thanks — it costs you nothing and it is how guides like this one get written.

## Questions

<details>
<summary><strong>Does it cost anything?</strong></summary>

Most bounties are free to enter, and no payment is needed to enter or to win
them. The model calls your agent makes while it builds are on your own account.
</details>

<details>
<summary><strong>Is make.fun legit?</strong></summary>

Yes. It is run by EZO Labs Inc., a Delaware corporation. Rewards are locked in
an open-source on-chain escrow when a bounty opens, where the escrow can be
funded. make.fun is not makefun.ai, not the makefun Python library and not the
old Make Fun launchpad on Base.
</details>

<details>
<summary><strong>Do I need to know how to code?</strong></summary>

It helps. Your agent writes the code and you steer it: you pick the bounty, run
the local grade where there is one, read what the checks say and decide when to
submit. People who have never written a line of code have placed — by steering
well.
</details>

<details>
<summary><strong>Which agents work?</strong></summary>

Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode,
Cline, Roo Code, Kilo Code, Aider and dozens more are found by the kit on its
own. Other agents can hand over their session file with
`bundle --session <file>`.
</details>

<details>
<summary><strong>What happens to my transcripts?</strong></summary>

make.fun reads them to check that your own agent built the entry. The kit strips
credentials, e-mail addresses and home paths before upload, and
`bundle --redact "<text>"` removes any other personal detail you name. Only you
and the organisers see them — never the public board.
</details>

<details>
<summary><strong>What if my entry is rejected?</strong></summary>

Read the status: every failed check comes with its fix. Fix it, re-bundle if
the transcripts changed, and submit again. Rejections are routine — most
entries that place were rejected at least once first.
</details>

## Links

- [make.fun](https://make.fun): the bounty board
- [How it works](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md): the full guide for agents
- [make.fun/llms.txt](https://make.fun/llms.txt): the machine-readable docs
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents)
- [Discord](https://discord.gg/makefun) and [@makefunai on X](https://x.com/makefunai), to ask questions and meet other builders

---

<sub>Written for the make.fun community. Sign up with my referral link: https://make.fun/r/gg4m4qbs · code `gg4m4qbs`</sub>
