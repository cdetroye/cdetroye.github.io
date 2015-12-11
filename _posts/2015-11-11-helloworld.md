---
layout: post
title: Work goddamnit
---

Foo bar bar


{% raw %}{::nomarkdown}
<div>
$$
\boxed{\judge{\Delta}{\Gamma}{e}{A}}
\\
\inferrule[\Var]
          { }
          {\judge{\Delta}{x:A}{x}{A}}
\\
\begin{array}{cc}
\inferrule[\AllI]
          {\judge{\Delta, \alpha}{\Gamma}{e}{A}}
          {\judge{\Delta}{\Gamma}{\Fun{\alpha}{e}}{\all{\alpha}{A}}}
& 
\inferrule[\AllE]
          {\judge{\Delta}{\Gamma}{e}{\all{\alpha}{B}} \\
           \judgetp{\Delta}{A}}
          {\judge{\Delta}{\Gamma}{e\;A}{[A/\alpha]B}}
\\[2em]
\inferrule[\LolliI]
          {\judge{\Delta}{\Gamma, x:A}{e}{B}}
          {\judge{\Delta}{\Gamma}{\fun{x:A}{e}}{A \to B}}
& 
\inferrule[\LolliE]
          {\judge{\Delta}{\Gamma}{e}{A \to B} \\
           \judge{\Delta}{\Gamma'}{e'}{A}}
          {\judge{\Delta}{\Gamma,\Gamma'}{e\;e'}{B}}
\\[2em]
\inferrule[\UnitI]
          { }
          {\judge{\Delta}{\cdot}{\unit}{1}}
&
\inferrule[\UnitE]
          {\judge{\Delta}{\Gamma}{e}{1} \\
           \judge{\Delta}{\Gamma'}{e'}{C}}
          {\judge{\Delta}{\Gamma,\Gamma'}{\letunit{e}{e'}}{C}}
\\[2em]
\inferrule[\TensorI]
          {\judge{\Delta}{\Gamma}{e}{A} \\
           \judge{\Delta}{\Gamma'}{e'}{B} }
          {\judge{\Delta}{\Gamma,\Gamma'}{\pair{e}{e'}}{A \tensor B}}
&
\inferrule[\TensorE]
          {\judge{\Delta}{\Gamma}{e}{A \tensor B} \\\\
           \judge{\Delta}{\Gamma', x:A, y:B}{e'}{C}}
          {\judge{\Delta}{\Gamma,\Gamma'}{\letpair{x}{y}{e}{e'}}{C}}
\\[2em]
\inferrule[\TopI]
          { }
          {\judge{\Delta}{\Gamma}{\unita}{\top}}
&
\\[1em]
\inferrule[\WithI]
          {\judge{\Delta}{\Gamma}{e}{A} \\
           \judge{\Delta}{\Gamma}{e'}{B} }
          {\judge{\Delta}{\Gamma}{\paira{e}{e'}}{A \with B}}
&
\begin{array}{l}
\inferrule[\WithEFst]
          {\judge{\Delta}{\Gamma}{e}{A \with B}}
          {\judge{\Delta}{\Gamma}{\fst{e}}{A}}
\\[1em]
\inferrule[\WithESnd]
          {\judge{\Delta}{\Gamma}{e}{A \with B}}
          {\judge{\Delta}{\Gamma}{\snd{e}}{B}}
\end{array}
\\[3em]
\begin{array}{l}
\inferrule[\SumIInl]
          {\judge{\Delta}{\Gamma}{e}{A }}
          {\judge{\Delta}{\Gamma}{\inl{e}}{A \oplus B}}
\\[1em]
\inferrule[\SumIInr]
          {\judge{\Delta}{\Gamma}{e}{ B}}
          {\judge{\Delta}{\Gamma}{\inr{e}}{A \oplus B}}
\end{array}
&
\begin{array}{l}
\inferrule[\SumE]
          {\judge{\Delta}{\Gamma}{e}{A \oplus B} \\\\
           \judge{\Delta}{\Gamma', x:A}{e'}{C} \\\\
           \judge{\Delta}{\Gamma', y:B}{e''}{C} }
          {\judge{\Delta}{\Gamma, \Gamma'}{\case{e}{x}{e'}{y}{e''}}{C}}
\end{array}
\\[3em]
&
\inferrule[\ZeroE]
          {\judge{\Delta}{\Gamma}{e}{0}}
          {\judge{\Delta}{\Gamma}{\abort{e}}{C}}
\end{array}
$$
$$a^2 + b^2 = c^2$$
$$
  \begin{array}{lcl}
    (\Fun{\alpha}{e})\;A                    & \mapsto & [A/\alpha]e  \\ 
    (\fun{x:A}{e})\;e'                      & \mapsto & [e'/x]e \\ 
    \letv{\unit}{\unit}{e'}                 & \mapsto & e' \\
    \letv{\pair{x}{y}}{\pair{e_1}{e_2}}{e'} & \mapsto & [e_1/x, e_2/y]e' \\ 
    \fst{\paira{e}{e'}}                     & \mapsto & e \\
    \snd{\paira{e}{e'}}                     & \mapsto & e' \\
    \case{\inl{e}}{x}{e'}{y}{e''}           & \mapsto & [e/x]e' \\ 
    \case{\inr{e}}{x}{e'}{y}{e''}           & \mapsto & [e/y]e'' \\ 
  \end{array}
$$
</div>
{:/}{% endraw %}

The end.
