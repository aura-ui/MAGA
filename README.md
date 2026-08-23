# MAGA
Make the Web Greate Again
> ⚠️ **Note on terminology:** «MAGA» here is used purely as a playful acronym for «Make the Web Great Again» within the Aura community. It refers exclusively to returning to web platform primitives (HTML, CSS, Web APIs) and carries no political connotation.

Let's get the joke out of the way. Yes, MAGA is intentionally playful. The idea behind it is serious:

> **Less framework. More platform.**

This is not an argument against React, Vue, Angular, Svelte, or any other framework. Frameworks are useful. They solve real problems and have created productive ecosystems.

The question is not whether frameworks are good or bad. The question is:

> **How much framework do we actually need?**

Over the years, frontend development has accumulated layer after layer of abstraction:

- component systems on top of the browser's component system
- event systems on top of DOM events
- routing systems on top of URLs and History
- state systems for state that sometimes already exists in the DOM
- rendering abstractions on top of HTML
- styling abstractions on top of CSS
- framework-specific APIs around browser APIs

None of these are necessarily bad. The problem appears when the abstraction becomes more important than the platform underneath it — when we stop building applications for the Web and start building them for a particular framework ecosystem.

Aura explores the opposite direction:

> **What if the Web Platform remained the foundation?**

## The Web Platform is already a platform

This may sound obvious, but it is worth stating explicitly.

The browser is not a primitive runtime waiting for a framework to make it useful. Modern browsers already provide an enormous set of primitives:

HTML for structure and semantics. CSS for layout, styling, animations, custom properties, and container queries. The DOM for the document tree and event model. Custom Elements for a native component model. Shadow DOM for encapsulation. Templates for reusable markup. ES Modules for a native module system. The URL and History APIs for navigation. Fetch for HTTP. Observers for reacting to document and viewport changes. Workers for background execution.

And the platform keeps evolving.

So perhaps the right question isn't always "Which framework should we use?" Sometimes the better question is:

> **Does the platform already solve this?**
## MANA

MAGA is the slogan. MANA is the decision rule:

**MANA — Minimize. Adhere. Native-first. Augment.**

> Minimize unnecessary abstractions.  
> Adhere to Web Platform contracts.  
> Build on a native-first substrate.  
> Augment the platform, never replace it.

The burden of proof is on the abstraction.

> **Minimize decides whether. Augment decides how.**  
> **Adhere decides which contracts. Native-first decides which substrate.**

### M — Minimize

**Meaning:** add a layer only if the platform cannot solve the problem.

**Question:** Is this layer necessary?

Every extra API costs learning, maintenance, and migration. Minimize does not ban abstractions — it bans *unnecessary* ones. If the platform falls short, a layer *may* be justified. What that layer is allowed to look like is Augment's job.

### A — Adhere

**Meaning:** follow existing Web contracts; don't invent parallel ones.

**Question:** Would a platform-literate developer recognize this?

Use HTML semantics, DOM events, URL meaning, and Custom Elements as they are. The goal is familiarity: *"I understand what the browser is doing here."*

### N — Native-first

**Meaning:** browser primitives are the foundation — HTML, CSS, DOM, Custom Elements, Shadow DOM, History, standard Web APIs.

**Question:** What does the browser already understand here?

Aura Router is the example: a route can be a Custom Element; a link stays an ordinary `<a href>`. The server still returns HTML. JavaScript enhances navigation instead of owning it. Without JS, the link still works.

### A — Augment

**Meaning:** when a layer is justified, keep it thin — enhance the platform, never replace it.

**Question:** Does the browser still participate?

Without Augment, Minimize could excuse a private runtime as long as someone called it "necessary." Augment forbids that: the browser remains a participant, not a backend for a framework-shaped platform.

## Platform First

There is one more term:

**Platform First**

MAGA is the vision. MANA is the set of principles. Platform First is the architectural approach:

> **Start with the Web Platform. Add an abstraction only when the platform doesn't provide what you need.**

