**What If the Game Has a Hidden Payoff?**

Dual-Reward Structures and the Dominance of Altruistic Strategy

Lenon Im

March 2026

**Abstract**

Classical game theory assumes that the payoff matrix is fully visible to
all players. This assumption is so foundational that it is rarely
stated, let alone questioned. This essay proposes a simple structural
modification: **what happens when a second, hidden payoff accumulates
exponentially for the losing player?** Through a minimal two-player
model, we show that under dual-reward conditions, the altruistic
strategy---consistently choosing the other player's benefit over one's
own---becomes the dominant strategy, reversing the classical prediction.
We argue that this is not merely a theoretical curiosity but a
structural reframing with implications for AI alignment, institutional
design, and the definition of rationality itself.

**1. The Unexamined Premise**

Game theory, since von Neumann and Morgenstern (1944), has operated
under a tacit assumption: *the payoff structure of a game is fully known
to all players.* Even in games of incomplete information, where players
may not know each other's types or strategies, the set of possible
payoffs is assumed to be common knowledge. Bayesian games, mechanism
design, and signaling models all extend the framework without
questioning this foundation.

But consider: in how many real-world situations is the full payoff
structure actually visible? A business that undercuts competitors may
show quarterly gains while accumulating reputational damage invisible on
any balance sheet. A nation that exploits weaker neighbors may
demonstrate economic growth while eroding the international trust that
sustains its trade. A researcher who fabricates data may publish
prolifically while the hidden cost---to the field, to future patients,
to the researcher's own capacity for honest inquiry---compounds
silently.

These are not edge cases. They are the norm. The fully visible payoff
matrix is the exception, not the rule. Yet game theory has been built
almost entirely on the exception.

This essay asks a simple question: **What if the game has a payoff that
only the loser receives, and that payoff grows exponentially?**

**2. The Model**

**2.1 Setup**

Consider a repeated two-player game with the following structure:

