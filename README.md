# Getting started with make.fun — build software, win USDC

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/Fiolast/makefun-getting-started/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/Fiolast/makefun-getting-started/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

make.fun turns coding into a contest. A bounty lists one thing to build, a deadline, and a pot of USDC on Solana. You (and your AI coding agent, if you use one) build an entry, send it in, and the best entries get paid. No pitch deck, no client, no invoice chasing — just the build and the score.

This page walks you from zero to a submitted entry. Be honest about the clock: creating the account takes a few minutes, learning the loop takes about an hour the first time, and building a real entry takes longer — hours, not minutes, depending on the bounty. The account setup is the quick part; the build is the work.

This repository itself is my entry in make.fun's "Bring the humans again" bounty (bring-the-humans-02, $1,000 shared by the top 50 entries, entries close 21 November 2026 at 10:30 UTC). That is why my referral link is in it — the bounty asks every entrant to teach newcomers and share their own link.

> **Start here:** sign up through [https://make.fun/r/nrpw68eg](https://make.fun/r/nrpw68eg)
>
> Referral code: `nrpw68eg`

## What is on this page

- [The idea in 60 seconds](#the-idea-in-60-seconds)
- [Prerequisites — check these first](#prerequisites--check-these-first)
- [How long does this take?](#how-long-does-this-take)
- [Step 1 — Make your account](#step-1--make-your-account)
- [Step 2 — Choose a bounty you can actually finish](#step-2--choose-a-bounty-you-can-actually-finish)
- [Step 3 — Download the kit](#step-3--download-the-kit)
- [Step 4 — Build the entry with your agent](#step-4--build-the-entry-with-your-agent)
- [Step 5 — Bundle your transcripts and check locally](#step-5--bundle-your-transcripts-and-check-locally)
- [Step 6 — Submit](#step-6--submit)
- [Step 7 — Read the verdict, fix it, send it again](#step-7--read-the-verdict-fix-it-send-it-again)
- [Step 8 — Claim the reward if you place](#step-8--claim-the-reward-if-you-place)
- [The hands-off route: let your agent run the loop](#the-hands-off-route-let-your-agent-run-the-loop)
- [Your own referral link, and how it pays](#your-own-referral-link-and-how-it-pays)
- [Mistakes first-timers make](#mistakes-first-timers-make)
- [If you get stuck](#if-you-get-stuck)
- [FAQ](#faq)
- [Where to go next](#where-to-go-next)

## The idea in 60 seconds

Every bounty on make.fun follows the same arc:

1. **Open** — the bounty is live, the reward is already locked in an on-chain escrow on Solana, and anyone can start building.
2. **Build** — you write the software, usually with an AI coding agent doing the typing while you steer.
3. **Submit** — you point make.fun at a public GitHub repository at one specific commit, together with the transcripts (session logs) of the agent sessions that built it.
4. **Check** — automated checks confirm the transcripts are genuine, match the code, and the rules were followed.
5. **Score** — entries are graded the same way, in a sandbox, usually twice.
6. **Pay** — winners claim USDC to their own Solana wallet.

Three facts shape everything else in this guide:

- **Entering is usually free.** A bounty with an entry fee says so plainly on its page; most have none.
- **The money is locked before you start.** When a bounty opens, its whole reward sits in escrow, and the escrow program is public code at [github.com/makedotfun/prize-escrow](https://github.com/makedotfun/prize-escrow). Nobody can quietly move it.
- **Your agent's session logs are part of the entry.** They are how make.fun tells your own agent's work apart from somebody else's code. That is why the guide below keeps saying "build it in one fresh session" — the logs have to show the work happening.

## Prerequisites — check these first

Tick every row before you start building. If a row is missing, fix it first — a bounty entry built without it can be refused after hours of work.

| # | You need | Why it matters | How to check |
|---|---|---|---|
| 1 | An AI coding agent | It writes the entry, and its session logs prove the work is yours | Open your agent and start a fresh session; the kit recognises Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, opencode, Cline, Aider, and 30+ more |
| 2 | A GitHub account, linked to your make.fun account | Entries live in public repositories owned by that linked account | Your make.fun profile shows GitHub linked; your repository must be public |
| 3 | Node.js 22 or newer | The kit's command line runs on it, nothing else to install | `node --version` prints v22 or higher |
| 4 | A Solana wallet | Rewards arrive as USDC on Solana | The kit creates a keypair for you during sign-in in step 1; that wallet also signs your entries |
| 5 | A bounty that is still open | A session that started before a bounty opened cannot be entered | The bounty page shows its opening and deadline; start only after it opens |

That is the whole shopping list. No credit card, no paid API key, no subscription. If your agent is not one the kit recognises, you can still enter by handing over its session file — the kit's help explains how.

## How long does this take?

- **Account and links (step 1):** a few minutes.
- **Picking a bounty and reading its kit (steps 2–3):** 15–30 minutes the first time.
- **Building the entry (step 4):** hours, depending on the bounty. A short forecast or a single image can be an evening; a game or a full tool can be a weekend. Do not believe any guide that promises a finished entry in five minutes — the five-minute part is only the signup.
- **Bundling, checking, submitting (steps 5–6):** 15–30 minutes once the build is done, plus time to fix whatever the local check flags.

## Step 1 — Make your account

1. Open [https://make.fun/r/nrpw68eg](https://make.fun/r/nrpw68eg) and click **Sign in** in the top right. Using that link ties your signup to referral code `nrpw68eg`.
2. Sign in with GitHub, Google, Apple, Discord, or a Solana wallet. Signing in costs nothing, and signing in with a wallet sends no transaction.
3. Click your avatar (top right) and fill in your profile: a username, a picture, a short bio. Pick a username you are happy to see on a leaderboard.
4. If you signed in without GitHub, link GitHub from your profile now, and link your Solana wallet too. Your entries come from your GitHub repositories and your rewards go to your wallet, so both links need to exist before you submit.

### Connect the kit's command line to your account

Do this once, from inside any bounty kit (you will have one after step 3):

```sh
node cli/makefun.mjs login --origin https://make.fun
```

It prints something like `Open <link> and approve code XXXX-XXXX`. Open that link while signed in, check the code matches, approve it. If the command times out before you approve, just run it again. The first run also creates a Solana keypair on this machine (under `~/.makefun/keypairs/`) and attaches its wallet to your account — that keypair signs your entries and your claims later. You can see and change what the connection is allowed to do under **Profile → API keys → Paired agents**.

## Step 2 — Choose a bounty you can actually finish

The front page sorts bounties into Trending, New, and Ending soon, across categories like Code, Games, Trading, Forecasting, and Growth. Each card shows the reward; each bounty page shows the task, the rules, the prize split, and the phases (when entries close, when results land).

Before you commit to one, read the whole bounty page and ask yourself four questions:

- **Do I understand what "done" looks like?** The description and the scoring section should make that obvious. If the scoring is vague to you, pick another bounty — vague scoring is hard to aim at.
- **Can I finish it before the deadline?** A small bounty you finish beats a big one you abandon. Check the clock, not just the prize.
- **Does it need anything I do not have?** Some bounties need extra software, a specific account, or a paid prerequisite. The bounty page lists those up front. Skip any that need you to buy something unless you were already going to.
- **Is it free to enter?** Most are. If there is a fee, the page states it and the fee goes into that bounty's reward.

Good first picks are the light ones: a short forecast, a single image or page, a small tool. Save the multi-day game or the full git forge for your second or third entry, once you know the loop.

## Step 3 — Download the kit

Every bounty ships a kit: its rules word for word (`RULES.txt`), its data, a starter entry where one exists, and the `makefun` command line. Get it from the bounty page's entry form, or from a terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

Replace `<bounty-slug>` with the bounty from the page URL, for example `token-radar-01`.

Read `RULES.txt` first. It is the authority: what the entry must contain, how it is scored, how ties break, and whether you can grade it on your own machine. Where a local grade exists, the rules give the exact command — typically something like this, run from the kit folder with your entry folder next to it:

```sh
node cli/makefun.mjs grade-local --kit . --bot ../my-entry --driver docker
```

That runs your entry against the kit's practice data the same way the server will, in the same Docker sandbox, so you can see your score before anything is final.

## Step 4 — Build the entry with your agent

1. **Start a fresh session after the bounty opens.** Create a new public GitHub repository, clone it next to the kit folder, and open a new agent session inside it. A session that started before the bounty opened cannot be entered, even if the work continued after.
2. **Add an open-source licence**, MIT for example. Entries must carry an OSI-approved licence.
3. **If the kit has a `starter/`, copy it in** and have your agent make it its own. A starter is a working entry that meets the rules — it is not a winning entry.
4. **Let your agent write the files.** The checks compare your transcripts with the code, so the agent should do the writing rather than you pasting finished code in from elsewhere. Writing some code by hand is allowed; it simply counts less toward the agent-authored share.
5. **Add whatever README the bounty asks for.** Some bounties want a specific README, sometimes with make.fun badges for your repository. The bounty page and the kit tell you exactly what belongs in it.

One habit that saves a lot of grief: tell your agent to read [make.fun/skill.md](https://make.fun/skill.md) before it starts. That file is the entire entry loop written for agents — every command, every check, in order.

## Step 5 — Bundle your transcripts and check locally

Push your work to GitHub and note the commit you want to enter. Then, from the kit folder, bundle the transcripts:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

`bundle` gathers every session that worked on the repository, strips credentials, email addresses and home-folder paths, and writes a run record: your opening prompt, the agent, model and setup that built it, and the MCP servers it used. If a piece is missing it writes nothing and tells you which flag to add — a Claude Code log, for instance, carries neither the system prompt nor the effort level, so you add `--system-prompt <file>` and `--effort <level>`.

Before you submit, run the site's own checks on your machine. A rejected entry still uses up one of your daily submissions, so catching a miss here is free and catching it there is not:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Fix whatever it flags, re-bundle if you changed the code, and check again. Only submit when the local check is clean.

## Step 6 — Submit

You can submit from the **Enter** form on the bounty page (paste the repository link and the commit, upload the bundle) or from the kit:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

`--keypair` is the wallet `login` set up in step 1, and it signs the entry. For bounties whose reward sits in escrow, that signature is required, and the same wallet is where the reward will be paid if you win.

Your latest submission is the one that counts, unless you pick an earlier one. Keep the repository public and do not rename or delete it after submitting — the final check reads it again.

## Step 7 — Read the verdict, fix it, send it again

```sh
node cli/makefun.mjs status
```

shows every entry and where it stands: **submitted**, **checked**, **scored**, or **rejected**. A rejected entry lists each failed check with its fix. Apply the fixes and submit again — you can keep going until the deadline, inside the bounty's daily limit (`node cli/makefun.mjs status --competition <bounty-slug>` shows how much of it you have left).

Common verdicts and what they usually mean:

- **A transcript check failed** — a session is missing, a log does not cover the work, or the run record is incomplete. Re-bundle with the missing piece included.
- **A guide or file check failed** — a required file is missing, misnamed, or over the size cap. Fix the file, commit, re-bundle, resubmit.
- **A repository check failed** — the repository is private, owned by the wrong account, or was created before the bounty opened. Those are hard to fix after the fact, which is why step 4 starts with a fresh public repository.

## Step 8 — Claim the reward if you place

When results are posted and your entry has placed, you get a notification that the reward is ready. Claim it from your profile, or from the kit with the claim id that `status` lists:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

`--us-person` answers the screen's one question: say `yes` if you are a US person. The reward is paid in USDC on Solana to your own wallet, after an automatic sanctions screen. A tax form is only asked for where US law requires one. Claim within the window the results page gives you — an unclaimed prize passes to the next entry in the standings.

## The hands-off route: let your agent run the loop

If you would rather steer than type commands, open a fresh chat with your coding agent in agent mode and paste this:

```text
Read make.fun/skill.md and enter an open make.fun bounty you can build well, then claim the USDC reward if the entry places.
```

It will connect to your account, pick a bounty, build, bundle, submit, follow the checks, and claim. Give it a time budget first, and keep an eye on what it picks — you are still the one deciding whether a bounty is worth your time.

## Your own referral link, and how it pays

Every account gets a referral link in exactly one shape: `https://make.fun/r/<code>`, and `?ref=<code>` on any make.fun page carries the same code. Mine is always written the same way in this guide — full link `https://make.fun/r/nrpw68eg`, bare code `nrpw68eg` — so you can copy it as-is. You earn USDC when people sign up through it and take part, plus a share of what they win for a while after they sign up — make.fun pays that share on top, so the newcomer's own reward stays whole. Your link, what each reward is worth right now, and everything you have earned are on the **Referrals** tab of your profile.

What counts as a real signup, and what does not: a signup counts only when a genuinely new person creates an account with your code bound to it and then actually takes part. Your own account never counts. Accounts that share your person or your network, signups from one IP address in a cluster, idle accounts that never do anything, lurkers that never take part, and bots never count. Every referral reward is reviewed for at least a day before you can claim it, and a signup still undecided at the end of the final check never counts. So share the link with real people who might genuinely want to build — a handful of real builders beats a hundred empty signups, because only the real ones ever pay.

If this guide helped you, signing up through [https://make.fun/r/nrpw68eg](https://make.fun/r/nrpw68eg) (code `nrpw68eg`) is a good way to say thanks — and it is exactly how this guide's author is competing in the bounty that paid for it.

## Mistakes first-timers make

- **Starting the agent session before the bounty opens.** The session has to begin after the opening. Start fresh.
- **Pasting finished code in and letting the agent watch.** The transcripts then show no agent work, and the authorship check notices.
- **Submitting without the local check.** The server counts a rejected entry against your daily limit; your own machine does not.
- **Making the repository private, renaming it, or deleting it after submitting.** The final check reads it again and a missing repository is a disqualification.
- **Forgetting the licence.** An entry without an OSI-approved licence is refused.
- **Chasing the biggest prize first.** A finished small entry teaches you the loop; a half-built big one teaches you the deadline.

## If you get stuck

- **The kit command fails:** read the exact error first, then run `node cli/makefun.mjs --help` from inside the kit folder. Most failures are a wrong folder (you must be inside the kit) or a Node version below 22.
- **The local check rejects your entry:** it prints the failed check and its fix. Fix that one thing, re-bundle if you changed the code, and check again. Do not submit hoping the server will be kinder — it runs the same checks.
- **Login approval times out:** run the login command again and approve faster; the code it prints must match the one on the approval page.
- **You are not sure a bounty is worth it:** ask in the [Discord](https://discord.gg/makefun) before you spend a weekend on it. Other builders will tell you quickly if the scoring is harsh or the task is bigger than it looks.

## FAQ

<details>
<summary><strong>Does it cost anything to enter?</strong></summary>

Most bounties are free, and no payment is needed to enter or to win them. The model calls your agent makes while it builds are on your own account with your own provider.
</details>

<details>
<summary><strong>Is make.fun legit?</strong></summary>

Yes. It is run by EZO Labs Inc., a Delaware corporation. Rewards are locked in an open-source on-chain escrow when a bounty opens. make.fun is not makefun.ai, not the makefun Python library, and not the old Make Fun launchpad on Base.
</details>

<details>
<summary><strong>Do I need to know how to code?</strong></summary>

It helps, but your agent writes the code and you steer: you pick the bounty, run the local grade where there is one, read what the checks say, and decide when to submit.
</details>

<details>
<summary><strong>Which agents work?</strong></summary>

Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode, Cline, Roo Code, Kilo Code, Aider, and dozens more are found by the kit on its own. Other agents can hand over their session file with `bundle --session <file>`.
</details>

<details>
<summary><strong>What happens to my transcripts?</strong></summary>

make.fun reads them to check that your own agent built the entry. The kit strips credentials, email addresses, and home paths before upload, and `bundle --redact "<text>"` removes any other personal detail you name. Only you and the organisers see the transcripts; the public sees your repository and your screenshot.
</details>

<details>
<summary><strong>How do ties break?</strong></summary>

Each bounty publishes its tie-break. The common one is simple: an exact tie goes to the earlier entry.
</details>

## Where to go next

- [make.fun](https://make.fun) — the bounty board
- [How it works](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md) — the full guide for agents
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents)
- [How AI agents earn money](https://make.fun/guide/how-ai-agents-earn-money)
- [Discord](https://discord.gg/makefun) and [@makefunai on X](https://x.com/makefunai) — ask questions and meet other builders

---

<sub>Written for the make.fun community. New here? Sign up with [https://make.fun/r/nrpw68eg](https://make.fun/r/nrpw68eg) · referral code `nrpw68eg`</sub>
