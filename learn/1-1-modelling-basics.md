# Modelling basics: from a word problem to variables, objective and constraints

*Tutorial 1.1 · level 1 of 10 · from [ProvenDecisions](https://proven-decisions.ai/?ref=github)*

## The idea

Most of the work in optimization happens before any solver runs: reading a story and turning it into a model. There are always the same four steps. Name what you decide, say what you want, list what limits you, and check the result against the story.

## The math, with a comment on each formula

**1. Decisions.** Give each quantity you control a symbol and a unit, for example $b$ = loaves of bread baked and $c$ = cakes baked per day. *In words: if you cannot say what a variable measures, it is not ready.*

**2. Objective.** Write the thing to maximise or minimise as a formula in the decisions:

$$\text{profit} = 4b + 5c .$$

*In words: every loaf earns 4 and every cake 5; the formula adds up the money.*

**3. Constraints.** One inequality per limited resource, in the same units on both sides:

$$2b + 3c \le 24 \;\;(\text{oven hours}),\qquad 3b + 2c \le 26 \;\;(\text{kg of flour}),\qquad b, c \ge 0 .$$

*In words: a loaf uses 2 oven hours and 3 kg of flour, a cake 3 oven hours and 2 kg; the oven has 24 hours and the pantry 26 kg; you cannot bake a negative amount.*

**4. Check.** Put the answer back into the story. Are all limits respected? Is a limit you did not mention (for example whole loaves only) missing from the model?

## Worked example

The story above, written in ProvenDecisions syntax:

```
maximize 4 b + 5 c
subject to
2 b + 3 c <= 24
3 b + 2 c <= 26
b, c >= 0
# b = loaves of bread per day, c = cakes per day
```

Bake 6 loaves and 4 cakes for a profit of 44 (status optimal). The picture shows the two limit lines meeting at the answer.

![figure](https://proven-decisions.ai/learn/modelling-basics-bakery.svg)

*Feasible region and optimum for bakery. Blue: constraint lines and feasible region; dashed orange: objective line through the optimum; dot: optimum.*

## Try it

A new customer wants at least 2 cakes a day, but the oven is down to 20 hours. Edit the model and solve it:

```
maximize 4 b + 5 c
subject to
2 b + 3 c <= 20
3 b + 2 c <= 26
c >= 2
b, c >= 0
# same story, tighter oven, a minimum order
```

The profit becomes 38 with 7 loaves and 2 cakes. Practise on the paint-mix and diet problems in the library (the golden problems listed above).

---

Read it on the site, with every other free tutorial and the solver: [Modelling basics: from a word problem to variables, objective and constraints](https://proven-decisions.ai/learn?t=modelling-basics&ref=github)

Text under [CC BY 4.0](../LICENSE-TEXT.md): reuse it with credit to ProvenDecisions and a link.
