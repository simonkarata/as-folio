---
title: Simulation and Modelling
description: How mathematical models and computational experiments help us understand complex systems, test ideas, and reason about possible futures.
date: 2026-11-07
author: simon
draft: false
tags:
  - simulation
  - modelling
  - computational science
  - systems thinking
categories:
  - science
  - computing
toc: true
relatedPosts: true
---

Many systems that matter to us are difficult to study directly. A city cannot be rebuilt just to test a new transport plan, and a medical treatment cannot be tried on every possible patient before it is used. Simulation offers a way to explore such systems by building a model, specifying how it changes, and running experiments in a controlled computational environment.

A model is a purposeful representation of a real or imagined system. It keeps details that matter for a question and simplifies others. A simulation is the process of using that model to calculate how the represented system might behave under particular conditions. Together, modelling and simulation connect theory with experimentation: they help make assumptions explicit, compare alternatives, and investigate outcomes that may be hard, expensive, or unsafe to observe in the real world.

## From a real system to a model

The first step is not choosing software or writing code. It is deciding what question the model should answer. A model designed to estimate the spread of a disease, for example, will need different details from one designed to plan hospital staffing. The purpose determines the system boundary, the variables to represent, and the level of detail that is useful.

Modellers then describe the system's important components and relationships. A model of a room's temperature might track heat entering through sunlight, heat lost through walls, and energy supplied by heating equipment. A model of traffic might represent vehicles, roads, intersections, and driver choices. In both cases, the model leaves out much of reality. That is not automatically a weakness: unnecessary detail can make a model harder to understand and validate without improving its usefulness.

The representation can take several forms. Equations describe relationships between quantities; algorithms specify step-by-step rules; diagrams show structures and flows; and data-driven models estimate patterns from observations. Some models combine these approaches, such as a physical model whose parameters are estimated from measured data.

## Different kinds of simulation

The choice of simulation method depends on the system and the question:

- **Continuous simulation** represents quantities that change over time, such as temperature, fluid pressure, or the concentration of a chemical.
- **Discrete-event simulation** focuses on events that occur at particular times. It is useful for queues, manufacturing lines, service systems, and logistics.
- **Agent-based simulation** represents individual entities—such as people, vehicles, or animals—and the rules governing how they interact. Collective behaviour can emerge from those local interactions.
- **System dynamics** describes how quantities accumulate and influence one another through feedback loops. It is often used to explore high-level behaviour in organisations, economies, and environmental systems.
- **Stochastic simulation** includes randomness to represent variability or incomplete knowledge, such as uncertain arrival times or random changes in a population.

These categories are not mutually exclusive. A model of a hospital could combine discrete events for patient flow, agents for individual patients and staff, and random variation in treatment times. The most useful method is not necessarily the most complicated one; it is the simplest one that can answer the question with adequate credibility.

## The modelling workflow

Although projects differ, a reliable workflow usually includes several linked activities.

### 1. Define the question and assumptions

State what the model is intended to explain, compare, or predict. Specify the boundary of the system, the time period, and the decisions the results might inform. Record assumptions early. They are part of the model, not incidental implementation details.

### 2. Formulate and implement the model

Translate the system description into equations, rules, or computational procedures. Choose an appropriate time step, event structure, and level of detail. Keep the implementation traceable to the conceptual model so that another person can understand why each important rule is present.

### 3. Verify the implementation

Verification asks whether the model has been implemented as intended. Useful checks include comparing calculations with hand-worked examples, testing boundary cases, checking units, and confirming that quantities obey known constraints. For a simulation that tracks a fixed population, for instance, the population should not silently increase unless the model includes births, arrivals, or another valid source.

### 4. Validate against evidence

Validation asks whether the model is an adequate representation for its intended use. Results can be compared with observations, established measurements, or expert understanding. Agreement with historical data is useful, but it does not prove that the model will work under new conditions. Validation is therefore tied to a specific purpose and range of use rather than being a permanent certificate of truth.

### 5. Explore uncertainty

Inputs and assumptions are rarely known with perfect accuracy. Sensitivity analysis varies important parameters to see which ones have the greatest effect on the results. When randomness is part of the model, repeated runs can show the range of possible outcomes rather than a single result. Reporting that range is often more informative than presenting one precise-looking number.

### 6. Communicate and revise

Explain the model's purpose, assumptions, evidence, and limitations alongside its results. Visualizations can help people explore patterns, but should not obscure uncertainty or imply greater precision than the model supports. Feedback from subject-matter experts and affected communities may reveal missing mechanisms or inappropriate assumptions, prompting another iteration.

## Where simulation is useful

Simulation is used across disciplines because it provides a structured way to reason about systems:

- **Engineering and manufacturing:** Test designs, operating conditions, and production processes before committing to costly physical changes.
- **Healthcare:** Study patient flow, support treatment planning, and explore physiological processes. Clinical decisions still require evidence and professional judgment beyond a simulation.
- **Climate and environmental science:** Examine interactions among atmosphere, oceans, land, and human activity, and compare scenarios over long time horizons.
- **Transport and urban planning:** Evaluate how changes to routes, schedules, infrastructure, or travel behaviour may affect a wider network.
- **Training and education:** Give learners a safe environment to practise procedures, operate equipment, or explore scientific ideas.
- **Digital twins:** Connect a model of an asset or process with data from its real-world counterpart, allowing teams to monitor conditions and investigate possible interventions.

In each case, simulation is most valuable when it supports a clear decision or investigation. It can reveal consequences that are difficult to see by inspecting a complex system alone, and it can help identify which questions deserve real-world experiments.

## What models cannot tell us

A simulation does not remove uncertainty; it organizes and exposes it. Results depend on the structure of the model, the quality of its input data, and the assumptions used to simplify the system. If an important mechanism is missing, a detailed simulation can still produce misleading answers. A model that matches one set of observations may also fail when applied to a different population, location, or time period.

There are ethical considerations as well. Models can influence decisions about health, resources, infrastructure, and public policy. Data may be incomplete or biased, and an optimization objective may prioritize one outcome while overlooking others. People affected by a decision should not be treated as invisible parameters. Transparent assumptions, appropriate review, and careful communication are essential when model outputs may shape real lives.

## A disciplined way to explore possibilities

The strongest simulation projects combine technical implementation with critical reasoning. They begin with a question, make assumptions visible, check the code, compare results with evidence, and test how conclusions change when inputs or conditions change. Their results are not predictions handed down by a computer, but conditional statements: given this representation and these assumptions, these outcomes are plausible.

Used in that way, simulation and modelling are not substitutes for observation or expertise. They are tools for asking better questions, making complex systems easier to examine, and learning where our understanding remains uncertain.
