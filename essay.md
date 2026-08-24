# MAGA: Build on the Web, Don't Rebuild It

Canonical essay for [Aura UI / MAGA](https://github.com/aura-ui/MAGA).

Short manifesto: [README](./README.md) | Practical checklist: [checklist.md](./checklist.md)

---

When I started building Aura Router, I thought I was solving a routing problem.

I wasn't.

I had an HTML and Web Components application that needed client-side navigation.

I didn't want to rewrite it in React just to get SPA routing.

I didn't want to introduce another component model.

So I built a router around the platform I was already using:

**HTML. Web Components. DOM. URLs. Browser navigation. JavaScript.**

That became [Aura Router](https://github.com/aura-ui/router).

I wrote about that journey in [Why I Built an SPA Router for HTML and Web Components](https://dev.to/aura-ui/why-i-built-an-spa-router-for-html-and-web-components-25dm).

But building the router exposed a bigger question:

> **Why do we keep rebuilding parts of the Web Platform inside frameworks?**

And then an even bigger one:

> **What would frontend development look like if the browser remained the foundation instead of becoming an implementation detail?**

That question led to three ideas:

**MAGA — Make the Web Great Again.**

**Platform First.**

And, most importantly:

**MANA — Minimal. Aligned. Native. Additive.**

Think of them as three levels of the same idea:

> **MAGA is the vision.**  
> **Platform First is the architecture.**  
> **MANA is the discipline — and the part you can actually apply.**

## MAGA: Make the Web Great Again

Yes, the acronym is deliberately provocative.

And yes, it's a joke.

The idea behind it isn't.

> **Make the Web Great Again.**

Not by going back. By recognizing how capable the Web has become.

Frameworks helped us build the modern Web. They solved real problems and created enormous ecosystems.

But the platform changed too.

HTML, CSS, the DOM, Web Components, JavaScript modules, and browser APIs have all grown substantially.

So maybe it's time to ask:

> **What if the browser is already good enough to be the platform?**

Not nostalgia. Not anti-framework ideology.

Simply:

> **Less framework. More platform.**

## The Web is already a platform

The browser is not a primitive runtime waiting for a framework to make it useful.

**It is already a platform.**

It gives us:

- HTML for structure and semantics
- CSS for layout, styling, animation, and responsive behavior
- the DOM for document structure and events
- Custom Elements and Shadow DOM
- templates and slots
- JavaScript modules
- URLs and browser navigation
- Fetch and other Web APIs
- observers, workers, and many other platform capabilities

And the platform keeps evolving.

So the question is no longer simply:

> "Which framework should we use?"

Sometimes the better question is:

> **"Does the platform already solve this?"**

## The problem isn't frameworks

I am not arguing against React, Vue, Svelte, or Angular.

Frameworks are useful. They solve real problems and have created enormously productive ecosystems.

The problem is not that abstractions exist.

The problem is that abstractions have costs.

Every abstraction can introduce another API, mental model, runtime layer, state representation, lifecycle, convention, migration path, and compatibility surface.

Sometimes that cost is absolutely worth paying.

Sometimes it isn't.

The question is:

> **Do we need a second model?**

That is where MANA begins.

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

### M — Minimal

**How much abstraction do we actually need?**

Use the smallest abstraction that solves the problem.

Start with one question:

> **Does the platform already solve this?**

If yes, don't create another system simply because a framework normally does.

If no, an abstraction may be justified.

Minimal does not mean writing the fewest lines of code.

It means minimizing unnecessary machinery.

> **The burden of proof is on the abstraction.**

### A — Aligned

**What meaning does the abstraction preserve?**

Preserve the platform's semantics and contracts.

Consider:

```html
<a href="/settings">Settings</a>
```

A router can enhance this link.

But the URL should remain a URL.

The link should remain a link.

The browser should still understand it.

The server should still understand it.

The user should still be able to open it in a new tab.

The abstraction improves the experience without changing the underlying meaning.

**That is alignment.**

> **A developer who understands the Web should be able to understand what the abstraction is doing.**

### N — Native

**What does the abstraction build on?**

Prefer native platform primitives as the underlying substrate.

Native does not mean "native is always better."

It means:

> **Start with what the browser already understands.**

HTML before a component abstraction when HTML is enough.

CSS before a styling runtime when CSS is enough.

DOM before another rendering model when the alternative provides no required capability.

URLs before a framework-specific navigation model.

Web APIs before recreating the same capability inside a framework.

> **Native is the default, not the religion.**

### A — Additive

**What happens when you remove the abstraction?**

Add capability without unnecessarily replacing the platform underneath it.

This is where the Removal Test becomes useful:

> **If you remove the abstraction, what remains?**

Consider:

```html
<a href="/account">Account</a>
```

With a router, it can become client-side navigation.

Without the router, it is still a valid link.

The application gained an enhancement without losing the Web.

Not every system needs to be fully reversible.

The useful distinction is simple:

```text
platform + capability
```

versus:

```text
platform replacement
```

## MANA in practice

When evaluating an abstraction, ask four questions:

- **Minimal** — Does the browser already solve this?
- **Aligned** — Does the API preserve native semantics?
- **Native** — Is it built on browser primitives?
- **Additive** — What still works if we remove it?

If the answers are unclear, that's a reason to look more closely at the abstraction.

### A simple example

Suppose we want to enhance navigation.

**Less aligned:**

```html
<aura-link href="/settings">Settings</aura-link>
```

Now the application has another element, another API, and another mental model.

**More aligned:**

```html
<a href="/settings" data-aura-link>Settings</a>
```

The router can enhance the existing link.

The URL is still a URL.

The link is still a link.

The browser still understands it.

That's the difference between replacing a platform primitive and adding capability around it.

## Platform First is not Platform Only

Platform First does not mean "never abstract."

Sometimes the platform is too low-level.

Sometimes a library is the better engineering choice.

Sometimes a thin wrapper provides much better developer experience.

That's fine.

The question is not:

> "Can we avoid an abstraction?"

The question is:

> **"Does this abstraction add enough value to justify another model?"**

MANA is a decision-making discipline, not a purity test.

## The Removal Test: Aura Router

This is where MANA becomes more than a philosophy.

A conventional SPA router can become the owner of application navigation:

```text
Router
 ├── route definitions
 ├── navigation state
 ├── URL handling
 ├── rendering lifecycle
 └── application navigation
```

Aura Router takes a different approach.

The browser still owns the underlying primitives:

```text
URL
<a>
history
navigation
DOM
```

Aura adds client-side behavior around them.

In practical terms, a server-rendered HTML response can remain the foundation. A normal link remains a normal link; the router enhances navigation when JavaScript is available.

The important part is what Aura does **not** require:

- route configuration does not replace the URL
- `<a href>` does not become `onClick` or a framework-specific `to=`
- without JavaScript, navigation can still fall back to the server

The router adds client-side behavior around the browser's existing model.

That is the boundary MANA is trying to define:

> **Add capability without making the platform disappear.**

This does not mean every router should work this way.

It means the browser's existing navigation model is worth treating as an architectural asset rather than something a framework has to replace.

## The platform is bigger than any component model

Web Components are important to Aura because they are already part of the Web Platform.

They are not an Aura invention, and they are not a framework that needs to sit between the application and the browser.

Web Components are built from standardized browser technologies such as Custom Elements, Shadow DOM, and HTML templates and slots.

That makes them a particularly good fit for Platform First.

But the principle is bigger than Web Components.

Tomorrow's platform may give us better primitives for components, rendering, navigation, state, or composition.

MANA doesn't need to predict which primitive wins.

It only asks us to start there.

> **Use the platform that exists. Add what is missing. Don't unnecessarily replace what already works.**

## Frameworks will change. The platform is the continuity layer.

Frontend technology changes quickly.

Frameworks rise and fall. Rendering models, build tools, state-management patterns, and component models change with them.

The Web Platform evolves differently, while maintaining a strong compatibility model across decades of the Web.

A URL is not a React primitive.

HTTP is not a Vue primitive.

CSS is not a Svelte primitive.

The DOM is not an Angular primitive.

> **Frameworks are products. The Web is a platform.**

That is why Platform First is not about choosing today's technology.

It is about building on the layer most likely to still matter when today's technology is gone.

## The experiment continues

I don't know the final answer.

And I don't think we should pretend we do.

MANA needs to be tested against real applications. It needs to encounter problems where the platform genuinely isn't enough, and discover where abstractions are justified.

Try to break the assumptions.

Tell me where the platform isn't enough.
Tell me where an abstraction is clearly justified.
Tell me where Aura's APIs are fighting the browser instead of working with it.

And if you see a better way, build it.

If you want to see the idea in code, try [Aura Router](https://github.com/aura-ui/router) and see whether its approach holds up in a real application.

Maybe the next generation of frontend shouldn't be about choosing the next framework.

Maybe it should be about deciding which parts of the Web Platform we actually need to abstract — and which we should leave intact.

> **MAGA is the vision.**  
> **Platform First is the architecture.**  
> **MANA is the discipline.**
>
> **Build on the Web. Don't rebuild it.**
