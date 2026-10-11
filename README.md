# Composing P.G.F.s

An animated, step-by-step walkthrough of one derivation from Section 2 of the Open University module M343, *The size of the nth generation*: how the probability generating function of a sum with a random number of terms comes out as one p.g.f. inside another.

$$\Pi_Z(s) = \Pi_N\bigl(\Pi_X(s)\bigr)$$

**Live page:** https://nihilisticiconoclast.github.io/composing-pgfs/

## The set-up

$`N`$ is a random count. Each of the $`N`$ items independently contributes an amount distributed like $`X`$, and $`Z`$ is the total. The $`X_i`$ are independent of each other and of $`N`$.

$$Z = X_1 + X_2 + \cdots + X_N$$

In a branching process this is how one generation becomes the next: $`N`$ is the size of generation $`n`$ and $`Z`$ is the size of generation $`n+1`$.

## What's on the page

Each section pairs an equation from the text with a figure you can play.

- **The set-up.** A needle draws $`N`$ from a ruler split by $`P(N = n)`$. Each parent then has 0, 1 or 2 children, which are counted into $`Z`$.
- **Step 1, Theorem of Total Probability.** A unit square is split into strips, one per value of $`N`$, each stacked with the distribution of $`Z`$ given that value. The blocks for the tracked value of $`Z`$ slide onto a ruler and add up to $`P(Z = z)`$, with a ledger of the products alongside.
- **Step 2, equation (2.9).** The joint table of $`P(N = n,\ Z = z)`$, added down its columns or factored along its rows, showing why the order of summation can be swapped and why $`P(N = n)`$ comes outside the inner sum.
- **Step 3, Result (2.8).** The distribution of $`Z`$ given $`N = n`$ for $`n = 0, 1, 2, 3`$, next to the expansion of $`\bigl(\Pi_X(s)\bigr)^n`$, including the empty sum at $`n = 0`$.
- **Step 4, equation (2.10).** Every $`s`$ in $`\Pi_N(s)`$ is swapped for $`\Pi_X(s)`$. A slider checks that $`\Pi_N\bigl(\Pi_X(s)\bigr)`$ always equals $`\sum_z P(Z = z)\,s^z`$.
- **Check.** Thousands of simulated families against the coefficients of $`\Pi_N\bigl(\Pi_X(s)\bigr)`$, with the sample mean and variance against the formulas.
- **Why it matters.** Composing once per generation gives the size distribution of each generation of a branching process, and the chance of extinction by generation $`n`$, for offspring means 0.8, 1 and 1.2.

## The example

Every figure uses the same small example, and every number on the page is computed from it.

| $`n`$ | 0 | 1 | 2 | 3 |
|---|---|---|---|---|
| $`P(N = n)`$ | 0.1 | 0.3 | 0.4 | 0.2 |

| $`x`$ | 0 | 1 | 2 |
|---|---|---|---|
| $`P(X = x)`$ | 0.25 | 0.5 | 0.25 |

So $`\Pi_X(s) = \tfrac14(1+s)^2`$, $`E(Z) = E(N)\,E(X) = 1.7`$ and $`\operatorname{Var}(Z) = 1.66`$.

## How it's built

- One self-contained `index.html`, with no build step and nothing to install.
- Each distribution is stored as the coefficient list of its p.g.f. Convolution gives sums of independent variables and polynomial composition gives $`\Pi_N\bigl(\Pi_X(s)\bigr)`$, so none of the probabilities on the page are typed in by hand.
- Maths is typeset with MathJax 3 (SVG output) from jsDelivr, and the fonts come from Google Fonts.
- The page follows the reader's light or dark setting and respects reduced-motion preferences.

## Run it locally

Open `index.html` in a browser, or serve the folder:

```sh
python3 -m http.server
```

Then visit http://localhost:8000. MathJax and the fonts load from CDNs, so you need to be online.

## Note

An unofficial study aid, not produced by or affiliated with the Open University. Equation and result numbers refer to Section 2 of the M343 module text; the example distributions are made up for illustration.
