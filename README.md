# DSI Optimization
Optimization Lecture and Assignment - Galvanize Data Science Immersive (DSI)

## Step 1 - Install Pyomo and a Solver
[Pyomo](http://www.pyomo.org/) is a Python-based, open-source optimization modeling language developed at Sandia National Laboratories.

Optimization or Algebraic Modeling Languages (AMLs) allow us to formulate optimization problems in terms of our problem/business logic.  They provide a common interface to optimization solvers.  Also, they abstract away some of the complexities of formulating optimization problems (e.g. computing gradients of the objective and constraint functions with respect to the decision variables).

Pyomo is unique relative to other AMLs in that it is implemented in code.  Most AMLs (e.g. AMPL, GAMS, RASON, etc.) read in text or json files and output optimization problems.  Pyomo allows us to create optimization problems directly in Python and export, if necessary, our problem to other formats.

Pyomo supports a wide range of optimization problem types:

* Linear programming
* Quadratic programming
* Nonlinear programming
* Mixed-integer linear programming
* Mixed-integer quadratic programming
* Mixed-integer nonlinear programming
* Stochastic programming
* Generalized disjunctive programming
* Differential algebraic equations
* Bilevel programming
* Mathematical programs with equilibrium constraints

You will, however, need to find/install appropriate underlying solvers in order to actually solve these problem types. We will stick with open-source solvers today. If you ever can't find/install an appropriate solver or want to give a commercial-solver a try you may want to send your problem to the [NEOS server](https://neos-server.org/neos/).

OK, let's get back to it. Install Pyomo with the following terminal command:

```
conda install -c conda-forge pyomo
```

Enter ```y``` when prompted to proceed.

Enter ```pyomo --version``` to confirm Pyomo was installed.

Now let's install a solver. [GLPK](https://www.gnu.org/software/glpk/) or GNU Linear Programming Kit solves large-scale Linear Programming (LP) and Mixed Integer Programming (MIP) problems.

```
conda install -c conda-forge glpk
```

## Step 2 - Solve Deterministic Newsvendor

![](img/kahlua-peppermint-mocha.jpg)

Pernod Ricard needs to choose how many bottles of Kahlua Peppermint Mocha 750 ml, q, to make to minimize expected cost, 𝔼(C(q, d)), given certain demand, d = 8200, at the beginning of the holiday season.  Pernod Ricard sells Kahlua Peppermint Mocha 750 ml at price, p = 15.99, and they make Kahlua Peppermint Mocha 750 ml at cost, c = 7.99.  Bottles not sold during the holidays get marked down and eventually sell for salvage value, s = 6.99.

Run the deterministic newsvendor problem defined for you in newsvendor.py.

Try to understand the objective_deterministic, model_deterministic, and solve_deterministic methods in the Newsvendor class. 

Reference the [Pyomo Documentation](http://www.pyomo.org/documentation/).

## Step 3 - Formulate and Solve Stochastic Newsvendor

Pernod Ricard needs to choose how many bottles of Kahlua Peppermint Mocha 750 ml, q, to make to minimize expected cost, 𝔼(C(q, D)), given uncertain demand, D = [(5400, 0.1), (7800, 0.4), (8200, 0.5)], at the beginning of the holiday season.  Pernod Ricard sells Kahlua Peppermint Mocha 750 ml at price, p = 15.99, and they make Kahlua Peppermint Mocha 750 ml at cost, c = 7.99.  Bottles not sold during the holidays get marked down and eventually sell for salvage value, s = 6.99.

Note: D = [(5400, 0.1), (7800, 0.4), (8200, 0.5)] represents (demand, probability) pairs. We could generate these pairs from a continuous or discrete distribution or any other applicable method so long as the sum of the probabilities (weights) equals 1.   

Finish implementing the objective_stochastic, model_stochastic, and solve_stochastic methods in the Newsvendor class.  Run the stochastic newsvendor problem.

## Step 4 - Generalize Stochastic Newsvendor (Extra Credit)

We may wish to consider many (demand, probability) pairs. Generalize your stochastic newsvendor problem so it can handle an arbitrary number of (demand, probability) pairs. You will need to use Pyomo's built in summation notation rather than a for loop, since Pyomo requires expressions it can take the derivative of. 



