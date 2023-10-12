---
title: Op methods problem bank
date: '2022-10-27T00:00:00Z'
draft: true
---




**Exercise:** Without using the table, find the Laplace transform of
$f(t)=t^2$ and $g(t)=t^3$.

(Hint: use integration by parts).

{{< spoiler text="Solution" >}}
 We start with $\mathcal{L}\left\\{f(t)\right\\}$:

$$\begin{aligned}
F(s)= \int_0^{\infty} t^2e^{-st}\ dt&=\bigg[\frac{-t^{2}e^{- st}}{s}\bigg]_0^{\infty} +\frac{2}{s}\int_0^{\infty}t e^{- s t}\ dt \\\\
&=\frac{2}{s}\int_0^{\infty}te^{- s t}\ dt \\\\
&=\frac{2}{s}\left(\bigg[\frac{-te^{- st}}{s}\bigg]_0^{\infty} +\frac{1}{s}\int_0^{\infty} e^{- s t}\ dt \right)\\\\
&=\frac{2}{s^2}\int_0^{\infty}e^{- s t} \ dt\\\\
&=\frac{2}{s^3}. 
\end{aligned}$$

Now, let us move to $\mathcal{L}\left\\{g(t)\right\\}$:

$$\begin{aligned}
G(s)= \int_0^{\infty} t^3e^{-st}\ dt&=\bigg[\frac{-t^{3}e^{- st}}{s}\bigg]_0^{\infty} +\frac{3}{s}\int_0^{\infty}t^2 e^{- s t}\ dt \\\\
&=\frac{3}{s}\int_0^{\infty}t^2 e^{- s t} \ dt \\\\
&=\frac{3}{s}\cdot \frac{2}{s^3}= \frac{6}{s^4}. 
\end{aligned}$$

**Side note:** There is a pattern here to be observed:

$$\mathcal{L}\left\\{t^{n}\right\\} =\frac{n}{s}\mathcal{L}\left\\{t^{n-1}\right\\}$$
If you expand it further, you'd get

$$\mathcal{L}\left\\{t^{n}\right\\} =\frac{n}{s}\cdot \frac{n-1}{s} \mathcal{L}\left\\{t^{n-2}\right\\}=\frac{n}{s}\cdot \frac{n-1}{s}\cdots \frac{2}{s}\mathcal{L}\left\\{t\right\\}=\frac{n}{s}\cdot \frac{n-1}{s}\cdots \frac{2}{s}\cdot\frac{1}{s^2}$$
Which means that

$$\boxed{\mathcal{L}\left\\{t^{n}\right\\} = \frac{n(n-1)(n-2)\cdots2}{s^{n+1}}=\frac{n!}{s^{n+1}}}$$
For any integer $n\ge 1$.

{{< /spoiler >}}

---

**Exercise:** Let $$f(t)=\begin{cases} 
1 &\text{ if } 0\le t\le 2\\\\
\sinh(t) &\text{ if } t>2
\end{cases}$$ Find $\mathcal{L}\left\\{f(t)\right\\}$ .

{{< spoiler text="Solution" >}}


We start by breaking down the LT integral into two integrals

$$F(s)=\int_{0}^{\infty} f(t) e^{-s t}\ dt =\int_0^2 e^{-st}\ dt +\int_2^{\infty} \sinh(t) e^{-st}\ dt$$

We compute the two integrals separately:

$$\int_0^2 e^{-st}\ dt =\frac{1-e^{-2s}}{s}.$$

To compute the second integral, we use the definition of $\sinh(t)$
which is $\frac{e^t-e^{-t}}{2}$ :

$$\begin{aligned}
    \int_2^{\infty} \sinh(t) e^{-st}\ dt&=\frac{1}{2}\int_2^{\infty} (e^t-e^{-t}) e^{-st}\ dt\\\\
    &=\frac{1}{2}\int_2^{\infty} e^t\cdot e^{-st}\ dt-\frac{1}{2}\int_2^{\infty} e^{-t}\cdot e^{-st}\ dt\\\\
    &=\frac{1}{2}\int_2^{\infty} e^{-(s-1)t}\ dt-\frac{1}{2}\int_2^{\infty}  e^{-(s+1)t}\ dt\\\\
    &=\frac12\bigg[\frac{-e^{-(s-1)t}}{s-1}\bigg]_2^{\infty} -\frac12\bigg[\frac{-e^{-(s+1)t}}{s+1}\bigg]_2^{\infty}\\ \\ 
    &=\frac{1}{2}\left(\frac{e^{-2(s-1)}}{s-1}-
    \frac{e^{-2(s+1)}}{s+1}\right) 
\end{aligned}$$

Finally we have:

$$F(s)=\frac{1-e^{-2s}}{s}+\frac{1}{2}\left(\frac{e^{-2(s-1)}}{s-1}-
    \frac{e^{-2(s+1)}}{s+1}\right).$$

**Alternative approach to the second integral:** Let us assume that
$s>1$ and let us call the second integral $I$ ( see my comment at the
end):

$$I=\int_2^{\infty} \sinh(t) e^{-st}\ dt$$

Apply IBP (integration by parts) to get

$$I=\bigg[\cosh(t)e^{-st}\bigg]_{2}^\infty +s\int_0^{\infty} \cosh(t)e^{- st}\ dt$$

Note that if $s>1$, we have
$\displaystyle\lim_{t\to \infty} \cosh(t)e^{-st}=0$. Then,

$$I=-\cosh(2)e^{-2s} +s\int_2^{\infty} \cosh(t)e^{- st}\ dt$$ 
We apply
IBP again, to get

$$I=-\cosh(2)e^{-2s} +s\bigg[\sinh(t)e^{-s t}\bigg]_{2}^{\infty} +s^2\int_2^{\infty}\sinh(t)e^{- st}\ dt=-\cosh(2)e^{-2s}-s\sinh(2)e^{-2s}+s^2 I.$$

Now, we need to solve a simple linear equation to get $I$:

$$I= -\cosh(2)e^{-2s}-s\sinh(2)e^{-2s}+s^2 I$$
 we have

$$\boxed{I=\frac{\cosh(2)+s \sinh(2)}{s^2-1}e^{-2s}.}$$

{{< /spoiler >}}

---

**Exercise:** Find the inverse Laplace transform of the following
functions


1.  $\displaystyle
     \frac{s+2}{s^2}.$

2.  $\displaystyle\frac{2s+1}{s^2+s}.$

{{< spoiler text="Solution" >}}


1.  $$\mathcal{L}^{-1}\left\\{\frac{s+2}{s^2}\right\\}= \mathcal{L}^{-1}\left\\{\frac{1}{s}\right\\}+2\mathcal{L}^{-1}\left\\{\frac{1}{s^2}\right\\}= 1+2t.$$

