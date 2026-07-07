---
title: SOLID Principles
date: '2026-06-24'
lastmod: '2026-07-02'
draft: false
keywords:
- SOLID Principles
- SOLID
- SOLID Pinciples
params:
  aliases:
  - SOLID
  - SOLID Pinciples
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: No Change
    subcategories:
    - software-architecture
---

[SOLID Principles](https://en.wikipedia.org/wiki/SOLID). We **adopt** it under **[[Technique]]** in the garden.

## Summary

**Key points:** is a mnemonic for five object-oriented design principles from Robert C. Martin. Together they reduce coupling, clarify change boundaries, and keep modules testable. We **adopt** the set as baseline discipline in application code, not as a checklist to apply in one refactor. Start with **[[Single Responsibility Principle]]** and **[[Dependency Inversion Principle]]** where coupling hurts tests or vendor swaps.

## Details

### The Five Principles (Short Form)

| Principle | One-line gist |
|-----------|----------------|
| Single Responsibility | One reason to change per module |
| Open/Closed | Open for extension, closed for modification |
| Liskov Substitution | Subtypes must honor the base contract |
| Interface Segregation | Many small interfaces beat one fat interface |
| Dependency Inversion | Depend on abstractions, not concretions |

### Application Order (Practical)

1. **SRP** first: split mixed concerns so each unit has a clear job.
2. **DIP** next: introduce ports where tests or vendors force seams.
3. **OCP / LSP / ISP** when extension points, inheritance, or interface bloat show up in review.

### Common Failure Modes

- Renaming a god class without splitting responsibilities (SRP violation remains)
- Interface-per-class with no consumer need (fake DIP)
- Subclasses that weaken preconditions or strengthen postconditions (LSP violation)
- "SOLID refactor" that delays delivery without a coupling metric

### Related Garden Items

- **[[Single Responsibility Principle]]**, **[[Open-Closed Principle]]**, **[[Liskov Substitution Principle]]**, **[[Interface Segregation Principle]]**, and **[[Dependency Inversion Principle]]** for per-principle guidance
- **[[Design Pattern]]** for named solutions after structure is clear
- **[[Unit Testing]]** as a forcing function for inversion and narrow modules
