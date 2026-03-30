<div align="center">
<img src="https://github.com/user-attachments/assets/90497885-d7f8-44af-b126-a449ee11e5a9" />
</div>

# Version Control Is Just Git's Day Job

**Git Stunts** is a GitHub org dedicated to pushing Git to its absolute limits. Anyone can use Git as a version control system. Few treat it as raw material for systems engineering experiments.

Peer beneath the porcelain and get your hands dirty with Git’s plumbing. Learn to think in systems, subvert familiar tools, and pull off real *Git Stunts*.

## The Philosophy: Play As Research

When you want a CMS or a database, your first instinct probably isn't to reach for Git, and that's good. But, hear me out. The goal here isn't conventional efficiency. It's understanding systems from the ground up.

When we use Git to perform these stunts, two things happen:

First, we get to ask, *"What does this enable that a traditional stack doesn't?"* Git gives us an accidental inheritance of properties like offline-first synchronization, cryptographic provenance, and cheap point-in-time recovery. Those are complex features. They're often entire projects in their own right.

Second, we internalize how Git actually works. You stop asking *"What does this command do?"* and instead ask *"What can I do with Git's objects, refs, invariants, and transitions?"*

## Who This Is For

This series is for people who know how to use Git but suspect there is a much stranger machine hiding underneath its interface.

If you mostly interact with Git through a GUI, this will show you what the GUI is politely abstracting away. If you have ever looked at a plumbing command and wondered *"What on earth is that for?"*, your inquisitiveness will be rewarded here.

And if you already read man pages, inspect raw objects, trace code paths, and treat tools as systems rather than products, welcome home.

This series is **not** for people looking for best practices, conventional application architecture, production checklists, or boringly sensible defaults. These projects prioritize understanding over orthodoxy and curiosity over safety rails.

## Creativity Comes From Constraints

Despite the name, this series is not about exploits, hacks, or terminal theater. The constraint is the point. By limiting ourselves to Git’s actual primitives, we are forced to reason carefully about data, state, and invariants.

These are **stunts**, not hacks: deliberate, reversible, and grounded in how the system really works. The goal is not to get away with something. The goal is to understand the system well enough that surprising architectures emerge naturally.

If you enjoy taking things apart, putting them back together in strange ways, and learning by misuse rather than memorization, you are in exactly the right place.

## The "Linus" Threshold

I call these "stunts" because they exist right at the edge of technical sanity.

The benchmark for what makes a good Git Stunt is a solution so unorthodox that if Linus Torvalds saw it, he would stop what he was doing, remove his glasses, rub his exhausted eyes, sigh deeply, and then, after a long silence, he would mutter *"You know what? Have fun"*, shake his head, then walk away.

I like to imagine he would secretly still check in every now and then to see if we actually pull these off.

We’re going to have some fun. We're going to use the plumbing to build things that shouldn't exist, and in the process, we're going to learn how to think about systems design from the bare metal up.

## What To Expect

Each post in this series follows a rigorous **Architecture Decision Record** (ADR) format to ensure that we're not just making a mess, but making a point. Every stunt is reproducible, documented, and intentionally constrained. 

All posts in the series will include:

- **The Stunt:** subversion of Git internals.
- **The Conventional Path:** How this is "supposed" to be solved.
- **The Source:** A link to a fully working, Dockerized GitHub repo.
- **The ADR:** A formal breakdown of context, decision, and consequences.
- **The Reality Check:** When and *when not* to use the technique.

## The Set List

### Git As Foundation

What even is Git? Before we can build complex applications on top of Git, we need a small set of primitives that treat Git as substrate.

| Part | Title | Stunt | Lesson |
|------|-------|--------|--------|
| I | [git-cas](https://github.com/git-stunts/git-cas): Git as Blob Store | A content-addressable storage layer built directly on Git objects | Git’s primitive is the object database |
| II | [git-warp](https://github.com/git-stunts/git-warp): Stateful Systems on Top of Immutable Objects | A higher-level state and traversal layer over Git’s immutable model | State can be constructed without pretending mutability exists |

### Git As Engine

Learn how to build applications that are powered by Git, not just versioned by it.

| Part | Title |Stunt | Lesson |
|------|-------|-------|--------|
| III | Git Stargate: Git as Zero-Trust Gateway | AST-validation in `pre-receive` hooks | Shift-left security, moving trust to the transport layer |
| IV |	Shiplog |	The Commit as a Structured Event Ledger	| Deployment provenance, policy enforcement, and tamper-evident audit trails |
| V | [Git as CMS](https://github.com/git-stunts/git-cms) | Git's `commit-tree` doubles as a DB-less API | How to reduce operational complexity via protocols |
| VI | Git as Key-Value Store | Offline-first KV-store using OIDs and Git notes | CAP theorem, consistency vs availability in distributed systems | 

### Git As System

Can Git be infrastructure?

| Part | Title | Stunt | Lesson |
|------|-------|------|--------|
| VII | Git as Bus | Using `post-receive` hooks for serverless pub/sub | Event-driven architecture, high-reliability event delivery (within constrained domains) |
| VIII | Git FUSE | FUSE-based virtualized filesystem via Git OIDs | Virtualization, Lazy-loading and on-demand hydration |

### Git Weird

Make Git remember things.

| Part | Title |Stunt | Lesson                                           |
|------|-------|-------|--------|
| IX | Agent-Native Git | RAG and decision-tracking via Git history | AI infra, verifiable Merkle trees for LLM memory |

## Find New Ways To Use Old Tools

When we look at a tool we use every day and ask *"What else can this thing do?"* sometimes we find surprising new ways to use them. The ability to deconstruct a system to its primitives is one of the most valuable skills in an engineer's toolkit.

Whether you're here to learn or you just want to see how far Git can be stretched before it breaks, I hope you have as much fun reading this series as I had writing it. 

Fork these repos and Git good.

---

Copyright © 2026 [James Ross](https://github.com/flyingrobots)
