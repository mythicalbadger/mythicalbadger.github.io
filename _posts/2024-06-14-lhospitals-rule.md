---
layout: post
title: Why Does L'Hospital's Rule Work?
date: 2024-06-14
description: Ft. the Mean Value Theorem
tags: math calculus
categories: math
tabs: true
---

## L’Hospital’s Rule

If you’ve ever taken a calculus course, you’ve probably encountered a limit like the following

$$
\lim_{x \to 0} \frac{x}{\sin x}
$$

Taking the limit directly results in an odd looking answer

$$
\lim_{x \to 0} \frac{x}{\sin x} = \frac{0}{\sin 0} = \frac 00.
$$

By this point, your calculus instructor has probably informed you about indeterminate forms as well, of which $$\frac00$$ is one. Luckily, there’s a neat little trick you can do to resolve this issue for most limits: L’Hospital’s Rule, named for Marquis de L’Hospital, who learned the results from his tutor Johann Bernoulli, and published them in 1696. This rule tells us that when an indeterminate form such as $$0/0$$ or $$\infty/\infty$$ is encountered, one can simply take the derivative of the numerator and denominator and evaluate the limit again. Using the example above

$$
\begin{align*}
\lim_{x \to 0} \frac{x}{\sin x} &= \lim_{x \to 0}\left(\frac{\frac{d}{dx} x}{\frac{d}{dx} \sin x}\right) \\
&= \lim_{x \to 0} \frac{1}{\cos x} \\
&= \frac{1}{\cos 0} \\
&= 1.
\end{align*}
$$

Formally, L’Hospital’s Rule is defined as follows

**Theorem (L’Hospital’s Rule).** *Let $$f$$ and $$g$$ be continuous on an interval containing $$a$$, and assume $$f$$ and $$g$$ are differentiable on this interval with the possible exception of the point $$a$$. If $$f(a)=g(a)=0$$ and $$g^\prime(x) \ne 0$$ for all $$x \ne a$$, then*

$$
\lim_{x \to a} \frac{f^\prime(x)}{g^\prime(x)} =L \implies \lim_{x \to a} \frac{f(x)}{g(x)}=L.
$$

This is pretty awesome, and can even be applied multiple consecutive times. But why does it even work? 

## Derivatives and the Mean Value Theorem

First, let’s recall the definition of a derivative. Given a function $$h: A \to \mathbb R$$ and a point $$c \in A$$, the derivative of $$h$$ at $$c$$ is defined as

$$
h^\prime(c) = \lim_{x \to c} \frac{h(x)-h(c)}{x-c},
$$

provided that the limit exists. If $$h^\prime$$ exists for all $$c \in A$$, we say that $$h$$ is differentiable on $$A$$. In order to analyze L’Hospital’s Rule, we also need the *Generalized Mean Value Theorem*, which states

**Theorem (Generalized Mean Value Theorem).** *If $$f$$ and $$g$$ are continuous on the closed interval $$[a,b]$$ and differentiable on the open interval $$(a,b)$$, then there exists a point $$c \in (a,b)$$ where*

$$
[f(b)-f(a)]g^\prime(c) = [g(b)-g(a)]f^\prime(c).
$$

*If $$g^\prime(c)$$ is never $$0$$ on $$(a,b)$$ then the conclusion can be stated as*

$$
\frac{f^\prime(c)}{g^\prime(c)} = \frac{f(b)-f(a)}{g(b)-g(a)}
$$

This is a bit random and comes out of nowhere, but is actually an extension of the *Mean Value Theorem*, which is a bit less complicated to understand.

**Theorem (Mean Value Theorem).** *If $$f:[a,b] \to \mathbb R$$ is continuous on $$[a,b]$$ and differentiable on $$(a,b)$$, then there exists a point $$c \in (a,b)$$ where*

$$
f^\prime(c) = \frac{f(b)-f(a)}{b-a}.
$$

The Mean Value Theorem is one of the most important results from real analysis. Simply put, it states that for any function $$f$$ continuous on the interval $$[a,b]$$, there exists some $$c \in (a,b)$$ such that the secant line joining points $$a$$ and $$b$$ is parallel to the tangent line at point $$c$$.
## Proof

Armed with this, we can prove L’Hospital’s Rule. Assuming we have two functions $$f,g$$, that the derivatives of both at $$a$$ exist, and that $$g^\prime(a)$$ is never zero, we have

$$
\begin{align*}
\lim_{x \to a} \frac{f(x)}{g(x)} &= \lim_{x \to a} \frac{f(x)-f(a)}{g(x)-g(a)} \tag{generalized MVT} \\
&= \lim_{x \to a} \frac{\frac{f(x)-f(a)}{x-a}}{\frac{g(x)-g(a)}{x-a}} \\
&= \frac{\lim_{x \to a}\frac{f(x)-f(a)}{x-a}}{\lim_{x \to a}\frac{g(x)-g(a)}{x-a}} \\
&= \frac{f^\prime(a)}{g^\prime(a)}
\end{align*}
$$