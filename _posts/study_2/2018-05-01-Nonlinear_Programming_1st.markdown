---
layout: post
title: "1st_Nonlinear_Programming(작성중)"
categories: study_2
tags: [study, optimization]
redirect_from:
  - /2018/05/01/
---


# Nonlinear Programming(2018.05.01)

1장의 목차는 아래와 같습니다. 이중에 1.1 Optimality Condition에 대해 정리하려고 합니다.

**1. Unconstrained Optimization**
**1.1 Optimality Condition**
1.2 Gradient Methods - Convergence
1.3 Gradient Methods - Rate of Convergence
1.4 Newton's Method and Variations
1.5 Least Squares Problems
1.6 Conjugate Direction Methods
1.7 Quasi-Newton Methods
1.8 Nonderivative Methods
1.9 Discrete-Time Optimal Control
1.10 Some Practical Guidelines
1.11 Notes and Sources


## 1 Unconstrained Optimization
### 1.1 Optimality Condition

- Variational Ideas
- Main Optimality Conditions

___
#### Variational Ideas
___
#### Local and Global Minima
local minimum과 global minimum에 대하여 아래와같이 정의하도록 합니다.

**Definition 1:** A vector $x^*$ is an unconstraind local minimum of f if there exists an $\epsilon >0$ such that
$$ f(x^*) \leq f(x), \quad \forall x \in \mathbb{R}^n \;  with \; \lVert x-x^* \rVert < \epsilon  $$

**Definition 2:** A vector $x^*$ is an unconstraind global minimum of f if
$$ f(x^*) \leq f(x), \quad \forall x \in \mathbb{R}^n \;   $$

** Note 3: ** 위의 두 정의에서 equility가 없이 성립될 경우(for $x \neq x^*$) 각각의 minimum을 strict 하다고 말하기로 합니다.

** Note 4: ** Local and global maximum are similarly defitned. -f 가 minimum을 갖을 때 f 가 maximum을 갖는다고 하겠습니다.

___
#### Necessary Conditions for Optimality

가장 기본적인 Necessary Condition에 대한 아이디어를 소개합니다. 이 아이디어에 대한 증명은 아래 Proposition에서 보다 수학적인 표현으로 증명 할것입니다.

** Idea 5: **
We expect that if $x^*$ is an unconstrained local minimum, the first order cost variation due to a small variation $\Delta x$ is nonnegative:

$$ \nabla f(x^*)'\Delta x = \sum_{i=1}^n \frac{\partial f(x^*)}{\partial x_i} \Delta x_i \geq 0 $$
In particular, by taking $\Delta x$ to be positive and negative multiples of the unit coordinate vectors, we obtain $\partial f(x^*) / \partial x_i \geq 0$ and $\partial f(x^*) / \partial x_i \leq 0$, respectively, for all coordinates $ i = 1, \dots, n $ . Equivalently, we have the necessary condition
$$ \nabla f(x^*) = 0.  $$

단순한 아이디어 입니다. $\nabla f(x^*) = 0$ 이라는 사실을 모른다는 가정하에 $x^*$에서의 값이 주변에서의 값보다 더 작을것이기 때문에 그 점에서 생각할 수 있는 아주 작은 증가분 $ \nabla f(x^*)'\Delta x$ 이 양수일 것이라는 것이죠. 더 작아진다면 local minimum이 아닐 태니까. 이 논리를 $-\Delta x$ 방향으로도 적용하게 되면(모든 방향으로의 미분값이 같을태니) 위와같은 결론을 얻을 수 있겠습니다.

위의 식에서 ' 는 transpose를 나타내는 기호입니다.
___
위 아이디어를 2차 미분까지를 고려하여 적용해보면 아래와같은 necessary condition을 얻을 수 있습니다.
** Idea 6: **
We also expect that the second order cost variation due to a small variation $\Delta x $ must also be nonnegative:
$$ \nabla f(x^*)' \Delta x + \frac{1}{2!} \Delta x' \nabla^2 f(x^*) \Delta x \geq 0. $$

Since $\nabla f(x^*)' \Delta x = 0$, we obtain
$$ \Delta x' \nabla^2 f(x^*) \Delta x \geq 0, $$

which implies that
$$ \nabla^2 f(x^*) : \text{positive semidefinite.}$$

** Note 7: ** $\nabla f(x) = 0$ 을 만족하는 벡터 x를 stationary point라고 부르겠습니다.
___
#### The Case of a Convex Cost Function

어떤 함수가 정의된 범위 내에서 Convex 라고 하면 local minimum과 global minimum이 같은 값을 갖게 됩니다. 게다가 위에서 얻었던 necessary condition $\nabla f(x) =0 $이 sunfficient condition이 되겠습니다. 증명은 아래의 Proposition에서 하도록 하겠습니다.
___
#### Sufficient Conditions for Optimality
