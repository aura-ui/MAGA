# MAGA
[![MAGA](https://raw.githubusercontent.com/aura-ui/MAGA/main/assets/maga-badge.svg)](https://github.com/aura-ui/MAGA)

**Make the Web Great Again.**

> Note: "MAGA" here is a playful acronym for Aura's vision that the Web Platform stays the foundation — not a political slogan.

Yes, the acronym is deliberately provocative.

And yes, it's a joke.

The idea behind it isn't.

> **Less framework. More platform.**

This repository is the home of that vision for [Aura UI](https://github.com/aura-ui).

## Three levels of the same idea

| Layer | Name | Role |
| --- | --- | --- |
| **Vision** | **MAGA** | Make the Web Great Again — keep the Web Platform central, not buried under frameworks |
| **Architecture** | **Platform First** | Decide in this order: platform first; add an abstraction only when the platform isn't enough |
| **Discipline** | **MANA** | Minimal. Aligned. Native. Additive. — how to judge an abstraction |

> **MAGA is the vision.**  
> **Platform First is the architecture.**  
> **MANA is the discipline — and the part you can actually apply.**

## Platform First

Platform First is not "vanilla JavaScript."

It is not "no dependencies."

It is not "never use a framework."

It is an order of decisions.

The traditional model often looks like:

```text
Framework
    ↓
Framework abstractions
    ↓
Application
    ↓
Browser
```

Platform First reverses the direction:

```text
Web Platform
    ↓
Application
```

And when the platform isn't enough:

```text
Web Platform
    ↓
Thin abstraction
    ↓
Application
```

The browser is not merely an implementation detail.

**The platform is the default. The abstraction is the addition.**

## MANA

Platform First describes the architecture.

MANA describes how we make decisions inside that architecture.

> **MANA doesn't tell you whether to use an abstraction. It tells you how to judge one.**

**MANA is four questions:**

| Letter | Meaning | Ask |
| --- | --- | --- |
| **M** | **Minimal** | How much abstraction do we actually need? |
| **A** | **Aligned** | What meaning does the abstraction preserve? |
| **N** | **Native** | What does the abstraction build on? |
| **A** | **Additive** | What happens when you remove the abstraction? |

> **The burden of proof is on the abstraction.**

In practice:

- **Minimal** — Does the browser already solve this?
- **Aligned** — Does the API preserve native semantics?
- **Native** — Is it built on browser primitives?
- **Additive** — What still works if we remove it?

### Removal Test

> **If you remove the abstraction, what remains?**

Prefer:

```text
platform + capability
```

over:

```text
platform replacement
```

Full checklist and examples: [checklist.md](./checklist.md)

## Platform First is not Platform Only

MANA is a decision-making discipline, not a purity test.

Not anti-framework ideology. Not "rewrite everything in vanilla JS."

Sometimes the platform is enough. Sometimes a library or framework is the right engineering decision. Use it.

The question is not:

> "Can we avoid an abstraction?"

The question is:

> **"Does this abstraction add enough value to justify another model?"**

## Start here

| Doc | What it is |
| --- | --- |
| **[essay.md](./essay.md)** | Full essay — canonical long-form argument |
| **[checklist.md](./checklist.md)** | Short MANA checklist for APIs and libraries |
| **[Aura Router](https://github.com/aura-ui/router)** | First practical experiment |

## In Aura packages

Aura libraries should be judged by MANA:

- ordinary platform primitives stay recognizable;
- abstractions stay thin and intentional;
- capability is added without making the platform disappear.

That is the boundary the essay defines:

> **Add capability without making the platform disappear.**

---

> **MAGA is the vision.**  
> **Platform First is the architecture.**  
> **MANA is the discipline.**
>
> **Build on the Web. Don't rebuild it.**