2.  First, we need to apply a partial fraction decomposition. There are
    (at least) two ways to do it:

    1.  We try to find $a,b$ such that

        $$\frac{2s+1}{s^2+s} =\frac{2s+1}{s(s+1)} = \frac{a}{s}+\frac{b}{s+1}= \frac{(a+b)s+a}{s(s+1)}$$
        This leads to a simple system $\begin{cases}a+b=2\\\\a=1
                \end{cases}$, the solution is $a=b=1$.

    2.  With a simple rearrangement, we have

        $$\frac{2s+1}{s^2+s} =\frac{2s+1}{s(s+1)}=
                \frac{s+1}{s(s+1)}+\frac{s}{s(s+1)}=\frac{1}{s}+\frac{1}{s+1}$$

    Now, we go back to the ILT:

    $$\mathcal{L}^{-1}\left\\{\frac{2s+1}{s(s+1)}\right\\}=\mathcal{L}^{-1}\left\\{\frac{1}{s}\right\\}+\mathcal{L}^{-1}\left\\{\frac{1}{s+1}\right\\}=1+e^{-t}$$

{{< /spoiler >}}

---

**Exercise:** Consider the following function $f$:

$$f(x)=\begin{cases}
1,\qquad &  0\le t\le 1, \\
(2-t)e^{1-t}, \qquad & 1<t\le 2,\\\\
0,\qquad &t>2
\end{cases}$$

Find $F(s)$. *Hint:* Break the integral into two.

{{< spoiler text="Solution" >}}


Break the integral into

$$\int_0^\infty f(t)e^{-st}\ dt= \int_0^1 e^{-st}\ dt+\int_1^2 (2-t)e^{1-t}e^{-st}\ dt.$$

The first integral is easy

$$\int_0^1 e^{-st}\ dt= \frac{1-e^{-s}}{s}.$$

To evaluate the second integral, we use integration by part

$$\begin{aligned}
    \int_1^2 (2-t)e^{1-t}e^{-st}\ dt& =\int_1^2 (2-t)e^{1-(s+1)t}\ dt\\\\
    &= \left[ \frac{(2-t)e^{1-(s+1)t}}{-(s+1)}\right]_1^2 -\frac{1}{(s+1)^2} \int_1^2 e^{1-(s+1)t}\ dt\\
    &=\frac{e^{-s}}{s+1} -\frac{e^{-s}-e^{-2s-1}}{(s+1)^2}.
\end{aligned}$$

The final answer is

$$\frac{1-e^{-s}}{s}+\frac{e^{-s}}{s+1} -\frac{e^{-s}-e^{-2s-1}}{(s+1)^2}$$

{{< /spoiler >}}

---

**Exercise:** Let $a,b,c$ be positive real numbers such that $a<b$,
find the Laplace transform of the following function

$$f(x)=\begin{cases}
c,\qquad & \text{ if } a\le x\le b, \\\\
0, \qquad & \text{otherwise}.
\end{cases}$$

*Food for thought (will not be graded):* Would your answer change if
$c<0$? Would it change if $a$ and/or $b$ are negative?

{{< spoiler text="Solution" >}}


We have

$$\begin{aligned}
\int_0^\infty f(t) e^{-s t}\ dt& = \int_0^a0 e^{-st} \ dt+ \int_a^b c e^{-st} \ dt+\int_b^\infty 0 e^{-st} \ dt\\\\
&= c\int_a^b e^{-s t}\ dt \\\\
&= c\left(\frac{e^{-as}-e^{-b s}}{s}\right).
\end{aligned}$$

**Notes:** The answer will not change if $c<0$. However, if $a<0<b$,
then
$$F(s)=\int_0^b c e^{-s t}\ dt=  c\left(\frac{1-e^{-s t}}{s}\right).$$
Also, if $b<0$, then $F(s)=0$ for all $s$.

{{< /spoiler >}}

---

**Exercise:** Find the Laplace transform of
$\displaystyle f(t)=\cos\left(t- \frac{\pi}{3}\right)$.

{{< spoiler text="Solution" >}}
 Use the trig identity:

$$\boxed{\cos(a-b)=\sin(a)\sin(b)+\cos(a)\cos(b)}$$ 
to get

$$\begin{aligned}
 F(s)&=\mathcal{L}\left\\{\cos\left(t-\frac{\pi}{6}\right)\right\\}\\\\\\\\
&=\mathcal{L}\left\\{\sin(t)\sin\left(\frac{\pi}{3}\right)+\cos(t)\cos\left(\frac{\pi}{3}\right)\right\\}\\\\\\\\
&= \mathcal{L}\left\\{\frac{\sqrt{3}}{2} \sin(t)+\frac{1}{2}\cos(t)\right\\}\\\\\\\\
&=\frac{\sqrt{3}}{2} \mathcal{L}\left\\{\sin(t)\right\\}+\frac{1}{2} \mathcal{L}\left\\{\cos(t)\right\\} \\\\\\\\
&=\frac{\sqrt{3}}{2}\cdot \frac{1}{s^2+1} +\frac{1}{2}\cdot \frac{s}{s^2+1}\\\\\\\\
&= \frac{\sqrt{3}+s}{2(s^2+1)}.
\end{aligned}$$

{{< /spoiler >}}

---

**Exercise:** Find the Laplace transform of
$\displaystyle f(t)=\sin\left(t- \frac{\pi}{6}\right)$.

{{< spoiler text="Solution" >}}
 Use the trig identity:

$$\boxed{\sin(a-b)=\sin(a)\cos(b)-\sin(b)\cos(a)}$$
 to get
$$\begin{aligned}
 F(s)&=\mathcal{L}\left\\{\sin\left(t-\frac{\pi}{6}\right)\right\\}\\\\\\\\
&=\mathcal{L}\left\\{\sin(t)\cos\left(\frac{\pi}{6}\right)-\cos(t)\sin\left(\frac{\pi}{6}\right)\right\\}\\\\\\\\
&= \mathcal{L}\left\\{\frac{\sqrt{3}}{2} \sin(t)-\frac{1}{2}\cos(t)\right\\}\\\\\\\\
&=\frac{\sqrt{3}}{2} \mathcal{L}\left\\{\sin(t)\right\\}-\frac{1}{2} \cos(t) \\\\\\\\
&=\frac{\sqrt{3}}{2}\cdot \frac{1}{s^2+1} -\frac{1}{2}\cdot \frac{s}{s^2+1}\\\\\\\\
&= \frac{\sqrt{3}-s}{2(s^2+1)}.
\end{aligned}$$

**Note:** There is at least three other ways to do this:

1.  You can integrate by parts twice, you just need to be careful about
    evaluating at zero correctly.

2.  You can use complex numbers: evaluate
    $\displaystyle\int_0^{\infty} e^{i\left(t-\frac{\pi}{6}\right)}e^{-s t}\ dt$,
    then take the imaginary part of the result (think about Euler
    identity $e^{i\theta}=\cos(\theta)+i\sin(\theta)$).

3.  Make a u-sub: $u=t-\frac{\pi}{6}$ and use the antiderivative of
    $\sin(u)e^{- su}$ that we \"kind of\" derived in the notes.

{{< /spoiler >}}

---

