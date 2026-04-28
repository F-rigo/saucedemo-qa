# SauceDemo QA Project

Manual QA engagement on [SauceDemo](https://www.saucedemo.com) — a practice e-commerce web application intentionally designed with bugs across different user types. The goal was to simulate a real-world testing environment: exploratory testing, structured bug reporting, and defect tracking using industry-standard tools.

---

## Project overview

| | |
|---|---|
| **Application** | SauceDemo (saucedemo.com) |
| **Type** | Web — e-commerce |
| **Testing approach** | Exploratory + structured manual testing |
| **Bug tracking** | Jira (project: SauceDemo QA / key: SQ) |
| **Test documentation** | Notion workspace |
| **Total bugs found** | 40 |
| **User types tested** | 5 (standard, locked_out, problem, performance_glitch, error, visual) |

---

## What was tested

The application was tested across all available user accounts, each of which exhibits different bug behaviours. Testing covered:

- **Authentication** — login flows, locked accounts, error messages
- **Inventory page** — product display, images, titles, sorting, filtering
- **Product detail pages** — data consistency between listing and detail views
- **Cart** — add/remove functionality, state synchronisation
- **Checkout flow** — form validation, field behaviour, empty cart handling
- **Performance** — LCP, INP, and input delay using Chrome DevTools Performance Insights
- **Visual / UI** — layout consistency, responsive behaviour, component styling
- **Cross-page consistency** — price, title and image consistency across views

---

## Bug summary

| Severity | Count |
|---|---|
| Critical | 3 |
| High | 20 |
| Medium | 11 |
| Low | 6 |
| **Total** | **40** |

### Highlights

**BUG-001 — Floating point error on price total**
Checkout summary displays prices with excessive decimal places (e.g. `$103.96000000000001`). Root cause: subtotal not formatted before rendering.

**BUG-010 — Last Name field redirects input to First Name (problem_user)**
Typing in the Last Name field outputs each character to First Name instead, completely blocking checkout. Severity: Critical.

**BUG-016 — INP of 5,024ms on inventory page (performance_glitch_user)**
Interaction to Next Paint measured at 5,024ms — rated "poor" by Google's Core Web Vitals threshold of 200ms. UI feels frozen on every interaction.

**BUG-024 — Sort filter triggers unhandled JavaScript alert (error_user)**
Selecting any sort option triggers a native browser alert: *"Sorting is broken! This error has been reported to Backtrace."* Unhandled error exposed directly to the user.

**BUG-034 — Prices differ between inventory and product detail pages (visual_user)**
Products display different prices on the listing vs. the detail page (e.g. Sauce Labs Backpack: $31.79 on inventory, different on detail). Severity: Critical — legal and trust issue.

---

## Tools and techniques

| Tool / Technique | Usage |
|---|---|
| Jira | Bug tracking, severity/priority classification, sprint board |
| Notion | Test session notes, bug report documentation |
| Chrome DevTools | Performance testing (LCP, INP), network inspection, responsive viewport testing |
| Exploratory testing | Session-based, one user type per session |
| Equivalence partitioning | Applied to form field validation testing |
| Boundary value analysis | Applied to checkout form inputs |

---

## Defect lifecycle

Each bug was reported with:
- Unique ID (BUG-XXX) and Jira ticket (SQ-XX)
- Affected user type
- Steps to reproduce
- Expected vs. actual result
- Severity and priority classification
- Screenshot (where applicable)
- Root cause hypothesis (where identifiable)
- Related bugs noted (e.g. BUG-026 cascades into BUG-027)

---

## Repository structure

```
/
├── README.md               ← this file
└── (automation coming)     ← Pytest + Selenium tests to be added (Sprint 7–8)
```

Automated test scripts will be added as part of the TripleTen QA Bootcamp automation sprints (Python, Pytest, Selenium WebDriver).

---

## About

This project is part of my QA portfolio, built during the [TripleTen QA Analyst Bootcamp](https://tripleten.com). I have a background in pharmacy QA and frontend development, and I'm transitioning into software QA.

- **LinkedIn:** [linkedin.com/in/fernando-frigo](https://linkedin.com/in/fernando-frigo)
- **Jira project:** frigodev.atlassian.net (SauceDemo QA / SQ)
- **Notion workspace:** available on request
