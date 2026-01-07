# Welcome to Git Stunts

> _Git isn't really a version control system at all._

<img alt="Git Stunts" src="https://github.com/user-attachments/assets/6dbfbdd4-e6f8-43cc-b693-3492d173f221" width="420" align="right" />


If you understand that sentence, this series is for you. If you don’t, it will be by the end. Git is really a content-addressable filesystem with a directed acyclic graph (DAG) built on top.

Most of us interact with Git through the **porcelain**—`push`, `pull`, `commit`—and never touch the **plumbing** underneath. But if you `man git`, you'll find that Git’s true power lies in its plumbing.

**Git Stunts** is a series dedicated to tinkering with that plumbing. We are going to take Git apart and put it back together in ways that were never intended.

This GitHub org is where I'll publish all of the source code modules for the stunts.

## The Philosophy: Play as Research

Why do this? If you’re looking for the most "practical" way to build a CMS or a database, you’d reach for Postgres or Contentful. But the goal here isn't conventional efficiency; it’s **first-principles engineering**.

When we use Git to perform these "stunts," two things happen:

**Architectural Divergence:** We get to ask, *"What does this enable that a traditional stack doesn't?"* By using Git as a backend, we accidentally inherit properties like offline-first synchronization, cryptographic non-repudiation, and infinite point-in-time recovery. Those are complex features that take months to build into a standard SQL-based app.

**Technical Mastery:** You will internalize how Git actually handles data, hashes, and refs. You stop memorizing commands and start understanding **state**.

## Who This Is For

This series is for people who use Git daily and have wondered how it actually works. If you primarily interact with Git through a GUI, it will dramatically deepen your understanding of what those tools are abstracting away. If you’ve ever looked at the Git CLI commands and thought *“what on earth does that one do?”*, this series shines a light into some of Git’s darker corners. And if you’re already reading man pages, tracing code paths, and treating tools as systems rather than products—good. You’ll fit right in.

If you’re looking for best practices, production checklists, or drop-in architectural advice, this probably isn’t for you. These stunts prioritize understanding over orthodoxy, and curiosity over safety rails.

Despite the name, this series isn’t about clever exploits or party tricks. The constraint is the point. By limiting ourselves to Git’s actual primitives, we’re forced to reason carefully about data, state, and invariants.

These are stunts, not hacks: deliberate, reversible, and grounded in how the system really works. If you’re looking for exploit chains or cinematic “hacker” theatrics, you’re in the wrong place. This is about understanding tools deeply enough that surprising architectures emerge naturally.

If you enjoy taking things apart and putting them back together in new ways, going deep on familiar tools all the way down to their primitives, and you believe that real engineering insight comes from misuse, not memorization, then you’re in exactly the right place.

## The "Linus" Threshold

I call these "stunts" because they exist right at the edge of technical sanity.

The benchmark for what makes a good Git Stunt is a solution so unorthodox that if Linus Torvalds saw it, he would stop what he was doing, remove his glasses, rub his exhausted eyes, sigh deeply, and then, after a long silence, he would mutter *"You know what? Have fun"*, shake his head, then walk away.

I like to imagine he would secretly still check in every now and then to see if we actually pull these off.

We’re going to have some fun. We're going to use the plumbing to build things that shouldn't exist, and in the process, we're going to learn how to think about systems design from the bare metal up.

## What to Expect

Each post in this series follows a rigorous **Architecture Decision Record** (ADR) format to ensure that we're not just making a mess, but making a point. Every stunt is reproducible, documented, and intentionally constrained. 

All posts in the series will include:

- **The Stunt:** subversion of Git internals.
- **The Conventional Path:** How this is "supposed" to be solved.
- **The Source:** A link to a fully working, Dockerized GitHub repo.
- **The ADR:** A formal breakdown of context, decision, and consequences.
- **The Reality Check:** When and *when not* to use the technique.

## The Set List

| Part | Title | Status | Stunt | Lesson |
|------|-------|--------|-------|--------|
| I | Git as CMS | In Review, Pending Publication | Git's `commit-tree` doubles as a DB-less API | How to reduce operational complexity via protocols |
| II | Git as Key-Value Store | Planned | Offline-first KV-store using OIDs and Git notes | CAP theorem, consistency vs availability in distributed systems | 
| III | Git as Bus | Planned | Using `post-receive` hooks for serverless pub/sub | Event-driven architecture, high-reliability event delivery (within constrained domains) |
| IV | Git FUSE | Planned | FUSE-based virtualized filesystem via Git OIDs | Virtualization, Lazy-loading and on-demand hydration |
| V | Agent-Native Git | Planned | RAG and decision-tracking via Git history | AI infra, verifiable merkle trees for LLM memory |
| VI | Git as Zero-Trust Gateway | Planned | AST-validation in `pre-receive` hooks | Shift-left security, moving trust to the transport layer |

## Adult Supervision Required

The posts in this series are about learning more than just how Git works under the hood. We aren't playing Macgyver with Git just for the fun of it; we do it to understand **how to think outside the box when conventional tools fail**.

The most elegant solutions often come from looking at a tool you use every day and ask *"What else can this thing do?"*

While I wouldn't recommend replacing your production Postgres instance with a series of Git notes, the **mental models** we build here are universal. The ability to deconstruct a system to its primitives is one of the most valuable skills in an engineer's toolkit.

So remember: try these stunts at your own risk! Whether you're here to learn or you just want to see how far Git can be stretched before it breaks, I hope you have as much fun reading this series as I had writing it. 

The one bit of advice I have before we get started is: when you're working on tools that directly interact with Git repos, **always** run the tests in Docker!

> [!note]
> **Quick note on licenses:** Code will be made available under Apache 2.0 and all writing CC BY 4.0.  
> Please steal freely, attribute honestly, and don't be weird. Well, don't be weird about this in particular.

Copyright © 2026 [James Ross](https://github.com/flyingrobots)