**Exercise:** Find the inverse Laplace transform of the following
functions\



1.  $\displaystyle\frac{1}{3s^2-18}$

2.  $\displaystyle\frac{1}{s^2+s-20}.$

3.  $\displaystyle\frac{1}{s^2+2s+1}$.

4.  $\displaystyle\frac{1}{s^2+2s+2}$.

5.  $\displaystyle\frac{1}{s^2+2s+5}$.

6.  $\displaystyle\frac{e^{-3s}}{s^2+2s+5}$.

7.  $\displaystyle
     \frac{1-3s^2-5s}{s(s+1)^2+s}$

8.  $\displaystyle\frac{1-e^{-2s}}{s(s^2+1)}$

9.  $\displaystyle\frac{1}{s^2+2s-15}$.

10. $\displaystyle\frac{1}{s^2+2s+10}$.

11. $\displaystyle\frac{1-3s^2-4s}{s(s+1)^2+s}$


{{< spoiler text="Solution" >}}


1.  We have

    $$\frac{1}{3s^2-18} = \frac{1}{3}\left(\frac{1}{s^2-6}\right) =\frac{1}{3\sqrt{6}}\left(\frac{\sqrt{6}}{s^2-(\sqrt{6})^2}\right)$$
    Therefore,

    $$\mathcal{L}^{-1}\left\\{\frac{1}{3s^2-18}\right\\}= \frac{1}{3\sqrt{6}}\mathcal{L}^{-1}\left\\{\frac{\sqrt{6}}{s^2-(\sqrt{6})^2}\right\\}= \frac{1}{3\sqrt{6}}\sinh\left(t\sqrt{6}\right)$$

2.  We apply PFD to the given fraction

    $$\frac{1}{s^2+s-20}=\frac{1}{(s+5)(s-4)}=
        \frac{a}{s+5}+\frac{b}{s-4}=\frac{(a+b)s-4a+5b}{(s+5)(s-4)}.$$

    Which leads to the system

    $$\begin{cases}
        a+b=0,\\\\
        -4a+5b=1,\end{cases}
        \overset{4(1)+(2)}{\Longrightarrow} 9b=1\Rightarrow b=\frac{1}{9}\Rightarrow a=\frac{-1}{9}.$$

    Therefore

    $$\mathcal{L}^{-1}\left\\{\frac{1}{s^2+s-20}\right\\} =-\frac{1}{9}\mathcal{L}^{-1}\left\\{\frac{1}{s+5}\right\\}+\frac{1}{9}\mathcal{L}^{-1}\left\\{\frac{1}{s-4}\right\\}= \frac{-e^{-5t}+e^{4t}}{9}.$$

3.  We have

    $$\frac{1}{s^2+2s+1}=\frac{1}{(s+1)^2}$$
     Using the 1st translation
    theorem, we get

    $$\mathcal{L}^{-1}\left\\{\frac{1}{(s+1)^2}\right\\} =\mathcal{L}^{-1}\left\\{\frac{1}{s^2}\right\\} e^{-t} =t e^{-t}$$

4.  Complete the square

    $$\frac{1}{s^2+2s+2}=\frac{1}{(s+1)^2+1}$$

    Apply the second translation theorem

    $$\mathcal{L}^{-1}\left\\{\frac{1}{(s+1)^2+1}\right\\}= \mathcal{L}^{-1}\left\\{\frac{1}{s^2+1}\right\\}e^{-t}=\sin(t) e^{-t}$$

5.  Check example 3 for more details. We have

    $$\frac{1}{s^2+2s+5}= \frac{1}{(s+1)^2+2^2}$$ 
    Apply the second
    translation theorem

    $$\mathcal{L}^{-1}\left\\{\frac{1}{(s+1)^2+2^2}\right\\}=\mathcal{L}^{-1}\left\\{\frac{1}{s^2+2^2}\right\\}e^{-t}=\frac{1}{2}\sin(2t)e^{-t}.$$

6.  Use the previous ILT and the second translation theeorem to get

    $$\mathcal{L}^{-1}\left\\{\frac{e^{-3s}}{(s+1)^2+2^2}\right\\}=\frac{1}{2}\sin(2(t-3))e^{-(t-3)}\mathscr{U}(t-3).$$

7.  We need to factor the denominator first and then apply PFD

    $$\begin{aligned}
    F(s)= \frac{1-3s^2-5s}{s(s+1)^2+s}&= \frac{1-3s^2-5s}{s((s+1)^2+1)}= \frac{a}{s}+\frac{bs+c}{(s+1)^2+1}\\\\
    &=\frac{(a+b)s^2+(2a+c)s+2a}{s((s+1)^2+1)}
    \end{aligned}$$

    By comparing the coefficients, we get

    $$\begin{cases}
    2a=1\\\\2a+c=-5\\\\a+b=-3
    \end{cases}\Longrightarrow \begin{cases}
    a=\frac{1}{2}\\\\b=\frac{-7}{2}\\\\c=-6. 
    \end{cases}$$

    Thus,
    $$F(s)=\frac{1}{2s}+\frac{\frac{-7}{2} s-6}{(s+1)^2+1}=\frac{1}{2s}+\frac{\frac{-7}{2} s-\frac{7}{2}}{(s+1)^2+1}+\frac{-\frac{5}{2}}{(s+1)^2+1}$$

    So,

    $$F(s)=\frac{1}{2s}-\frac{7}{2}\cdot \frac{s+1}{(s+1)^2+1}-\frac{5}{2}\cdot \frac{1}{(s+1)^2+1}$$
    The inverse LT of the first term is easy, to the find the other two
    inverse LTs we need to use the first translation theorem.

    $$f(t)=\frac{1}{2} -\frac{7}{2}\cos(t)e^{-t}-\frac{5}{2}\sin(t) e^{-t}.$$

8.  You can always perform a PFD like we did in the previous example but
    there is a shortcut here

    $$\frac{1}{s(s^2+1)}=s \frac{s^2}{s^2(s^2+1)}= s \frac{(s^2+1)-s^2}{s^2(s^2+1)}=s\frac{1}{s^2}-s \frac{1}{s^2+1}=\frac{1}{s}-\frac{s}{s^2+1}.$$

    Now, we have

    $$\frac{1-e^{-2s}}{s(s^2+1)}= \left(\frac{1}{s}-\frac{s}{s^2+1}\right) -\left(\frac{1}{s}-\frac{s}{s^2+1}\right)e^{-2s}$$

    The first part is easy, you need to apply the 2nd translation
    theorem to the second one to get

    $$1-\cos(t) -\left(1-\cos(t-2)\right) \mathscr{U}(t-2)$$

