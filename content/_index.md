---
title: News
---

# About

In the Model-Driven Software Engineering (MDSE) community, the combination of techniques operating on graph-based models (e.g., Pattern Matching (PM) and Graph Transformation (GT)) and Integer Linear Programming (ILP) is a common occurrence, since ILP solvers offer a powerful approach to solve linear optimization problems and help to enforce global constraints while delivering optimal solutions.
However, designing and specifying complex optimization problems from more abstract problem descriptions can be a challenging task.
A designer must be an expert in the specific problem domain as well as the ILP optimization domain to translate the given problem into avalid ILP problem.
Typically, domain-specific ILP problem generators are hand-crafted by experts, to avoid specifying a new ILP problem by hand for each new instance of a problem domain.
Unfortunately, the task of writing ILP problem generators is an exercise, which has to be repeated for each new scenario, tool, and approach.
For this purpose, we introduce the **GIPS** (**G**raph-Based **I**LP **P**roblem **S**pecification Tool) framework that simplifies the development of ILP problem generators for graph-based optimization problems and a new Domain-Specific Language (DSL) called **GIPSL** (**G**raph-Based **I**LP **P**roblem **S**pecification **L**anguage) that integrates GT and ILP problems on an abstract level.
Our approach uses GIPSL specifications as a starting point to derive ILP problem generators for a specific application domain automatically.
First experiments show that the derived ILP problem generators can compete with hand-crafted programs developed by ILP experts.

---

**This work has been funded by the German Research Foundation (DFG) within
the Collaborative Research Center (CRC) 1053 [MAKI](https://www.maki.tu-darmstadt.de).**

---
