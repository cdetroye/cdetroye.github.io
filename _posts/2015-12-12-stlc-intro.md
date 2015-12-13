---
layout: default
title: Operational Semantics of the STLC
---
{% include mathjax.html %}

$$
\inferrule [Right=T-If]
    {\inferrule[Right=T-False]
         { }
         {\texttt{false} : Bool} \\ \qquad \inferrule[T-Succ]
                                                {\inferrule[T-Pred]
                                                {\inferrule[T-Zero]
                                                    {}
                                                    {\texttt{0}:Nat}} {pred\:\texttt{0} : Nat} } {succ(pred\:
    \texttt{0})} \\ \qquad \inferrule[Right=T-Zero] { } {\texttt{0}:
    Nat} } {if\:\texttt{false}\:then\:\texttt{succ(pred
    0)}\:else\:\texttt{0} :Nat}

$$
