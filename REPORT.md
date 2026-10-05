# Suspected Unauthorized Usage on a Claude Pro Account — Incident Report

**Prepared:** Mon 5 Oct 2026 (MYT)
**Account:** Claude Pro (email withheld: this repository is public)
**Timezone used throughout:** Asia/Kuala_Lumpur (MYT, UTC+8)
**Status:** Unconfirmed. The evidence shows unusually fast quota use. It does not prove a third party was involved.

> **Read this first: limits of this report.**
> - The screenshots have no embedded timestamps. Every time attached to a screenshot comes from the account owner's notes.
> - I can't see Anthropic's server-side sign-in, device or usage logs. Only Anthropic Support can confirm or rule out unauthorized access.
> - I can see the account's Claude Code cloud sessions and Routines (scheduled tasks), and Section 3 uses that data. I can't see Cowork sessions, chat history or connector logs.
> - The account owner's draft mentions an "August 2026 warning about infostealer session theft". I could not verify that warning. My knowledge only runs to June 2026. Include a link to the warning or remove that line.

---

## 1. Summary

- Over about 15 hours on 5 Oct, weekly usage rose from **57% to 91%**. The current 5-hour session hit **100%**. The Usage page now predicts the weekly limit will run out "tomorrow morning, before Wednesday's reset".
- **76%** of this week's usage is labelled **"Other"**, not Chats, Cowork or Claude Code. The page doesn't say what "Other" covers.
- The session reset times suggest the 5-hour session windows ran **back to back**: about 1:10 AM, 6:10 AM, 11:10 AM and 4:10 PM. If nobody used the account between about 6 AM and 4 PM, that is the strongest sign of usage the owner didn't start. This is an inference, and Section 4 explains its weak points.
- **The draft email says no other Claude sessions were running. My check found otherwise.** Two old cloud sessions, created in June from Android, were reactivated today at about **12:53 PM MYT**. Both failed to start with a GitHub authentication error. See Section 3.
- Both scheduled Routines are disabled. Their last runs were on 2 Oct and 3 Oct, so they can't explain today's usage.

## 2. Timeline (from screenshots and owner's notes)

| Time (MYT, 5 Oct) | Current session | Weekly | Session reset at | Source |
|---|---|---|---|---|
| ~1:14 AM | 8% | 57% | 6:10 AM | Screenshot (on track) |
| ~1:14 AM | — | by product: Other 76%, Cowork 20%, Chats 4%, Claude Code 0% | — | Screenshot (exact time unconfirmed) |
| ~1:25 AM | 40% | 60% | 6:10 AM | Screenshot |
| ~12:53 PM | — | — | — | Server data: 2 old cloud sessions reactivated, both failed (Section 3) |
| 4:47 PM | 42% | 86% | 9:10 PM (in 4 h 22 m) | Owner's note. **No screenshot attached.** |
| later, before 9:10 PM | 68% | 88% | 9:10 PM | Screenshot ("Heads up…") |
| later, before 9:10 PM | 100% | 91% | 9:10 PM | Screenshot ("Heads up…") |
| 5:38 PM | — | — | — | This investigation session started. It is billed to cloud session credits, not the plan (see 4.4). |
| **5:41 PM** | **0%** | **0%** | "Starts with your first message" | **Owner used the free Full reset.** Screenshot. Cloud session credit: $99 of $100 left (expires 5 Nov, 3:59 PM). |
| 6:15 PM | — | — | — | Re-check of cloud sessions and Routines: no new sessions, no changes, Routines still disabled |
| **~10:51 PM** (screenshot; time from session reset) | **100%** | **13%** | **Tue 3:40 AM** | Screenshot ("On track"). Cloud credit $98 of $100. A reset at 3:40 AM means this window opened ~10:40 PM, so the session hit 100% within ~11 minutes. Cloud session list at 10:51 PM: still no new sessions; this investigation session is billed to promotional credit (~$1.08 total). |

Other details on the Usage page:
- The weekly limit resets **Wednesday 7:00 PM**, so this week began Wed 30 Sep 7:00 PM.
- A free "Full reset" was available until 23 Oct. **The owner used it at 5:41 PM on 5 Oct.** Usage then showed 0% session and 0% weekly, with no resets left.
- Usage credits are off and the balance is 0, according to the owner.

## 3. Findings from the account's Claude Code cloud data

I read this data directly from the account during this session.

**Cloud sessions (3 total):**

| Session | Created | Origin | Last updated (MYT) | Notes |
|---|---|---|---|---|
| "Pro account unauthorized usage investigation" | 5 Oct 5:38 PM | claude.ai web | running | This investigation |
| "Asian fusion restaurant website" | 15 Jun | Android | **5 Oct 12:53 PM** | Status *pending*. Start-up failed: "Authentication failed while accessing the repository john123-1/PHP-Login-System". Worker epoch 4. |
| "Caveman mode" | 5 Jun | Android | **5 Oct 12:53 PM** | Same failure. Worker epoch 3. |