9.  We have
    $$\displaystyle\frac{1}{s^2+2s-15}=\frac{1}{(s+5)(s-3)}=\frac{a}{s+5}+\frac{b}{s-3}= \frac{(a+b)s+(5b-3a)}{(s+5)(s-3)}$$

    We have $a+b=0$ and $5b-3a=1$ which leads to $a=\frac{-1}{8}$ and
    $b=\frac{1}{8}$. Therefore

    $$\mathcal{L}^{-1}\left\\{\frac{1}{s^2+2s-15}\right\\} = \frac{e^{3t}-e^{-5t}}{8}.$$

    **Note:** There is another way to do this using the translation
    theorem:
    $$\mathcal{L}^{-1}\left\\{\frac{1}{s^2+2s-15}\right\\}=\mathcal{L}^{-1}\left\\{\frac{1}{(s+1)^2-4^2}\right\\}=\frac{1}{4}
        \mathcal{L}^{-1}\left\\{\frac{4}{(s+1)^2-4^2}\right\\}=\frac{1}{4}\sinh(4t)e^{-t}.$$

10. We have
    $$\mathcal{L}^{-1}\left\\{\frac{1}{s^2+2s+10}\right\\}=\mathcal{L}^{-1}\left\\{\frac{1}{(s+1)^2+3^2}\right\\}=\frac{1}{3}\sin(3t)e^{-t}.$$

11. We need to factor the denominator first and then apply PFD

    $$\begin{aligned}
    F(s)= \frac{1-3s^2-4s}{s(s+1)^2+s}&= \frac{1-3s^2-4s}{s((s+1)^2+1)}= \frac{a}{s}+\frac{bs+c}{(s+1)^2+1}\\\\
    &=\frac{(a+b)s^2+(2a+c)s+2a}{s((s+1)^2+1)}
    \end{aligned}$$

    By comparing the coefficients, we get

    $$\begin{cases}
    2a=1\\\\2a+c=-4\\\\a+b=-3
    \end{cases}\Longrightarrow \begin{cases}
    a=\frac{1}{2}\\\\b=\frac{-7}{2}\\\\c=-5. 
    \end{cases}$$

    Thus,
    $$F(s)=\frac{1}{2s}+\frac{\frac{-7}{2} s-6}{(s+1)^2+1}=\frac{1}{2s}+\frac{\frac{-7}{2} s-\frac{7}{2}}{(s+1)^2+1}+\frac{-\frac{3}{2}}{(s+1)^2+1}$$

    So,

    $$F(s)=\frac{1}{2s}-\frac{7}{2}\cdot \frac{s+1}{(s+1)^2+1}-\frac{3}{2}\cdot \frac{1}{(s+1)^2+1}$$
    The inverse LT of the first term is easy, to the find the other two
    inverse LTs we need to use the first translation theorem.

    $$f(t)=\frac{1}{2} -\frac{7}{2}\cos(t)e^{-t}-\frac{3}{2}\sin(t) e^{-t}.$$

{{< /spoiler >}}

---

**Exercise:** Solve the following differential equations using Laplace
transform:

1.  $\displaystyle y'(t)+y(t)=\cos(3t),\qquad  y(0)=0.$

2.  $\displaystyle y''(t)+y(t)=\cos(3t),\qquad  y(0)=1,y'(0)=2.$

3.  $\displaystyle y''(t)-4y'(t)+4y(t)=\cos(2t),\qquad  y(0)=0,\  y'(0)=1.$

4.  $\displaystyle y'(t)-y(t)=\cosh(3t),\qquad  y(0)=0.$

5.  $\displaystyle y''(t)-2y'(t)+5y(t)=\cos(2t),\qquad  y(0)=0,\  y'(0)=1.$

{{< spoiler text="Solution" >}}


1.  There are three steps:

    1.  Apply LT to both sides $$sY(s)-0 +Y(s)=\frac{s}{s^2+9}$$

    2.  Solve for $Y(s)$: $$Y(s)=\frac{s}{(s+1)(s^2+9)}$$

    3.  Apply the ILT: First, start with the PFD

        $$\frac{s}{(s+1)(s^2+9)}=\frac{a}{s+1}+\frac{bs+c}{s^2+9}=\frac{(a+b)s^2+(b+c)s+9a+c}{(s+1)(s^2+9)}\longrightarrow\begin{cases}
            a+b=0,\\
            b+c=1,\\
            9a+c=0.
            \end{cases}$$ The solution to the above problem is
        $(\frac{-1}{10},\frac{1}{10},\frac{9}{10})$. Therefore,

        $$Y(s)=\frac{1}{10}\left(\frac{-1}{s+1}+\frac{s}{s^2+9}+\frac{9}{s^2+9}\right).$$

        Consequently,

        $$y(t)=\frac{1}{10}\left(-e^{-t}+\cos(3t)+3\sin(3t)\right).$$

2.  We follow the same steps

    1.  Apply LT to both sides $$s^2Y(s)-s-2+Y(s)=\frac{s}{s^2+9}$$

    2.  Solve for $Y(s)$

        $$Y(s)=\frac{s}{(s^2+9)(s^2+1)} +\frac{s+2}{s^2+1}$$

    3.  Apply the ILT: First, you need to apply the PFD to the first
        fraction

        $$\frac{s}{(s^2+9)(s^2+1)}=\frac{as+b}{s^2+1}+\frac{c s+d}{s^2+9}=\frac{(a+c)s^3+(b+d)s^2+(9a+c)s+9b+d}{(s^2+9)(s^2+1)}$$
        It is easy to see that $b=d=0$. After that, you have to solve a
        $2\times 2$ system to get $a=\frac{1}{8}$ and $b=\frac{-1}{8}$.
        Now, we have:

        $$Y(s)=\frac{1}{8}\left(\frac{s}{s^2+1}-\frac{s}{s^2+9}\right) +\frac{s}{s^2+1}+\frac{2}{s^2+1}$$
        Which gives us

        $$y(t)=\frac{1}{8}\left(\cos(t)-\cos(3t)\right)+\cos(t)+2\sin( t)$$

        $$\boxed{y(t)= \frac{9}{8}\cos(t)-\frac{1}{8}\cos(3t)+2\sin(t)}$$

3.  I will skip the first few steps and jump right into

    $$Y(s)=\frac{1}{(s-2)^2} +\frac{s}{(s-2)^2(s^2+4)}.$$ Therefore,

    $$y(t)=te^{2t} +\mathcal{L}^{-1}\left\\{\frac{s}{(s-2)^2(s^2+4)}\right\\}$$

    Apply PFD

    $$\frac{s}{(s-2)^2(s^2+4)}=\frac{a}{s-2}+\frac{b}{(s-2)^2}+\frac{c s+d}{s^2+4}$$

    You will get the following system

    $$\begin{cases}
    a+c=0\\\\-2 a + b - 4 c + d=0\\\\4 a + 4 c - 4 d=1 \\\\-8 a + 4 b + 4 d=0
    \end{cases}\Longrightarrow \begin{cases}
    a=0\\\\b=\frac{1}{4}\\\\c=0\\\\d=-\frac{1}{4}. 
    \end{cases}$$ (A good first step would be using (1) and (3) to find
    $d$). Now,

    $$\frac{s}{(s-2)^2(s^2+4)}=\frac{1}{4}\left(\frac{1}{(s-2)^2}- \frac{1}{s^2+4}\right)$$

    Finally, we get

    $$y(t)=t e^{2 t} +\frac{1}{4} te^{2t} -\frac{1}{8} \sin(2t)=\frac{5}{4} te^{2t} -\frac{1}{8} \sin(2t)$$

    **Note 1:** You can combine the two fraction in the first line and
    work from there.

    **Note 2:** You can avoid the system by noticing that

    $$\frac{s}{(s-2)^2(s^2+4)} =\frac{1}{4} \frac{4s}{(s^2-4s+4)(s^2+4)}=\frac{1}{4} \frac{(s^2+4)-(s^2-4s+4)}{(s^2-4s+4)(s^2+4)}.$$