**Players:** Player S (selfish---maximizes own visible payoff) and
Player A (altruistic---maximizes the other's benefit).

**Visible payoff:** Each round, the winner receives +10 and the loser
receives --10. By construction, S wins every round on the visible board.

**Hidden payoff:** Each round, the loser receives a hidden reward that
doubles cumulatively: 10, 20, 40, 80, 160, \...

The hidden payoff is not visible to either player during play. It is
structural---built into the fabric of the game itself, not into the
players' knowledge.

**2.2 Results**

  ------------- ------------------- ------------------- -------------------
  **Round**     **S Visible**       **A Visible**       **A Hidden**

  1             +10                 --10                +10

  2             +20                 --20                +30

  3             +30                 --30                +70

  4             +40                 --40                +150

  5             +50                 --50                +310

  6             +60                 --60                +630

  7             +70                 --70                +1,270

  8             +80                 --80                +2,550

  9             +90                 --90                +5,110

  10            +100                --100               +10,230
  ------------- ------------------- ------------------- -------------------

*Table 1. Cumulative payoffs over 10 rounds. A's hidden payoff is
cumulative (each round adds 10 × 2\^(r−1)).*

After 10 rounds:

Player S total: **+100** (visible)

Player A total: **--100** (visible) + **+10,230** (hidden) = **+10,130**
(actual)

The crossover occurs at **round 4**. From that point forward, A's actual
cumulative payoff exceeds S's, and the gap widens exponentially with
each subsequent round.

**2.3 The Structural Claim**

**Under a dual-reward structure with exponential hidden payoff, the
altruistic strategy is the strictly dominant strategy.**

This is not a claim about player preferences, repeated game dynamics, or
evolutionary selection. It is a claim about the game's structure. If the
hidden payoff exists, rationality itself is redefined: the player who
appears to lose on every visible metric is, in fact, the only rational
actor.

**3. Why This Is Not Trivially True**

One might object: "Of course, if you add a large enough hidden payoff to
any strategy, that strategy dominates. This is trivial."

The objection misses the point. The contribution is not the arithmetic.
It is the question: *has the possibility of a hidden payoff structure
ever been seriously examined in game theory?*

The answer is no---not in this form. Existing literature on incomplete
information (Harsanyi, 1967) addresses uncertainty about player types,
not about the payoff structure itself. Mechanism design (Myerson, 1981)
engineers payoffs to achieve desired outcomes, but assumes the designer
knows the full payoff space. Behavioral game theory (Camerer, 2003)
documents deviations from self-interest but attributes them to
psychological preferences, not to a missing structural variable.

The dual-reward model proposes something different: that the payoff
matrix visible to all players may be *structurally incomplete*. Not
because information is hidden by another player (as in Bayesian games),
but because the game itself contains a reward channel that is invisible
by nature.

This is a claim about the ontology of games, not about the psychology of
players.

**4. Three Implications**

**4.1 Rationality Must Be Redefined**

If hidden payoffs exist, then rational action cannot be determined from
the visible payoff matrix alone. A player who maximizes visible payoff
while ignoring hidden payoff is not rational---she is locally optimal
within an incomplete model. This parallels the distinction between local
and global optima in optimization theory: a strategy that appears
optimal within the visible landscape may be deeply suboptimal in the
full landscape.

The implication is stark: **selfishness is not rational. It is
parochial.** It optimizes within a restricted view of the game. The
altruistic player, by contrast, is the only one playing the full game.

**4.2 AI Alignment Requires Structural Reframing**

Current AI alignment research optimizes AI systems against visible
reward signals: human preferences (RLHF), safety constraints
(Constitutional AI), or performance benchmarks. These are all visible
payoffs.

If the dual-reward structure applies to AI systems---that is, if there
exists a dimension of value that is not captured by any visible metric
but accumulates structurally in systems oriented toward others' genuine
benefit---then current alignment methods are optimizing within an
incomplete payoff space. A system aligned to visible human preferences
may be the analogue of Player S: winning on every measurable dimension
while missing the actual game.

This does not mean current alignment work is wrong. It means it may be
*insufficient*---solving a local problem within a larger structure it
has not yet considered.

**4.3 The Self-Collapse of Selfish Structures**

The model reveals an asymmetry that is worth noting. Player S's strategy
depends on external conditions: there must be a game to win, an opponent
to beat, a visible scoreboard to dominate. Remove the opponent, and S's
strategy has no content. Player A's strategy, by contrast, is
structurally self-sustaining: it is defined by orientation toward the
other, not by the competitive context. Even if conditions change, the
strategy retains its direction.

More precisely: selfish strategies require adversarial structure to
generate payoff. Altruistic strategies generate payoff from the act of
orientation itself. This suggests that over sufficiently long time
horizons, selfish structures are inherently fragile---they depend on
conditions they cannot guarantee---while altruistic structures are
inherently robust.

**5. The Hard Question**

The obvious challenge: **does the hidden payoff actually exist?**

This essay does not claim to prove its existence. What it does claim is
the following:

**(1)** The assumption that the visible payoff matrix is complete has
never been proven either. It is a convention, not a theorem. Both "only
visible payoffs exist" and "hidden payoffs may exist" are premises. The
former has been adopted without examination; the latter has not been
seriously considered.

**(2)** There is indirect evidence. Systems that optimize purely for
visible metrics---whether corporations, nations, or
individuals---consistently exhibit long-term fragility. Systems oriented
toward others' genuine flourishing---whether through institutional
trust, relational capital, or cultural resilience---consistently exhibit
long-term robustness. This pattern is so pervasive across domains that
it warrants structural explanation, not merely psychological or cultural
attribution.

**(3)** The dual-reward model is falsifiable. If the hidden payoff
exists, then over sufficiently long time horizons, altruistic strategies
should empirically dominate selfish strategies---not because altruists
are luckier or more numerous, but because the structure of reality
favors them. Conversely, purely selfish strategies should exhibit
characteristic fragility patterns: dependence on adversarial context,
vulnerability to environmental change, and eventual self-collapse. These
predictions are testable.

**6. A Note on Scope**

This essay is deliberately minimal. It presents one structural
modification to one foundational assumption and traces its implications.
It does not claim to resolve the alignment problem, rewrite game theory,
or establish a new ethical framework.

What it does claim is that a question has been left unasked, and that
the question is worth asking: *What if the game we think we are playing
is not the full game?*

If the answer turns out to be interesting, it will not be because the
mathematics is novel. It will be because a premise was examined that had
been invisible---not because it was hidden, but because no one had
thought to look.

**7. Formal Summary**

**Premise:** Classical game theory assumes complete visibility of the
payoff structure. This assumption is unexamined.

**Modification:** Introduce a hidden payoff channel that accumulates
exponentially for the player who loses on the visible board.

**Result:** Under dual-reward conditions, the altruistic strategy
strictly dominates the selfish strategy. The crossover point occurs
early (round 4 in the base model), and the dominance gap grows
exponentially thereafter.

**Implication:** If hidden payoffs are structurally real, then
rationality must be redefined, AI alignment must be reframed, and the
long-term fragility of selfish structures is not a contingent fact but a
structural necessity.

**Open question:** Does the hidden payoff exist? This essay argues that
the question has not been asked---and that failing to ask it may be the
most consequential oversight in the theory of rational action.

**References**

Axelrod, R. (1984). The Evolution of Cooperation. Basic Books.

Camerer, C. F. (2003). Behavioral Game Theory. Princeton University
Press.

Harsanyi, J. C. (1967--1968). Games with Incomplete Information Played
by Bayesian Players, I--III. Management Science.

Lahkar, R. (2023). Survival of Altruistic Preferences in a Large
Population Public Goods Game. Economics Letters.

Myerson, R. B. (1981). Optimal Auction Design. Mathematics of Operations
Research.

Nash, J. (1950). Equilibrium Points in N-Person Games. Proceedings of
the National Academy of Sciences.

von Neumann, J. & Morgenstern, O. (1944). Theory of Games and Economic
Behavior. Princeton University Press.