What this means:
- Something tried to resume two months-old sessions at almost the same moment today. A worker epoch above 1 suggests the session has been restarted before, so these may not be the first attempts.
- Both failed at checkout, before any model work would normally begin. **They probably used little or no quota.** I can't confirm that from here.
- Possible innocent causes: opening the Claude app on a phone, the web or the desktop app (both sessions appear under "Recents" in the owner's Claude Code desktop sidebar), an app update reconnecting old sessions, or an automatic retry. **Ask yourself whether you used the Claude Android app or claude.ai/code around 12:53 PM.** If you didn't, raise this with Support as a specific lead.
- The GitHub authentication failure means the GitHub connection no longer has access to that repository. That may simply be expired authorization. It is not evidence of an attack by itself.

**Routines (scheduled tasks), 2 total, both disabled:**

| Routine | Schedule | Model | Last run (MYT) | Disabled at (MYT, approx.) |
|---|---|---|---|---|
| Daily news briefing | 8:00 AM daily | Sonnet | 2 Oct, 8:07 AM (~10 min) | 2 Oct, ~11:39 PM |
| Daily malaysia news briefing | 7:00 PM daily | Opus | 3 Oct, 7:14 PM (~1 min) | 4 Oct, ~1:37 PM |

Both Routines have the **Shopify**, Claude Docs and Claude Code Remote connectors attached. They are disabled, but those connectors are still authorized on the account. Review them (Section 6).

## 4. Analysis

### 4.0 After the 5:41 PM reset (strongest evidence so far)
- In about 5 hours after the reset, weekly usage went from **0% to 13%**. The current session hit **100%**.
- The windows fit back-to-back chaining again: ~5:40 PM to ~10:40 PM, then a new window from ~10:40 PM that was **full within ~11 minutes**.
- None of this shows up in Claude Code cloud sessions or Routines. This investigation session is billed to cloud promotional credit.
- **If the owner didn't use chats, Cowork, Claude in Chrome, the desktop app or the mobile app between 5:41 PM and 10:51 PM, this is very likely usage the owner didn't start.** It may come from another person or a process holding a valid session. I can't tell which surface it came through.

### 4.1 How fast session usage feeds weekly usage
- 1:14 to 1:25 AM: session +32 points, weekly +3 points.
- Evening: session +58 points (42 to 100), weekly +5 points (86 to 91).
- So 100% of one 5-hour session is roughly **6–12 points** of weekly usage. The range is wide because the page rounds to whole percentages.

### 4.2 The jump from 60% to 86%
- Weekly usage rose **26 points** between ~1:25 AM and 4:47 PM.
- The 1:10 AM session could add at most ~4–7 more points (40% to 100%). The 4:10 PM session added ~2–5 points by 4:47 PM.
- That leaves roughly **14–20 points** unaccounted for. That is more than one full session's worth, and **probably two sessions between ~6:10 AM and ~4:10 PM**.
- The reset times fit an unbroken chain of 5-hour windows: 1:10 AM, 6:10 AM, 11:10 AM, 4:10 PM.

**Caveats:**
- I'm not certain how Anthropic anchors session windows. They may round, or start at the first message after the previous window expires. If a window starts at the first message, an unbroken chain means usage started within minutes of each reset. That fits continuous automated use, or a person using the account through the morning.
- Weekly usage may be weighted by model. For example, Opus may cost more per message than Sonnet. If so, the session-to-weekly ratio isn't constant.

**The key question for you:** were you, or anything you run, using Claude between about **6 AM and 4 PM** today? If not, the numbers strongly suggest someone else, or some background process, was.

### 4.3 The "Other" category (76%)
- The breakdown shows **Claude Code at 0%**, yet this account runs Claude Code cloud sessions. The Usage page also has a "Cloud session credits" section.
- It's possible that cloud sessions, Claude in Chrome, Routines, mobile or other surfaces are counted under "Other". **This is a guess, not something I can confirm.** Ask Support (question 2 in the email) to say exactly what "Other" contains.

### 4.4 Ways today's usage could be legitimate
Rule these out before concluding there was theft:
1. Using Claude (any surface: web, desktop, Android, Cowork, Claude in Chrome) during the morning and afternoon, including drafting the support email.
2. ~~This investigation session~~: **ruled out.** The 5:41 PM screenshot shows cloud session credit at $99 of $100. So this cloud session is billed to that credit, not to the plan's session or weekly limits.
3. Long-running Cowork tasks, or a Claude in Chrome agent, left running.
4. Large attachments or long conversations. Every follow-up message re-sends the whole context.

### 4.5 Device compromise
- An infostealer usually steals browser session cookies. With those, an attacker can use the account **without your password and without triggering 2FA**, until the session is revoked.
- A common sign of such malware on Windows is **Task Manager "disabled by your administrator"**. Malware often sets the `DisableTaskMgr` policy so it can't be ended.
- If you've seen that on your Windows PC, treat the PC as possibly infected. **Clean it before signing back in.** Otherwise new cookies will be stolen again.

## 5. Corrections to the draft support email

1. **"No other Claude sessions were running"** is not accurate. Two cloud sessions were reactivated at 12:53 PM (Section 3). Mention them.
2. **The 4:47 PM data point (86% / 42%) has no screenshot.** Attach one, or note that it is from memory.
3. **The "August 2026 warning" reference.** I could not verify it. Link it or remove it.
4. **"[changed my password / will change my password]"** needs a decision. Claude.ai may sign you in by email link or Google instead of a password. If so, the step that matters is securing your **email/Google account** and **signing out all Claude sessions**.
5. Add the **Routine connectors** details and note that **the Full reset was used at 5:41 PM** (the earlier numbers are gone from the page now, so the screenshots are your only record).
6. Don't put the exact quota numbers in a public place. This report withholds your email because the repository is public.

## 6. Recommended actions (in order)

1. **Clean the device first.** Run a full offline scan on the Windows PC, for example Microsoft Defender Offline scan. Check for unknown browser extensions and startup programs. Check whether Task Manager is policy-disabled.
2. **Secure your email/Google account from a clean device.** Change the password, turn on 2FA, and review "Your devices" and third-party access.
3. **Sign out all Claude sessions**, then sign back in only on clean devices.
4. **Review connectors and integrations.** Disconnect any you don't use, especially **Shopify**. Also review GitHub (Claude GitHub App and authorized OAuth apps) and the **Claude in Chrome** extension.
5. **Archive the two stale cloud sessions** ("Asian fusion restaurant website", "Caveman mode") so nothing can resume them. They can be unarchived later.
6. **The Full reset was used at 5:41 PM, so you now have a clean baseline.** Usage reads 0% / 0% and the session window "starts with your first message". **Don't use Claude for a while, for example overnight, and then check again.** If the session meter has started or the weekly figure has risen without you using Claude, that is strong evidence of usage you didn't start. Screenshot it with the clock visible. There are no resets left, so finish steps 1–4 as soon as possible.
7. **Keep watching the Usage page.** If the session meter rises while you aren't using Claude, take a screenshot with the system clock visible and send it to Support.
8. **Send the support email** (Section 7) with all five screenshots attached. Include the 4:47 PM one if you have it.

## 7. Revised support email (ready to send)

> **Subject:** Suspected unauthorized usage on my Pro account – please investigate
>
> Hello Anthropic Support,
>
> I believe someone else may be using my Claude Pro account, or something on my account is using quota without my action. Please investigate.
>
> **Account email:** [your account email]
> **Plan:** Pro
> **Timezone:** Asia/Kuala_Lumpur (UTC+8)
>
> **What I observed (screenshots attached; times are from my notes):**
> - Mon 5 Oct, ~1:14 AM: weekly usage 57%, session 8% (reset 6:10 AM). "This week's usage by product": Other 76%, Cowork 20%, Chats 4%, Claude Code 0%.
> - ~1:25 AM: weekly 60%, session 40%. The session rose 32 points in about 11 minutes.
> - 4:47 PM: weekly 86%, session 42%, reset 9:10 PM. So a new session window began ~4:10 PM, which I did not knowingly start. [Screenshot attached / from memory]
> - Later that evening: weekly 88% then 91%. The session reached 100%. The page now says I will run out before Wednesday's reset.
> - Weekly usage rose 26 points between ~1:25 AM and 4:47 PM. The session resets (1:10 AM, 4:10 PM) fit back-to-back 5-hour windows through the morning, when [I was not using Claude / I used Claude only briefly].
>
> **What I checked:**
> - Both Routines (scheduled tasks) are disabled. They last ran on 2 Oct and 3 Oct (MYT).
> - Two old Claude Code cloud sessions from June ("Asian fusion restaurant website" and "Caveman mode") were reactivated around 12:53 PM MYT on 5 Oct. Both failed with a GitHub authentication error. [I did / did not] open the Claude app around that time.
> - Usage credits are off and my balance is 0.
>
> **What I need:**
> 1. Please check for sign-ins, devices, sessions, or API/connector activity on my account that are not mine, especially between 6 AM and 4:10 PM MYT on 5 Oct, and tell me what you find.
> 2. Please explain what the "Other" usage category contains and what drove it this week.
> 3. Please review the usage and restore any quota consumed by unauthorized activity.
> 4. Please tell me what else I should do to secure the account.
>
> I used my free Full reset at 5:41 PM MYT on 5 Oct. Usage showed 0% session and 0% weekly. I will report any usage that appears while I am not using Claude. I have [signed out of all devices / secured my email account / scanned my PC for malware].
>
> Thank you,
> Jeff Hoh
