---
title: No refactoring issues
description: Understanding tech debt and a pragmatic proposal on handling it.
author: Nico Rehwaldt
---

# *No Refactoring Issues*

#### The inevitable cleanup, and how not to do it.

<small>[`Nico Rehwaldt`](https://github.com/nikku) 2025</small>

---

## Understanding *accidental* and *essential* complexity in software engineering.

---

#### *Accidental* complexity is what engineers create and can fix.

#### *Essential* (inherent) complexity is caused by the problem to be solved, and cannot be removed.

<small>Adapted from [No silver bullet](https://en.wikipedia.org/wiki/No_Silver_Bullet)</small>

---

### Accidental complexity has many forms, in code and UX

A quick fix enables interaction `A`; now, the existing user journey `B` is broken.

We plan to do `X` as a first step towards a higher goal, but never follow up.

----

#### We introduce accidental complexity all the time, through leaky abstractions, half-baked trade-offs, and "quick fixes".

---

### Accidental complexity is inevitable

The environment in which an application operates changes, rendering UIs outdated and dependencies vulnerable.

An application decays in code and user experience, whether you touch it or not.

---

### We want to have measures to keep our applications in check.

---

## Technical debt = *accidental complexity, in code*

---

#### [Technical debt is] a collection of design or implementation constructs that make future changes more costly or impossible ([ref](https://en.wikipedia.org/wiki/Technical_debt)).

---

[![essential complexity and cruft, as described by Martin Fowler](./technical-debt-cruft-fowler.png)](https://martinfowler.com/bliki/TechnicalDebt.html)

---

### How to tame it? Through *refactoring*.

---

#### Refactoring is a [...] technique for restructuring an existing body of code, altering its internal structure without changing its external behavior. ([ref](https://refactoring.com/))

---

#### The goal of refactoring is to adapt existing code to make new changes straightforward.

---

#### Refactoring ensures that the application, over time, stays fit for purpose, for its use.

---

![A graph showing the velocity of changes decreasing over time, if no refactoring is applied](./velocity-without-refactoring.png)

---

![A graph highlighting the actual "work done", if no refactoring is applied.](./velocity-without-refactoring-work-done.png)

---

#### Refactoring keeps the system fit for purpose and the velocity in check.

---

![](./velocity-continuous-refactioring.png)

---

#### By doing it *continuously*, we *keep the effort low*.

---

#### By doing it *continuously*, we *make it a habit*, a normal thing, an inherent part of our developer tool belt. We make it a path traveled.

---

[![Two paths, one is less traveled](./paths-traveled-1.png)](https://medium.com/@davidbillson/allowing-for-change-abcf02338251)

---

#### By doing it *opportunistically*, *focusing on the current task* at hand, we ensure that *we do it where it matters most*: in critical code paths.

---

![](./velocity-compared.png)

---

## Rules of (not) refactoring

---

### :speech_balloon: "I created an issue for it."

---

### :loudspeaker: "I *did not bother to fix this thing today, where I have context*, but hope a magic wizard will some day come and fix it."

---

### :bulb: Nobody is going to clean up after you. It is *your code base*, *your responsibility*. *You are* the one *suffering* from the mess you leave behind.

---

<!--config
name=no-refactoring-issues
-->

### :one: `no-refactoring-issues` - do not allow "refactoring issues", fix things you encounter.

---

### :speech_balloon: "I don't dare to touch this code path, because I don't know what breaks."

---

### :loudspeaker: "*Our (automated) testing practice sucks.* I don't trust it to meaningfully report whats broken, when I change things."

---

### :loudspeaker: "*Our (automated) testing practice sucks.* I know I have to fix 1000 tests after this small change."

---

<!--config
name=architect-for-testability
-->

### :two: `architect-for-testability` - build a system that is easy to test, and it will be well composed, easier to maintain, and understand. Support it with a comprehensive, fast, and reliable test suite.

---

### :speech_balloon: "I could not fix it."

---

### :loudspeaker: "*I was too lazy to fix it*, and I hope someone else will do it someday."

---

### :question: Who is the magic wizard who can fix things for you?

---

<!--config
name=easier-when-practiced
-->

### :three: `easier-when-practiced` - Yes, refactoring can be complicated. It only gets harder if we don't practice it, or let the code base erode further. *Start refactoring today.*

---

### :speech_balloon: "I did not know cleaner was my job description."

---

### :loudspeaker: "I have a very simplistic view of what a [developer's job](https://github.com/nikku/talks/tree/main/2024-team-jobs-environment-composition#jobs-and-environment) is."

---

### :question: Who on your team has cleaner in their job description? Who ensures things are maintainable for the long run?

---

<!--config
name=embody-the-maintainer
-->

### :four: `embody-the-maintainer` - ensure that the maintainer perspective is part of everything you do. Add it to your _definition of done_, enforce it.

---

### :speech_balloon: "I am behind schedule to wrap up this issue".

---

### :loudspeaker: "I keep the code base in this state so *I'll be behind schedule next time, too*".

---

<!--config
name=invest-in-tomorrow
-->

### :five: `invest-in-tomorrow` - do not accept today's excuses, invest reasonably to *set yourself up for (your) future success*.

---

<!--config
theme=eco
-->

### Always leave the campground cleaner than you found it.

###### (Boy scouts of America)

---

## When is a refactoring successful? *Is it always worth it?*

---

### :speech_balloon: "Next time we should clean this up."

---

### :bulb: No body is going to prioritize your *cleanup*, it *ships no user value*. Clean it up now, in context, or keep suffering.

---

<!--config
name=opportunistic-in-context
-->

### :five: `opportunistic-in-context` - make reasonable efforts to clean up the mess you encounter, while you have context. *It is cheaper now.*

---

### :speech_balloon: "I refactored, but the code base is no better now."

---

### :loudspeaker: "I changed things without a plan."

---

### :bulb: The feeling that "something is wrong" does not automatically lead to a successful outcome.

---

<!--config
name=know-what-and-why
-->

### :seven: `know-what-and-why` - understand what you do and why, before you do. Use the plan to assess if the actual step of doing is *feasible* and *worth the effort*. If in doubt, get a second opinion.

---

### :speech_balloon: "Refactoring makes a code review hard to execute."

---

### :loudspeaker: "I did not properly structure my work, so others can follow along."

---

<!--config
name=make-it-explicit
-->

### :eight: `make-it-explicit` - Separate refactoring and feature development. Document [what changes, why](#know-what-and-why). Structure work in multiple PRs, or multiple commits.

---

### :speech_balloon: "Is this [bike-shedding](https://en.wikipedia.org/wiki/Law_of_triviality)?"

---

### :bulb: Be concious about your time. Put your attention to places _where it matters_. Be able to argue [what changes, why](#know-what-and-why). Get buy-in from your team.

---

<!--config
name=improve-substantially
-->

### :nine: `improve-substantially` - Cosmetic changes are a waste of time and attention - refactor where it is worth the effort. Manage technical debt wisely, you'll never fully get rid of it anyway.

---

<!--config
theme=eco
-->

## Make refactoring and continuous improvement integral parts of our work.

---

### Getting there is a *cultural* and *technical challenge*

Cultural, because we need to get over old habbits, change our way of working.

Technical, because the first steps to a better code base are the hardest, and skills have to be learned.

---

### A [healthy environment](#environment) and following [basic rules of refactoring](#rules-of-refactoring) can help.

---

<!--config
name=environment
-->

### Environment

* [:one:](#no-refactoring-issues) `no-refactoring-issues`
* [:two:](#architect-for-testability) `architect-for-testability`
* [:three:](#embody-the-maintainer) `embody-the-maintainer`
* [:four:](#easier-when-practiced) `easier-when-practiced`
* [:five:](#invest-in-tomorrow) `invest-in-tomorrow`

---

<!--config
name=rules-of-refactoring
-->

### Rules of refactoring

* [:six:](#know-what-and-why) `know-what-and-why`
* [:seven:](#opportunistic-in-context) `opportunistic-in-context`
* [:eight:](#make-it-explicit) `make-it-explicit`
* [:nine:](#improve-substantially) `improve-substantially`

---

<!--config
name=note-to-managers
-->

### Note to managers

* Empower your peers, setup a [healthy environment](#environment)
* Provide clear expectations, establish [accountability](https://www.merriam-webster.com/dictionary/accountability)
* Empower your peers to live by [the rules of refactoring](#rules-of-refactoring)
* Setup [friendly reminders](#definition-of-done)

---

## Thanks

# :heart:

---

## Appendix

---

### Things that may not work (1)

* **Refactoring Friday** - You'll never complete your refactoring in time.
* **Refactoring issues** - Offload today's responsibility to your future self.
* **30% time for refactoring** - Add this to the 13% working on papercuts, the 37.85% reviewing, the 20% discussing strategic matters, and the 23.14% coding.

---

### Things that may not work (2)

* **Rebuild periodically** - Nothing is more permanent than a temporary solution. Also, remember the [second system effect](https://en.wikipedia.org/wiki/Second-system_effect).
* **Solve it with more process** - What will this magic process be?

---

## Simple reminders can go a long way

---

<!--config
name=definition-of-done
-->

![definition of done](./definition-of-done.png)

---

## Refactoring and (re-) architecting are related activities

---

[![](./lean-architecture.png)](https://nikku.github.io/talks/2021-lean-architecture)