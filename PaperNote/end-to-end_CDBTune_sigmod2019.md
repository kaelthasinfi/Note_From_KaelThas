
<h4>
   Background
</h4>

DBMS configuration Tuning Method:
$\textbf{a)}$**Search-based methods**:1.Restart processing whenever a new request comes.
$\quad$ 2.Fail to utilize knowledge gained from  previous tuning effort.
$\textbf{b)}$**Learing-based methods**:OtterTune as an example.
$\quad$ Disadvantage:1.It cannot optimize the performance in an end-to-end manner.
$\quad$ 2.hard to reproduce all the conditions and accumulate high-quality samples.
$\quad$ 3.Regression methods is naive.
$\quad$ 4.Hardware configuration is not fixed.


<h4>
   Contribution
</h4>

$\textbf{1}$:End-to-end with deep RL
$\textbf{2}$:adopt a try-and-error manner in RL
$\textbf{3}$:design an effective reward funciton which enables end-to-end manner and accelerates the convergence speed of model.
$\textbf{4}$:utilize deep deterministic policy gradient.