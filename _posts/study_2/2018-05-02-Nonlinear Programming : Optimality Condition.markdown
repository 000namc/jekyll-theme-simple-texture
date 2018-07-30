---
layout: post
title: "Nonlinear Programming : Optimality Condition"
categories: study_2
comments: true
tags: [study, optimization]
redirect_from:
  - /2018/05/02/
---
- [2018-05-01 : 스터디 소개 : Nonlinear Programming Study](https://000namc.github.io/blog/2018/05/01/Nonlinear-Programming/)
- [2018-05-02 : Nonlinear Programming : Optimality Condition Study](https://000namc.github.io/blog/2018/05/02/Nonlinear-Programming-Optimality-Condition/) $\leftarrow$  
- [2018-05-12 : Nonlinear Programming : Gradient Methods - Convergence(작성중) Study](https://000namc.github.io/blog/2018/05/12/Nonlinear-Programming-Gradient-Methods-Convergence/)


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

{:toc .toc}

## 1 Unconstrained Optimization  
### 1.1 Optimality Condition  

- 1.1.1 Variational Ideas  
- 1.1.2 Main Optimality Conditions  

___

#### 1.1.1 Variational Ideas  
___

#### Local and Global Minima  
local minimum과 global minimum에 대하여 아래와같이 정의하도록 합니다.  

**Definition 1:** A vector $ x^* $ is **an unconstraind local minimum** of f if there exists an $ \epsilon >0 $ such that   

$$ f( x^* ) \leq f(x), \quad \forall x \in \mathbb{R}^n \;  with \; \lVert x-x^* \rVert < \epsilon  $$

**Definition 2:** A vector $ x^* $ is **an unconstraind global minimum** of f if  

$$ f( x^* ) \leq f(x), \quad \forall x \in \mathbb{R}^n  $$

**Note 3:** 위의 두 정의에서 equility가 없이 성립될 경우( for $ x \neq x^* $ ) 각각의 minimum을 **strict** 하다고 말하기로 합니다.  

**Note 4:** Local and global maximum are similarly defitned. $ -f $ 가 minimum을 갖을 때 $ f $ 가 maximum을 갖는다고 하겠습니다.  

**Note** 함수 f가 최소 최대를 갖게하는 점 x 에는 minimum, maximum  

**Note** 함수 f의 최소 최대값은 minima, maxima 라는 표현을 씁니다.  

___

#### Necessary Conditions for Optimality  

가장 기본적인 Necessary Condition에 대한 아이디어를 소개합니다. 여기에는 First order necessary condition과 Second order necessary condition 이 있고, 이 아이디어에 대한 증명은 아래 Proposition에서 보다 수학적인 표현으로 증명 할것입니다.  

**Idea 5:**  
We expect that if $ x^* $ is an unconstrained local minimum, the first order cost variation due to a small variation $\Delta x$ is nonnegative:  

$$ \nabla f( x^* )'\Delta x = \sum_{i=1}^n \frac{\partial f( x^* )}{\partial x_i} \Delta x_i \geq 0 $$  

In particular, by taking $\Delta x$ to be positive and negative multiples of the unit coordinate vectors, we obtain $\partial f( x^* ) / \partial x_i \geq 0$ and $\partial f( x^* ) / \partial x_i \leq 0$, respectively, for all coordinates $ i = 1, \dots, n $ . Equivalently, **we have the first order necessary condition**  

$$ \nabla f( x^* ) = 0.  $$  

단순한 아이디어 입니다. $\nabla f( x^* ) = 0$ 이라는 사실을 모른다는 가정하에 $ x^* $에서의 값이 주변에서의 값보다 더 작을것이기 때문에 그 점에서 생각할 수 있는 아주 작은 증가분 $ \nabla f( x^* )'\Delta x$ 이 양수일 것이라는 것이죠. 더 작아진다면 local minimum이 아닐 태니까. 이 논리를 $-\Delta x$ 방향으로도 적용하게 되면(모든 방향으로의 미분값이 같을태니) 위와같은 결론을 얻을 수 있겠습니다.

위의 식에서 ' 는 transpose를 나타내는 기호입니다.

___

위 아이디어를 2차 미분까지를 고려하여 적용해보면 아래와같은 necessary condition을 얻을 수 있습니다.  
**Idea 6:**  
We also expect that the second order cost variation due to a small variation $\Delta x $ must also be nonnegative:

$$ \nabla f( x^* )' \Delta x + \frac{1}{2!} \Delta x' \nabla^2 f( x^* ) \Delta x \geq 0. $$

Since $\nabla f( x^* )' \Delta x = 0$, **we obtain second order necesarry condition**

$$ \Delta x' \nabla^2 f( x^* ) \Delta x \geq 0, $$

which implies that

$$ \nabla^2 f( x^* ) : \text{positive semidefinite.}$$

**Note 7:**  아래의 조건을 **strengthened form of the second order necessary condition** 이라고 부르겠습니다.

$$ \Delta x' \nabla^2 f( x^* ) \Delta x > 0 $$

which implies that
$$ \nabla^2 f( x^* ) : \text{positive definite.}$$

**Note 8:** $\nabla f(x) = 0$ 을 만족하는 벡터 x를 **stationary point** 라고 부르겠습니다.

___

#### The Case of a Convex Cost Function

어떤 함수가 정의된 범위 내에서 Convex 라고 하면 local minimum과 global minimum이 같은 값을 갖게 됩니다. 게다가 위에서 얻었던 necessary condition $\nabla f(x) =0 $ 이 sufficient condition이 되겠습니다. 증명은 아래의 Proposition에서 하도록 하겠습니다.

___

#### Sufficient Conditions for Optimality

하지만 위의 경우처럼 Convexity를 보장할 수 없는경우에는 first order necessary condition이 바로 sufficient condition이 되지 않습니다. Convexity가 보장되지 않은경우에 local minimum을 갖을 sufficient condtion은 first order necessary condition과 strengthened form of the second order necessary condition을 만족하는 것입니다. 증명은 아래의 Proposition에서 하도록 하겠습니다.

**Note 9:** 연속이지 않은 함수에 대해서는 necessary condition을 만족하지 않아도 local minimum을 갖을 수 있습니다. 이러한 불연속인 점 $x$ 를 **singular point** 라고 부르겠습니다. local minimum중에 necessary condition을 만족하는 자연스러운 점은 **nonsingular point** 라고 부르겠습니다.

**Note 10:** singular point에 대해서는 sufficient condtion을 찾는 다던지, 최적해를 찾는 알고리즘을 만든다던지 모든게 어렵습니다.

___

#### Quadratic Cost Functions

Quadratic function은 아래와 같이 쓸 수 있습니다.

$$ f(x) = \frac{1}{2} x'Qx-b'x, $$

where Q is a symmetric $ n\times n$ matrix and b is a vector in $\mathbb{R}^n$

만약 $ x^* $ 함수 $f$의 local minimum이라면 아래와 같은 필요조건을 만족하게됩니다.

$$\nabla f( x^* ) = Qx^* -b = 0, \qquad \nabla^2f( x^* ) = Q : \text{positive semidefinite}$$

그러므로 만약 $Q$가 positive semidefinite가 아니라면 $f$는 local minima를 갖을 수 없습니다. 만약 Q가 positive semidefinite 라면 $f$가 convec라는것을 보일 수 있고 따라서 $f$가 local minima를 갖을 충분조건을 만족합니다($f$ is convec and satisfy the first order necessary condition).

그런즉 $Q$가 positive semidefinite일때, $\nabla f( x^* ) = Qx^* -b = 0$을 만족하는 모든 $ x^* $에서 함수 $f$가 global minima를 갖게됩니다. 하지만 이경우에는 $Q$가 역행렬을 갖지 않을 수 있고 같은말로 해를 갖지 않을 수 있습니다. 만약 $Q$가 positive definite라면 $Q$는 언제나 역행렬을 갖고, 따라서 함수 $f$는 $x^* = Q^{-1} b $ 에서 unique global minima 를 갖게 됩니다.

___

Quadratic function은 두가지 이유에서 중요합니다. 첫번째로 많은 application에서 cost function으로 자주 등장하고, 두번째로 $ x^* $에서 local minimum을 갖는 nonquadritic 함수를 충분히  잘 근사 할 수 있다는 것입니다.


$$f(x) = f( x^* )( x-x^* ) + \frac{1}{2}( x-x^* )'\nabla^2f( x^* )( x-x^* ) + o(\lVert x-x^* \rVert^2 )$$

This means that we can carry out much of our analysis and experimentation with algorithms using positive definite quadratic functions and expect that the conclusions will largely carry over to more general cost functions near convergence to such local minima.

___

#### Existence of Optimal Solutions
많은 경우에 적어도 하나의 global minimum을 보장받을 수 있는 상황을 기대합니다. 하지만 아래와같이 두가지 가능성이 있습니다.


The set $\{ f(x) : x \in X \}$ is bounded below. that is, there exists a scalar $M$ such that $M \leq f(x)$ for all $x \in X$.  
The set $\{ f(x) : x \in X \}$ is unbounded below. In this case we write

$$ \text{inf}_{ x \in X} f(x) = -\infty.$$

**Theorem 11: Weierstrass Theorem**  
Existence of at least one global minimum is guaranteed if $f$ is a continuous function and $X$ is a compact subset of $\mathbb{R^n}.$

___

#### Why do we Need Optimality Conditions?

Optimization problem을 푸는데에 있어 Optimality Condition은 정말 중요한 역할을 합니다. 보통 아래와같은 과정을 통해 문제를 풀게됩니다 :

우선, first order necessary condition을 만족하는 모든 점을 찾습니다. 그리고난 후 이 점들에 대해서 second order necessary condition이 만족하는 것들을 뽑아냅니다. 이점들중에 $\nabla^2f$가 positive definite이게 하는 점이 local minimum 이겠습니다.


___

#### Sensitivity

Sensitivity와 관해서 3.2절에서 다루도록 하겠습니다.

___

#### 1.1.2 Main Optimality Conditions
We now provide formal statements and proofs of the optimality conditions duscussed inthe preceding section.

___

**Proposition 1.1.1 : (Necessary Optimality Conditions)**  
Let $ x^* $ be an unconstrained local minimum of $ f : \mathbb{R}^n \mapsto \mathbb{R}, $ and assume that $f$ is continuously differetiable in an open set $S$ containing $ x^* $. Then

$$\nabla f( x^* ) = 0 . \qquad \text{First Order Necessary Condition}$$

if in addition $f$ is twise continuously differetiable within S, then

$$ \nabla^2 f( x^* ) : \text{positive semidefinite.} \qquad \text{Second Order Necessary Condition}  $$

___

    Proof:

Fix some $d \in \mathbb{R}$. Then, using the chain rule to differentiate the function $g(\alpha) - f(x^* +\alpha d) $ of the scalar $\alpha$, we have

$$ 0 \leq lim_{\alpha \to 0} \frac{f(x^* -\alpha d) - f( x^* )}{\alpha} = \frac{dg(0)}{d\alpha} = d'\nabla f( x^* ),$$

where the inequality follows from the assumption that $ x^* $ is a local minimum. Since d is arbitrary, the same inequality holds with d replaced by $-d$. Therefore, $d'\nabla f( x^* ) = 0$ for all $d\in \mathbb{R}^n,$ which shows that $\nabla f( x^* ) = 0.$

Assume that $f$ is twice continuously differentiable, and let $d$ be any vector in $\mathbb{R}^n$. For all $\alpha \in \mathbb{R}$, the second order Talyor series expansion yields

$$ f(x^* + \alpha d) - f( x^* ) = \alpha \nabla f( x^* )'d + \frac{\alpha^2}{2} d'\nabla^2f( x^* )d + o(\alpha^2)$$

Using the condition $\nabla f( x^* ) = 0$ and the local optimality of $ x^* $, we see that there is a sufficiently small $\epsilon>0$ such that for all $\alpha$ with $\alpha \in (0,\epsilon),$

$$ 0 \leq \frac{f(x^* + \alpha d) - f( x^* )}{\alpha^2} = \frac{1}{2}d'\nabla^2f( x^* )d + \frac{o(\alpha^2)}{\alpha^2} $$

Taking the limit as $\alpha \to 0$ and using the fact

$$ lim_{\alpha \to 0}  \frac{o(\alpha^2)}{\alpha^2} = 0,  $$

we obtain $d'\nabla^2f( x^* )d \geq 0,$ showing that $\nabla^2f( x^* )$ is positive semidefinite.

    Q.E.D.

___

**Proposition 1.1.2 : (Convex Cost Function)**  
Let $f:X \mapsto \mathbb{R}$ be a convex funtion over the convex set X.

(a) A local minimum of $f$ over $X$ is also a global minimum over $X$. If in addition $f$ is strictly convex, then there exists at most one global minimum of $f$.


(b) If $f$ is convex and the set $X$ is open, then $\nabla f( x^* )=0$ is a necessary and sufficient condition for a vector $x^* \in X$ to be a global minimum of f over $X$

___

**Proof:**

___
**Proposition 1.1.3 : (Second Order Sufficient Optimality Conditions)**  
Let $f:\mathbb{R}^n \mapsto \mathbb{R}$ be twice continuously differentiable in an open set $S$. Suppose that a vector $x^* \in S$ satisfies the conditions

$$\nabla f( x^* ) = 0, \nabla^2f( x^* ) : \text{positive definite}.$$

Then, $ x^* $ is a strit unconstrained local minimum of $f$. In particular, there exist scalar $\gamma >0 $ and $ \epsilon >0 $ such that

$$ f(x) \geq f( x^* ) + \frac{\gamma}{2} \lVert x-x^* \rVert^2, \qquad \forall x \text{ with} \lVert x-x^* \rVert < \epsilon $$

___

**Proof:**

___