That changes the order of decisions. The traditional approach often looks like this:

```text
Framework
↓
Framework abstractions
↓
Application
↓
Browser
```

The Platform First approach looks more like:

```text
Web Platform
↓
Thin, framework-independent abstractions
↓
Application
```

That doesn't mean applications have to be tiny. It doesn't mean complex applications don't need abstractions. It means the browser remains visible underneath them.

## This is not "vanilla JavaScript"

MANA does not mean "never use a library," "write everything yourself," or "real developers only use vanilla JavaScript." That would simply replace one dogma with another.

If a library provides something the platform doesn't, use it. If a framework gives your team a genuine advantage, use it. If an abstraction makes a difficult problem significantly easier, keep it.

But don't introduce a framework-specific abstraction simply because that's how the framework expects the problem to be solved.

> **Platform first. Abstraction when justified.**

Not:

> **Platform at all costs.**

## From framework zoo to a common platform

Frontend applications accumulate technologies easily. A project starts with one framework. Then another library appears because the framework doesn't solve a particular problem. Then a router. Then a state manager. Then a component library. Then wrappers around Web Components. Then another build-time abstraction. Then another runtime abstraction.

None of those decisions are necessarily wrong. The problem is the accumulated result: a stack where every layer assumes the layer below it, until the application depends on the ecosystem more than on the Web.

Aura explores the opposite direction. Instead of asking which framework everything should depend on, we can ask:

> What can we build that depends primarily on the Web?

That creates a different kind of interoperability. A Web Component doesn't need to know whether its consumer uses React, Vue, Angular, Svelte, another Web Component library, or no framework at all. The browser becomes the integration layer.

## Aura Router was the first experiment

This is why Aura Router matters beyond routing. It was the first practical test of Platform First:

- Could an SPA router exist without a second component model?
- Could it preserve ordinary HTML links?
- Could the server remain responsible for the initial response?
- Could JavaScript enhance navigation without owning the application's fundamental structure?
- Could Web Components stay mounted while only a child route changes?

The answer turned out to be yes.

Aura Router can reuse HTML already present on the page, handle marked links for client-side navigation, and leave ordinary links to the browser. It also supports nested layouts where shared Web Components remain mounted while child content changes.

That doesn't mean the router is finished. It means the experiment worked well enough to justify exploring the larger idea.

## MANA is now an official Aura principle

These ideas are no longer just notes from building a router. They are how Aura makes design decisions:

| Letter | Decides | Ask |
| --- | --- | --- |
| **M** Minimize | **whether** a layer is needed | Is this layer necessary? |
| **A** Adhere | **which contracts** to follow | Would a platform-literate developer recognize this? |
| **N** Native-first | **which substrate** to build on | What does the browser already understand here? |
| **A** Augment | **how** a justified layer may behave | Does the browser still participate? |

**MANA — Minimize. Adhere. Native-first. Augment.**

> Minimize unnecessary abstractions.  
> Adhere to Web Platform contracts.  
> Build on a native-first substrate.  
> Augment the platform, never replace it.

The burden of proof is on the abstraction.

## What MANA does not mean

MANA is not a purity test.

A project doesn't become "more Aura" because it has fewer dependencies. A native API isn't automatically better just because it is native. A framework abstraction isn't automatically bad because it is a framework abstraction.

Sometimes the browser API is too low-level. Sometimes a library provides enormous value. Sometimes an abstraction is exactly what a project needs.

MANA is about where we start, not about what we are forbidden to use. The starting point is the platform. The burden of proof is on the abstraction.

## Why now?

The Web Platform has changed enormously. Custom Elements, Shadow DOM, and ES Modules are standardized. CSS is dramatically more capable than a decade ago. Browser APIs continue to expand.

At the same time, frontend development has accumulated an enormous amount of abstraction.

Maybe the question shouldn't be "Which framework is the future?" Maybe there is another question worth asking:

> **How much framework do we actually need?**

That's the question behind Aura.
