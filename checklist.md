# MANA checklist

Use this when designing or reviewing an abstraction in an Aura package — or anywhere you want Platform First decisions.

**MANA — Minimal. Aligned. Native. Additive.**

> MANA doesn't tell you whether to use an abstraction. It tells you how to judge one.

## Four questions

When evaluating an abstraction, ask:

- **Minimal** — Does the browser already solve this?
- **Aligned** — Does the API preserve native semantics?
- **Native** — Is it built on browser primitives?
- **Additive** — What still works if we remove it?

If the answers are unclear, that's a reason to look more closely at the abstraction.

### M — Minimal

**How much abstraction do we actually need?**

- [ ] Does the platform already solve this?
- [ ] Are we adding a system only because a framework normally does?
- [ ] Is this the smallest abstraction that solves the problem?
- [ ] Are we minimizing unnecessary machinery — not just lines of code?

> The burden of proof is on the abstraction.

### A — Aligned

**What meaning does the abstraction preserve?**

- [ ] The URL remains a URL
- [ ] The link remains a link (`<a href>`, open in new tab, browser and server still understand it)
- [ ] HTML elements are treated like HTML elements
- [ ] DOM events are not replaced by a parallel event universe without need
- [ ] A developer who understands the Web can understand what the abstraction is doing

### N — Native

**What does the abstraction build on?**

- [ ] We start with what the browser already understands
- [ ] HTML / CSS / DOM / URLs / Web APIs are preferred when they suffice
- [ ] We are not inventing a parallel model without a required capability
- [ ] Native is the default, not the religion

### A — Additive

**What happens when you remove the abstraction?**

- [ ] Removing the layer leaves a usable platform path where applicable
- [ ] We added capability without unnecessarily replacing the platform
- [ ] The design is `platform + capability`, not `platform replacement`

> **If you remove the abstraction, what remains?**

## Quick contrast

**Less aligned** (replaces a primitive):

```html
<aura-link href="/settings">Settings</aura-link>
```

**More aligned** (enhances a primitive):

```html
<a href="/settings" data-aura-link>Settings</a>
```

The URL is still a URL. The link is still a link. The browser still understands it.

## Decision line

Platform First is not Platform Only.

The question is not:

> "Can we avoid an abstraction?"

The question is:

> **"Does this abstraction add enough value to justify another model?"**

Full argument: [essay.md](./essay.md)