4.  There are three steps:

    1.  Apply LT to both sides $$sY(s)-0 -Y(s)=\frac{s}{s^2-9}$$

    2.  Solve for $Y(s)$: $$Y(s)=\frac{s}{(s-1)(s^2-9)}$$

    3.  Apply the ILT: First, start with the PFD

        $$\frac{s}{(s-1)(s^2-9)}=\frac{a}{s-1}+\frac{bs+c}{s^2-9}=\frac{(a+b)s^2+(c-b)s-9a-c}{(s-1)(s^2-9)}\longrightarrow\begin{cases}
            a+b=0,\\
            c-b=1,\\
            -9a-c=0.
            \end{cases}$$ The solution to the above problem is
        $(\frac{-1}{8},\frac{1}{8},\frac{9}{8})$. Therefore,

        $$Y(s)=\frac{1}{8}\left(\frac{-1}{s-1}+\frac{s}{s^2-9}+\frac{9}{s^2-9}\right).$$

        Consequently,

        $$y(t)=\frac{1}{8}\left(-e^{t}+\cosh(3t)+3\sinh(3t)\right).$$

        **Note:** There is another way to do PFD

        $$\frac{s}{(s-1)(s^2-9)} = \frac{a}{s-1}+\frac{b}{s-3}+\frac{c}{s+3}.$$
        You will get $a=\frac{-1}{8}, b= \frac{1}{4}$ and
        $c=\frac{-1}{8}$. The final answer would be

        $$y(t)=\frac{1}{8}\left( -e^{t}+2e^{3t}-e^{-3t}\right).$$

5.  After applying LT, we get

    $$(s^2-2s+5)Y(s)=\frac{s}{s^2+4}+1$$
    $$Y(s)=\frac{s}{(s^2-2s+5)(s^2+4)} +\frac{1}{s^2-2s+5}.$$ Let us
    start with the ILT of the second fraction

    $$\mathcal{L}^{-1}\left\\{\frac{1}{s^2-2s+5}\right\\}= \mathcal{L}^{-1}\left\\{\frac{1}{(s-1)^2+4}\right\\}= \frac{1}{2}\sin(2t)e^t.$$
    To find the ILT of the first fraction, we need to perform a PFD
    first

    $$\frac{s}{(s^2-2s+5)(s^2+4)}= \frac{a s+b}{s^2-2s+5}+ \frac{c s+d}{s^2+4}=\frac{(a+c)s^3+(b-2c+d)s^2+(4a+5c-2d)s+4b+5d}{(s^2-2s+5)(s^2+4)}.$$

    This is a $4\times 4$ system but after substituting $a=-c$, we get a
    $3\times 3$ system:

    $$\begin{cases}
     b-2c+d=0,\\\\
     c-2d=1, \\\\
     4b+5d=0
     \end{cases}\overset{b=2c-d}{\Longrightarrow} \begin{cases}
     c-2d=1, \\\\
     8c+d=0
     \end{cases}
     \longrightarrow c=\frac{1}{17},\ d=\frac{-8}{17}.$$ 
     From there, we
    get $a=\frac{-1}{17}, b=\frac{10}{17}$. Now, we have

    $$\begin{aligned}
    \displaystyle\frac{s}{(s^2-2s+5)(s^2+4)} &=\frac{1}{17} \left(\frac{-s+10}{(s-1)^2+4} + \frac{s-8}{s^2+4}\right),\\\\\\\\
     \displaystyle&= \frac{1}{17} \left(\frac{-(s-1)}{(s-1)^2+4} +\frac{9}{(s-1)^2+4}  +\frac{s}{s^2+4}-\frac{8}{s^2+4}\right)
    \end{aligned}$$
    
     The ILT of the expression is

    $$\frac{1}{17}\left( -\cos(2t)e^{t} +\frac{9}{2}\sin(2t)e^t +\cos(2t)-4\sin(2t)\right).$$

    Finally,

    $$\boxed{y(t)= \frac{1}{17}\left( -\cos(2t)e^{t} +\frac{9}{2}\sin(2t)e^t +\cos(2t)-4\sin(2t)\right) +\frac{1}{2}\sin(2t)e^t}$$

{{< /spoiler >}}

---

**Exercise:** Apply Laplace transform to this equation and solve it for
$Y(s)$ $$y''(t)+y(t)=f(t),\qquad  y(0)=0,y'(0)=0.$$ Where

$$f(t)=\begin{cases}
1,& 0\le t\le 2, \\
0,& t>2.
\end{cases}$$ You do not have to apply the inverse Laplace transform.

{{< spoiler text="Solution" >}}
 The LT of $f$ is

$$F(s)=\int_0^2 e^{-s t}\ dt=\frac{1-e^{-s}}{s}.$$

By applying LT to both sides, we get

$$(s^2+1) Y(s)=\frac{1-e^{-2s}}{s}$$

Therefore,

$$Y(s)=\frac{1-e^{-2s}}{s(s^2+1)}$$

{{< /spoiler >}}

---

**Exercise:** Use Laplace transform to solve the following IVP
$$y''(t)+4y(t)=f(t),\qquad  y(0)=0,y'(0)=0.$$ Where $$f(t)=\begin{cases}
0,& 0\le t\le 2, \\
1,& t>2.
\end{cases}$$ {{< spoiler text="Solution" >}}
 Apply ILT to both sides
$$s^2Y(s)+4Y(s)=\frac{1}{s}e^{-2s}.$$ Solve for $Y(s)$
$$Y(s)=\frac{1}{s(s^2+4)}e^{-2s}.$$ Use PFD (details skipped)
$$Y(s)=\frac{1}{4}\left(\frac{1}{s}-\frac{s}{s^2+4}\right)e^{-2s}.$$ Use
the second translation theorem to get

$$y(t)= \frac{1}{4}\left(1-\cos(2(t-2))\right)\mathscr{U}(t-2).$$

{{< /spoiler >}}

---

**Exercise:** Use Laplace Transform to solve the following IVP:\
$$y''(t)-2y'(t)+y(t)=e^{2t}\mathscr{U}(t-1), \qquad  y(0)=1, y'(0)=5.$$

{{< spoiler text="Solution" >}}
 First, we need to compute the Laplace transform of the
right hand side

