# Linear programs: the feasible region and the corner solution

*Tutorial 2.1 · level 2 of 10 · from [ProvenDecisions](https://proven-decisions.ai/?ref=github)*

## The idea

With two decisions you can draw a linear program. Each constraint cuts the plane with a straight line and keeps one side; what is left is the *feasible region*, a polygon. The objective is also a line, and sliding it across the polygon shows the best point. It is always found at a corner, which is why solvers can search corners only.

## The math, with a comment on each formula

A linear program in two variables:

$$\max\; c_1 x + c_2 y \quad\text{subject to}\quad a_{i1} x + a_{i2} y \le b_i \;\; (i=1,\dots,m),\; x,y \ge 0 .$$

*In words: each line $a_{i1}x + a_{i2}y = b_i$ is the edge of one allowed half-plane.*

The objective has the same value everywhere on a line $c_1 x + c_2 y = z$. Increasing $z$ slides this line in the direction $(c_1, c_2)$. The best $z$ is the last one at which the line still touches the polygon. *In words: the line leaves the polygon at a corner, or along a whole edge if it is parallel to that edge, and a corner of that edge is then also optimal.*

So it is enough to check the corners (the *vertices*), where two constraint lines meet. The simplex method walks from corner to corner, improving each time.

## Worked example

Maximise $5x + 4y$ with $6x + 4y \le 24$ and $x + 2y \le 6$. The kernel solved it:

```
maximize 5 x + 4 y
subject to
6 x + 4 y <= 24
x + 2 y <= 6
x, y >= 0
# x, y = units of two products
```

The optimum is $x = 3$, $y = 1.5$ with value 21 (status optimal).

![figure](https://proven-decisions.ai/learn/lp-geometry-lp.svg)

*Feasible region and optimum for lp. Blue: constraint lines and feasible region; dashed orange: objective line through the optimum; dot: optimum.*

The dashed line is the objective through the optimum; the whole polygon lies on one side of it. A minimisation works the same way: for “minimise $x + 2y$ with $x + y \ge 1$, $2x + y \ge 2$, $x,y\ge 0$” the kernel finds the corner $(1, 0)$ with value 1.

## Try it

Tilt the objective to $x + 3y$ and look at the picture again:

```
maximize x + 3 y
subject to
6 x + 4 y <= 24
x + 2 y <= 6
x, y >= 0
# same region, a new objective
```

The best corner moves to $(0, 3)$ and the value is 9. The region did not change; only the direction in which the objective line slides did.

![figure](https://proven-decisions.ai/learn/lp-geometry-tilt.svg)

*Feasible region and optimum for tilt. Blue: constraint lines and feasible region; dashed orange: objective line through the optimum; dot: optimum.*

---

Read it on the site, with every other free tutorial and the solver: [Linear programs: the feasible region and the corner solution](https://proven-decisions.ai/learn?t=lp-geometry&ref=github)

Text under [CC BY 4.0](../LICENSE-TEXT.md): reuse it with credit to ProvenDecisions and a link.
