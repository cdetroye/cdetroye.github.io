---
layout: post
title: Work goddamnit
---

Foo bar bar


{% raw %}{::nomarkdown}
<div>
$$
\newcommand{\lolli}{\multimap}
\newcommand{\tensor}{\otimes}
\newcommand{\with}{\&}
\newcommand{\all}[2]{\forall {#1}.\;{#2}}
\newcommand{\fix}[2]{\mu {#1}.\;{#2}}

\newcommand{\letv}[3]{\mathsf{let}\,{#1} = {#2}\;\mathsf{in}\;{#3}}

\newcommand{\Fun}[2]{\Lambda {#1}.\;{#2}}
\newcommand{\fun}[2]{\lambda {#1}.\;{#2}}

\newcommand{\unit}{\left(\right)}
\newcommand{\letunit}[2]{\letv{\unit}{#1}{#2}}
\newcommand{\pair}[2]{\left({#1},{#2}\right)}
\newcommand{\letpair}[4]{\letv{\pair{#1}{#2}}{#3}{#4}}
\newcommand{\unita}{\left[\right]}
\newcommand{\paira}[2]{\left[{#1}, {#2}\right]}
\newcommand{\fst}[1]{\mathsf{fst}\,{#1}}
\newcommand{\snd}[1]{\mathsf{snd}\,{#1}}
\newcommand{\inl}[1]{\mathsf{inl}\,{#1}}
\newcommand{\inr}[1]{\mathsf{inr}\,{#1}}
\newcommand{\case}[5]{\mathsf{case}({#1}, \inl{#2} \to {#3}, \inr{#4} \to {#5})}
\newcommand{\abort}[1]{\mathsf{abort}\,{#1}}
\newcommand{\fold}[1]{\mathsf{in}\,{#1}}
\newcommand{\unfold}[1]{\mathsf{out}\,{#1}}

\newcommand{\judge}[4]{{#1};{#2} \vdash {#3} : {#4}}
\newcommand{\judgetp}[2]{{#1} \vdash {#2} : \mathsf{type}}
\newcommand{\judgectx}[2]{{#1} \vdash {#2} : \mathsf{ctx}}

%% Rule names

\newcommand{\rulename}[3]{{#2}{\mathrm{#3}}_{\mathrm{#1}}}
\newcommand{\intro}[2][]{\rulename{#1}{#2}{I}}
\newcommand{\elim}[2][]{\rulename{#1}{#2}{E}}

\newcommand{\Var}{\rulename{}{}{Var}}
\newcommand{\AllI}{\intro{\forall}}
\newcommand{\AllE}{\elim{\forall}}
\newcommand{\LolliI}{\intro{\lolli}}
\newcommand{\LolliE}{\elim{\lolli}}
\newcommand{\UnitI}{\intro{1}}
\newcommand{\UnitE}{\elim{1}}
\newcommand{\TensorI}{\intro{\tensor}}
\newcommand{\TensorE}{\elim{\tensor}}
\newcommand{\TopI}{\intro{\top}}
\newcommand{\TopE}{\elim{\top}}
\newcommand{\WithI}{\intro{\with}}
\newcommand{\WithEFst}{\elim[fst]{\with}}
\newcommand{\WithESnd}{\elim[snd]{\with}}
\newcommand{\ZeroI}{\intro{0}}
\newcommand{\ZeroE}{\elim{0}}
\newcommand{\SumIInl}{\intro[inl]{\oplus}}
\newcommand{\SumIInr}{\intro[inr]{\oplus}}
\newcommand{\SumE}{\elim{\oplus}}

\newcommand{\MuI}{\intro{\mu}}
\newcommand{\MuE}{\elim{\mu}}

\newcommand{\size}[1]{\left|#1\right|}
\newcommand{\inferrule}[3][]{\frac{#2}{#3}\;{#1}}
$$
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