$$\mathcal{L}\left\\{e^{2t}\mathscr{U}(t-1)\right\\}= e^{2}\mathcal{L}\left\\{e^{2(t-1)}\mathscr{U}(t-1)\right\\}=e^{2}e^{-s}\mathcal{L}\left\\{e^{2t}\right\\}=e^{2}\frac{e^{-s}}{s-2}.$$
The LT of the left hand side is easy

$$\mathcal{L}\left\\{y''(t)-2y'(t)+y(t)\right\\}= (s-1)^2Y(s)- s -3$$
Therefore

$$Y(s)=\frac{s+3}{(s-1)^2} +e^2 \frac{1}{(s-1)^2(s-2)} e^{-s}$$

We have

$$\mathcal{L}^{-1}\left\\{\frac{s+3}{(s-1)^2}\right\\} =\mathcal{L}^{-1}\left\\{\frac{s-1}{(s-1)^2}+\frac{4}{(s-1)^2}\right\\} =\mathcal{L}^{-1}\left\\{\frac{1}{(s-1)}+\frac{4}{(s-1)^2}\right\\} =e^t(1+4t)$$

and

$$\mathcal{L}^{-1}\left\\{ \frac{1}{(s-1)^2(s-2)}\right\\}= \mathcal{L}^{-1}\left\\{-\frac{1}{s-1}-\frac{1}{(s-1)^2}+\frac{1}{s-2}\right\\}=e^{2t}-e^t(t+1).$$

By applying the second translation theorem we get

$$\mathcal{L}^{-1}\left\\{e^{2} \frac{e^{-s}}{(s-1)^2(s-2)}\right\\}=e^{2}\left(e^{2t-2}-e^{t-1}t\right)\mathscr{U}(t-1)=\left(e^{2t}-e^{t+1}t\right)\mathscr{U}(t-1).$$

Combining the two ILT, we get $$\boxed{\boxed{
y(t)=e^t(1+4t)+\left(e^{2t}-e^{t+1}t\right)\mathscr{U}(t-1)
}}$$

{{< /spoiler >}}

---

**Exercise:** Use Laplace Transform to solve the following IVP:\
$$y''(t)-4y'(t)+5y(t)=e^{3t}\mathscr{U}(t-2), \qquad  y(0)=1, y'(0)=0.$$

{{< spoiler text="Solution" >}}
 First, we need to compute the Laplace transform of the
right hand side

$$\mathcal{L}\left\\{e^{3t}\mathscr{U}(t-2)\right\\}= e^{6}\mathcal{L}\left\\{e^{3(t-2)}\mathscr{U}(t-1)\right\\}=e^{6}e^{-2s}\mathcal{L}\left\\{e^{3t}\right\\}=e^{6}\frac{e^{-2s}}{s-3}.$$
The LT of the left hand side is easy

$$\mathcal{L}\left\\{y''(t)-4y'(t)+5y(t)\right\\}= (s^2-4s+5)Y(s)+ s-4$$
Therefore

$$Y(s)=\frac{s-4}{s^2-4s+5} +e^6 \frac{1}{(s^2-4s+5)(s-3)} e^{-2s}$$

We have

$$\mathcal{L}^{-1}\left\\{\frac{s-4}{s^2-4s+5}\right\\} =\mathcal{L}^{-1}\left\\{\frac{s-2}{(s-2)^2+1}-2\frac{1}{(s-2)^2+1}\right\\}  =\left(\cos(t)-2\sin(t)\right)e^{2t}.$$

Using PFD (details skipped)

$$\mathcal{L}^{-1}\left\\{ \frac{1}{(s^2-4s+5)(s-2)}\right\\}= \frac{1}{2}\mathcal{L}^{-1}\left\\{\frac{1}{s-3}-\frac{s-1}{s^2-4s+5}\right\\}=\frac{1}{2}e^{3t} -\frac{e^{2t}}{2}\left(\cos(t)+\sin(t)\right).$$

By applying the second translation theorem we get

$$\mathcal{L}^{-1}\left\\{e^{6} \frac{e^{-2s}}{(s^2-4s+5)(s-2)}\right\\}=e^{6}\left(\frac{1}{2}e^{3(t-2)} -\frac{e^{2(t-2)}}{2}\left(\cos(t-2)+\sin(t-2)\right)\right)\mathscr{U}(t-2).$$

Combining the two ILT, we get $$\boxed{\boxed{
y(t)=\left(\cos(t)-2\sin(t)\right)e^{2t}+e^{6}\left(\frac{1}{2}e^{3(t-2)} -\frac{e^{2(t-2)}}{2}\left(\cos(t-2)+\sin(t-2)\right)\right)\mathscr{U}(t-2)
}}$$

It can be simplified to
$$y(t)=e^{2t}\left[\cos(t)-2\sin(t)+\frac{1}{2}\left(e^{t} -e^{2}\left(\cos(t-2)+\sin(t-2)\right)\right)\mathscr{U}(t-2)\right]$$

{{< /spoiler >}}

---

**Exercise:** Use theorem 7.4.1 to compute
$\mathcal{L}\left\\{t^3\cos(t)\right\\}$.

{{< spoiler text="Solution" >}}
 We have

$$\begin{aligned}
\mathcal{L}\left\\{t^3\cos(t)\right\\}&=-\frac{\mathrm{d}^3}{\mathrm{d}s^3}\mathcal{L}\left\\{\cos(t)\right\\}= -\frac{\mathrm{d}^3}{\mathrm{d}s^3}\left(\frac{s}{s^2+1}\right)\\\\\\\\
&=-\frac{\mathrm{d}^2}{\mathrm{d}s^2}\left(\frac{1-s^2}{\left(s^2+1\right)^2}\right)\\\\\\
&=-\frac{\mathrm{d}}{\mathrm{d}s}\left(\frac{2 s \left(s^2-3\right)}{\left(s^2+1\right)^3}\right)\\\\\\\\
&=-\left(-\frac{6 \left(s^4-6 s^2+1\right)}{\left(s^2+1\right)^4}\right) \\\\\\\\
&=-\frac{6 \left(s^4-6 s^2+1\right)}{\left(s^2+1\right)^4}
\end{aligned}$$

There are other equivalent forms that have $(s^2+1)^8$ in the
denominator.

{{< /spoiler >}}

---

**Exercise:** Write the following inverse Laplace transforms as
convolutions (You do not need to evaluate the integral):



1.  $\displaystyle\mathcal{L}^{-1}\left\\{\frac{1}{(s-4)s}\right\\},\hspace{3cm}$

2.  $\displaystyle\mathcal{L}^{-1}\left\\{\frac{s}{(s^2+a^2)^2}\right\\}.$

3.  $\displaystyle\mathcal{L}^{-1}\left\\{\frac{1}{(s^2-2s+2)(s^2+2s+2)}\right\\}.$

4.  $\displaystyle\mathcal{L}^{-1}\left\\{\frac{s}{(s^2+4)(s^2+1)}\right\\}.$


{{< spoiler text="Solution" >}}


1.  $$\mathcal{L}^{-1}\left\\{\frac{1}{(s-4)s}\right\\}=\mathcal{L}^{-1}\left\\{\frac1s\right\\}* \left\\{\frac{1}{s-4}\right\\}=(1)* (e^{4t})=\int_0^te^{4r}\ dr$$

2.  $$\mathcal{L}^{-1}\left\\{\frac{s}{(s^2+a^2)^2}\right\\}=\mathcal{L}^{-1}\left\\{\frac{s}{(s^2+a^2)}\right\\}*\mathcal{L}^{-1}\left\\{\frac{1}{(s^2+a^2)}\right\\}$$

    If $a\neq 0$, we have

    $$\mathcal{L}^{-1}\left\\{\frac{s}{(s^2+a^2)}\right\\}*\mathcal{L}^{-1}\left\\{\frac{1}{(s^2+a^2)}\right\\}= \frac{1}{a}(\cos(a t)) * (\sin(a t))=\frac{1}{a}\int_0^t \cos(a r)\sin(a(t-r)) dr$$

    If $a=0$, then

    $$\mathcal{L}^{-1}\left\\{\frac{s}{(s^2+a^2)^2}\right\\}=\mathcal{L}^{-1}\left\\{\frac{1}{s^3}\right\\}= \frac{t^2}{2}.$$

3.  
    $$\begin{aligned}
    \mathcal{L}^{-1}\left\\{\frac{1}{(s^2-2s+2)(s^2+2s+2)}\right\\}&=
    \mathcal{L}^{-1}\left\\{\frac{1}{(s-1)^2+1}\right\\} * \mathcal{L}^{-1}\left\\{\frac{1}{(s+1)^2+1}\right\\}\\\\
    &=(e^t\sin(t)) * (e^{-t}\sin(t))\\\\\\
    &=\int_0^t e^{r-(t-r)}\sin(r)\sin(t-r)\ dr\\\\
    &=\int_0^t e^{2r-t}\sin(r)\sin(t-r)\ dr
    \end{aligned}$$

4.  This one is very similar to (b):

    $$\mathcal{L}^{-1}\left\\{\frac{s}{(s^2+4)(s^2+1)}\right\\}=\mathcal{L}^{-1}\left\\{\frac{s}{s^2+4}\right\\} * \mathcal{L}^{-1}\left\\{\frac{1}{s^2+1}\right\\}=(\cos(2t))*(\sin(t))=\int_0^t \cos(2r)\sin(t-r)\ dr$$

{{< /spoiler >}}

---

**Exercise:** Find the following Laplace transforms without evaluating
the integral first



1.  $\displaystyle\mathcal{L}\left\\{\int_0^te^r \ dr\right\\}$

2.  $\displaystyle\mathcal{L}\left\\{\int_0^t re^{r} \ dr\right\\}$

3.  $\displaystyle\mathcal{L}\left\\{t \int_0^t r e^r \ dr\right\\}$

4.  $\displaystyle\mathcal{L}\left\\{\int_0^t r\sin(r) \ dr\right\\}$


{{< spoiler text="Solution" >}}


1.  Apply theorem 7.4.3 to get
    $$\mathcal{L}\left\\{\int_0^te^r \ dr\right\\} = \frac{1}{s}\mathcal{L}\left\\{e^t\right\\}=\frac{1}{s(s-1)}.$$

2.  This is similar to (a),
    $$\mathcal{L}\left\\{\int_0^tre^r \ dr\right\\} = \frac{1}{s}\mathcal{L}\left\\{te^t\right\\}=\frac{1}{s(s-1)^2}.$$
    The first translation theorem can be applied to get
    $\mathcal{L}\left\\{te^t\right\\} = \frac{1}{(s-1)^2}$.

3.  Use the derivative of transforms theorem to get

    $$\mathcal{L}\left\\{t\int_0^tre^r \ dr\right\\}=-\frac{d}{ds} \mathcal{L}\left\\{\int_0^tre^r \ dr\right\\}=-\frac{d}{ds}\frac{1}{(s-1)^2}= \frac{3 s-1}{s^2(s-1)^3 }.$$

4.  $$\mathcal{L}\left\\{\int_0^t r\sin(r) \ dr\right\\} = \frac{1}{s}\mathcal{L}\left\\{t\sin(t)\right\\}= \frac{-1}{s}\frac{d}{ds} \frac{1}{s^2+1}=\frac{2}{\left(s^2+1\right)^2}.$$

{{< /spoiler >}}

---

**Exercise:** Use Laplace transform to the following (so called
integro-differential equation) to find $y(t)$

$$y'(t)=1-\sin( t)-\int_{0}^{t} y(r)\ d r,\qquad  y(0)=0.$$ 
**Note:**
The steps are similar as for ODES: Apply LT, solve for $Y(s)$, apply
ILT.

{{< spoiler text="Solution" >}}


Apply LT to both sides to get

$$sY(s)=\frac1s-\frac{1}{s^2+1} -\frac{1}{s}Y(s)$$

This can be simplified to

$$(s^2+1)Y(s)=1-\frac{s}{s^2+1}$$ 
so

$$Y(s)=\frac{1}{s^2+1}-\frac{s}{(s^2+1)^2}$$
 To compute the LT of the
second part, we use the convolution theorem

$$\mathcal{L}^{-1}\left\\{\frac{s}{(s^2+1)^2}\right\\}=\mathcal{L}^{-1}\left\\{\frac{s}{s^2+1}\cdot\frac{1}{s^2+1}\right\\}=\int_0^t \sin(r)\cos(t-r)\ dr$$

To compute this integral we can use
$\sin(a)\cos(b)=\frac{1}{2}\left(\sin(a+b)+\sin(a-b)\right)$

$$\begin{aligned}
 \int_0^t \sin(r)\cos(t-r)\ dr&= \frac{1}{2}\int_0^t \sin(t)\ dr+ \frac{1}{2}\int_0^t \sin(2r-t)\ dr \\\\
&=\frac{1}{2}t \sin(t) +\frac{1}{2}\bigg[\frac{-\cos(2r-t)}{2}]_{r=0}^t\\\\
&=\frac{1}{2}t\sin(t) +0\\
&=\frac{1}{2}t\sin(t). 
\end{aligned}$$

The final answer is

$$\boxed{y(t)=\sin(t)-\frac{1}{2}t\sin(t).}$$

{{< /spoiler >}}

---

**Exercise:** $f$ is a $2\pi-$periodic function, defined on $[0,2\pi)$
by

$$f(t)=\begin{cases}
        \sin(t), & 0\le t<\pi,\\
        0, & \pi\le t<2\pi
\end{cases}$$

Here's the graph of $f$:

Find the Laplace transform of $f$.

{{< spoiler text="Solution" >}}
 Using the theorem about periodic functions, we have

$$F(s)=\frac{1}{1-e^{-2\pi s}} \underbrace{\int_0^{\pi}\sin(t) e^{-st} \ dt }_{\text{Let us call this }I}$$
There are at least two ways to compute $I$:

1.  1st method: Integrate by parts twice and solve for $I$
    $$\begin{aligned}
      I&=  \int_0^{\pi}\sin(t) e^{-st} \ dt \\\\
      & = \bigg[-\cos(t)e^{-st}]_{0^\pi} -s\int_0^{\pi} \cos(t)e^{-s t}\ dt\\\\
      & =e^{-\pi s}+1-s\int_0^{\pi} \cos(t)e^{-s t}\ dt \\\\
      & =e^{-\pi s}+1- s\bigg[ \sin(t)e^{-s t} \bigg]_0^\pi -s^2 \int_0^{\pi } \sin(t) e^{-st}\ dt\\\\ 
      I & =e^{-\pi s}+1-s^2I.
    \end{aligned}$$

    And then you can solve for $I$ to get
    $\displaystyle I=\frac{e^{-\pi s}+1}{s^2+1}$. Finally we have

    $$F(s) = \frac{1}{1-e^{-2\pi s} }\cdot \frac{e^{-\pi s}+1}{s^2+1}.$$

    This can be simplified a little bit but there is no neeed for that.

2.  2nd method: we can write $I$ as

    $$\begin{aligned}
    I&= \int_0^{\infty}\sin(t)\left(1-\mathscr{U}\left(t-\pi\right)\right) e^{-st} \ dt \\\\
    &=\mathcal{L}\left\\{\sin(t)\right\\}- \mathcal{L}\left\\{\sin(t)\mathscr{U}(t-\pi)\right\\}\\\\ 
    & = \mathcal{L}\left\\{\sin(t)\right\\}+\mathcal{L}\left\\{\sin(t-\pi)\mathscr{U}(t-\pi)\right\\}
        \\\\
        & =\frac{1}{s^2+1}+\frac{e^{-\pi s}}{s^2+1}. 
    \end{aligned}$$

    As you can see, no integration skills were needed here. This shows
    the importance of algebraic manipulations and the basic theorems of
    Laplace transform.

**Note:** There are other methods to evaluate $I$. For example, if you
are comfortable with complex numbers, you can evaluate

$$\int_0^{\pi} e^{it-st} \ dt$$ 
and take the imaginary part.

{{< /spoiler >}}

---

**Exercise:** Use Laplace transform to solve the following system:\
$$\begin{cases} 
        x'(t)+y'(t)=-3x(t)+2\\\\
        x'(t)-2y'(t)=-8t \\
\end{cases}\qquad \qquad  x(0)=1, \quad y(0)=-1.$$

{{< spoiler text="Solution" >}}
 Apply Laplace transform to both sides to get

$$\begin{bmatrix}
s+3& s\\\\ s&-2s \end{bmatrix}\begin{bmatrix}\displaystyle X(s) \\\\\displaystyle Y(s) \end{bmatrix}= \begin{bmatrix} \displaystyle\frac{2}{s} \\\\\\\\ \displaystyle\frac{-8}{s^2}+3 \end{bmatrix}.$$

Multiply both sides with the inverse matrix to get

$$\begin{bmatrix}\displaystyle X(s) \\\\\displaystyle Y(s) \end{bmatrix}=
\frac{-1}{3s(s+2)}\begin{bmatrix}
-2s& -s\\\\ -s&s+3 \end{bmatrix}
\begin{bmatrix} \displaystyle\frac{2}{s} \\\\\\\\ \displaystyle\frac{-8}{s^2}+3 \end{bmatrix} =\frac{-1}{3s(s+2)}  \begin{bmatrix} \displaystyle-3s-4+\frac{8}{s} \\\\\\\\ \displaystyle 3s-\frac{8}{s}-\frac{24}{s^2}+7\end{bmatrix} .$$

Which leads to

$$\begin{cases}
\displaystyle X(s)=\frac{1}{s+2} +\frac{4}{3s(s+2)} -\frac{8}{3s^2(s+2)},   \\\\\\\\
 \displaystyle Y(s)=\frac{-1}{s+2} +\frac{8}{3s^2(s+2)} +\frac{8}{s^3(s+2)}-\frac{7}{3s(s+2)}.
\end{cases}$$

We notice that there are three inverse LTs to be computed, they can be
computed using the convolution theorem easily: We know that
$\mathcal{L}^{-1}\left\\{\frac{1}{s+2}\right\\}=e^{-2t}$, then

$$\mathcal{L}^{-1}\left\\{\frac{1}{s(s+2)}\right\\} =\int_0^t e^{-2r}\ dr =\frac{1-e^{-2t}}{2}$$

Again,

$$\mathcal{L}^{-1}\left\\{\frac{1}{s^2(s+2)}\right\\} =\int_0^t \frac{1-e^{-2r}}{2} dr =\frac{t}{2}-\frac{1-e^{-2t}}{4}$$

Again,

$$\mathcal{L}^{-1}\left\\{\frac{1}{s^3(s+2)}\right\\} =\int_0^t\frac{r}{2}-\frac{1-e^{-2r}}{4} dr =\frac{t^2}{4} -\frac{t}{4}+\frac{1-e^{-2t}}{8}$$

By putting everything together, you should get

$$\begin{cases}
 \displaystyle x(t)= \frac{4}{3}-\frac{4t}{3}-\frac{e^{-2t}}{3}, \\\\\\\\
  \displaystyle y(t) =2t^2-\frac{2t}{3}-\frac{e^{-2t}}{6} -\frac{5}{6}. 
\end{cases}$$

{{< /spoiler >}}

---

**Exercise:** Use Laplace transform to solve the following initial
value problem:
$$y''(t)+y(t)=\delta(t-2\pi)+\delta(t-4\pi), \qquad \qquad y(0)=1,\  y'(0)=0$$

{{< spoiler text="Solution" >}}


Apply LT to both sides and solve the equation for $Y(s)$ to get

$$Y(s)=\frac{s}{s^2+1} +\frac{e^{-2\pi s}}{s^2+1}+\frac{e^{-4\pi s}}{s^2+1}.$$
Apply the inverse LT to both sides (use the second translation theorem)
to get

$$y(t)=\cos(t) +\sin(t-2\pi) \mathscr{U}(t-2\pi) +\sin(t-4\pi) \mathscr{U}(t-4\pi).$$

**Note:** The above expression is equivalent to

$$y(t)=\cos(t) +\sin(t) \mathscr{U}(t-2\pi) +\sin(t) \mathscr{U}(t-4\pi).$$

{{< /spoiler >}}

---

**Exercise:** Let $a$ be a positive number, solve the following IVP

$$y'(t)=\delta(t-a),\qquad y(0)=0.$$

*Note:* This problem shows that the delta \"function\" is the
\"derivative\" of another function that we have studied this semester.

{{< spoiler text="Solution" >}}
 Apply LT to both sides

$$sY(s)=e^{-a s}$$
 divide by $s$ 
 $$Y(s)=\frac{1}{s} e^{-a s}$$

Apply the second translation theorem to get

$$y(t)=\mathscr{U}(t-a).$$
{{< /spoiler >}}
