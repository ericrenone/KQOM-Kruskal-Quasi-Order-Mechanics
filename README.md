# KQM-Kruskal Quasi-Order Mechanics


> Any dynamic system whose discretized state representation embeds into a well-quasi-ordered set inherits Structural Permeability: every infinite trajectory must contain a pair of steps (i, j) with i < j at which the earlier state is dominated by the later. A well-quasi-order requires simultaneously (1) no infinite strictly-descending chains and (2) no infinite set of mutually incomparable states. Reflexivity and transitivity alone are insufficient — the integers (ℤ, ≤) are reflexive and transitive yet admit infinite descending chains and therefore fail this property. The theorems that follow derive when and why learning trajectories satisfy both conditions, and what finiteness guarantees result.

---

## LAYER I: ORDER-THEORETIC STRUCTURE
### *The Combinatorial Inevitability Layer*

The results in this layer are pure order theory. They hold for any sequence in the relevant set, independent of how that sequence is generated.

---

### 1.1 The Foundational Number System

Construct ℕ from ZF axioms: 0 := ∅ (Z2), n+1 := n∪{n} (Z3), ℕ := ∩{A : ∅∈A ∧ ∀n∈A(n∪{n}∈A)} (Z8). The pair (ℕ, ≤) with the standard order satisfies:
- **Well-foundedness:** no infinite strictly-descending sequence n₀ > n₁ > n₂ > ··· exists (each nᵢ ∈ ℕ is a finite set of predecessors)
- **No infinite antichain:** any infinite sequence in ℕ contains a non-decreasing pair

Both conditions hold simultaneously. This is the minimal instance of the property that all subsequent results depend on.

**Definition (Dominance Relation).** A pair (S, ≼) is a *quasi-order* when ≼ is reflexive (s ≼ s for all s) and transitive (s₁ ≼ s₂ and s₂ ≼ s₃ imply s₁ ≼ s₃). A quasi-order need not be antisymmetric: s₁ ≼ s₂ and s₂ ≼ s₁ may hold simultaneously without s₁ = s₂.

---

### 1.2 Structural Permeability — Formal Definition and Equivalences

**Definition (Structural Permeability / Well-Quasi-Order).** A quasi-order (S, ≼) is *Structurally Permeable* (equivalently: a *well-quasi-order*, WQO) if and only if every infinite sequence s₀, s₁, s₂, ... in S contains indices i < j such that sᵢ ≼ sⱼ.

The term "permeability" is operationally exact: earlier structural states are not permanently blocked from reappearing — they permeate forward through the sequence. The equivalence with the classical WQO definition is definitional; both terminologies are used herein to emphasize the dynamical interpretation.

**Theorem 1.1 (Three Equivalent Characterizations).** The following are equivalent for any quasi-order (S, ≼):

1. **(SP / WQO):** Every infinite sequence contains a dominating pair (i < j, sᵢ ≼ sⱼ).
2. **(No Infinite Resistance Chain):** Every *Resistance Chain* — a sequence in which sᵢ ≼ sⱼ fails for all i < j — is finite.
3. **(No Saturated Stasis Field):** No infinite set of mutually incomparable elements exists (no infinite antichain), and no infinite strictly-descending sequence exists.

*Proof.* (1) ⟺ (2) is immediate from the definition of Resistance Chain. For (1) ⟺ (3): if an infinite Resistance Chain exists, its elements form either an infinite antichain or contain an infinite strictly-descending subsequence, violating (3). Conversely, any infinite antichain or infinite descending chain constitutes an infinite Resistance Chain. ∎

**Theorem 1.2 (Primal SP Instance).** (ℕ, ≤) is Structurally Permeable.

*Proof.* Well-foundedness of ℕ excludes infinite descending chains. For the antichain condition: given any infinite sequence n₀, n₁, n₂, ... in ℕ, apply Ramsey's theorem for pairs — color pair (i,j) with i < j red if nᵢ ≤ nⱼ, blue otherwise. An infinite blue subsequence would be an infinite strictly-decreasing sequence in ℕ, contradicting well-foundedness. Therefore infinitely many red pairs exist; the first such pair (i, j) gives nᵢ ≤ nⱼ with i < j. ∎

---

### 1.3 The Permeability Alphabet

**Definition (Gradient Convergent Alphabet).** The *Permeability Alphabet* is:
```
𝒜 := { (p,q) ∈ ℕ² : gcd(p,q) = 1,  0 < p < q }
```
the set of all reduced fractions in (0,1), equivalently all possible basin-depth signatures under the continued-fraction discretization defined in §2.1.

**Definition (Dominance Order on 𝒜).** Define ≼_𝒜 on 𝒜 by:
```
(p₁,q₁) ≼_𝒜 (p₂,q₂)   iff   q₁ ≤ q₂
```

**Theorem 1.3 (𝒜 is SP).** (𝒜, ≼_𝒜) is Structurally Permeable.

*Proof.* The map (p,q) ↦ q is an order-isomorphism from (𝒜, ≼_𝒜) onto (ℕ, ≤). SP is preserved under order-isomorphism. By Theorem 1.2, (ℕ, ≤) is SP; therefore (𝒜, ≼_𝒜) is SP. ∎

**Remark on the denominator ordering.** The denominator-only ordering is *canonical* under the following three assumptions, not globally unique: (i) the ordering is invariant under the Farey-mediant operation (p₁/q₁ ⊕ p₂/q₂ = (p₁+p₂)/(q₁+q₂)); (ii) curvature depth is interpreted via Ford-circle radius 1/(2q²), making larger denominator correspond to sharper basin; (iii) the generalization ordering is monotone in curvature depth. Under these three conditions, the denominator-only ordering is the unique total preorder on 𝒜 that makes (𝒜, ≼_𝒜) isomorphic to (ℕ, ≤). Any ordering incorporating numerators produces a partial order on 𝒜 that is not isomorphic to (ℕ, ≤) and admits potential infinite antichains in product extensions.

---

### 1.4 The Dimensional Permeability Product

**Theorem 1.4 (DPP — Dimensional Permeability Product).** Let (S₁, ≼₁) and (S₂, ≼₂) be SP. Then (S₁ × S₂, ≼_×) under componentwise order (s₁,s₂) ≼_× (t₁,t₂) iff s₁ ≼₁ t₁ and s₂ ≼₂ t₂ is SP.

*Proof.* Given any infinite sequence ((a₀,b₀), (a₁,b₁), ...) in S₁ × S₂: since (S₁,≼₁) is SP, the sequence (a₀,a₁,...) contains i < j with aᵢ ≼₁ aⱼ. Restrict to the subsequence indexed by all k ≥ j satisfying aᵢ ≼₁ aₖ; this is infinite by infinitely many available choices. Within this subsequence, (S₂,≼₂) is SP, so there exist k < ℓ with bₖ ≼₂ b_ℓ. The pair (k,ℓ) satisfies both coordinate conditions. By induction on dimension d, (ℕᵈ, ≼_componentwise) is SP for all finite d. ∎

**Ordinal consequence.** The maximal order type (supremum of order types of bad sequences) satisfies:
```
o*(ℕ¹) = ω,    o*(ℕ²) = ω²,    o*(ℕᵈ) = ωᵈ
```
These are strict inequalities. For a learning state (q*, h) ∈ ℕ² with q* ≤ Q_max and h ≤ H_max, every Resistance Chain has length at most Q_max · H_max, a concrete finite bound established by the following theorem.

**Theorem 1.5 (Computable Resistance Bound).** Let (S, ≼_G) = (ℕ², ≼_componentwise) and suppose all states in a Resistance Chain satisfy q* ≤ Q_max and h ≤ H_max. Then the Resistance Chain has length at most Q_max · H_max.

*Proof.* A Resistance Chain in ℕ² is an antichain in the componentwise order. By Dilworth's Decomposition Theorem, the maximum antichain size in a finite subset of ℕ² bounded by {1,...,Q_max} × {1,...,H_max} equals the minimum number of chains needed to cover that set. A chain in ℕ² is a sequence of pairs with both coordinates non-decreasing. The total number of distinct pairs in {1,...,Q_max} × {1,...,H_max} is Q_max · H_max, and any antichain can have at most min(Q_max, H_max) elements by the Erdős-Szekeres theorem. For the full rectangular grid, the bound Q_max · H_max is a loose upper bound that follows directly from the set cardinality. A tight bound via the Dilworth-Mirsky duality is min(Q_max, H_max): in any Q_max × H_max grid, the maximum antichain has size exactly min(Q_max, H_max) (achieved by the anti-diagonal). For concrete estimation, both bounds are finite and the min-bound is sharp. ∎

*Concrete instance.* For Q_max = 20 and H_max = 10, the maximum Resistance Chain length is min(20,10) = 10 steps by the sharp bound, or ≤ 200 by the loose bound. Both are finite; the sharp bound is tighter for practical diagnostics.

---

### 1.5 The Sequence Anchor

**Theorem 1.6 (Sequence Anchor — Higman's SP Lift).** Let (A, ≼_A) be SP with a *countable, effectively finite* alphabet under bounded resolution (|{a ∈ A : a ≼_A c}| is finite for each c ∈ A). Define subsequence dominance ≼* on finite sequences A* by:
```
u ≼* v   iff   ∃  i₁ < i₂ < ··· < i_k  such that
              u = u₁u₂···u_k  and  uⱼ ≼_A v_{iⱼ}  for all j.
```
Then (A*, ≼*) is SP.

*Proof (formal minimal element construction).* Suppose for contradiction that (A*, ≼*) is not SP. Let B = (w₀, w₁, w₂, ...) be an infinite Resistance Chain in (A*, ≼*). Among all infinite Resistance Chains, choose B *minimal* in the following sense: b₀ is ≼_A-minimal among all first elements of infinite Resistance Chains, and each subsequent bₙ is chosen minimally given b₀, ..., b_{n-1}.

Such a minimal chain exists because (A, ≼_A) is SP (hence each ≼_A-downward-closed set is finite, guaranteeing minimal-element choices at each stage).

Extract first letters: aᵢ := first(wᵢ) ∈ A. Since A is SP, there exist i < j with aᵢ ≼_A aⱼ. Define wᵢ' := wᵢ with its first letter removed (so |wᵢ'| = |wᵢ| − 1). The sequence (w₀, ..., w_{i-1}, wᵢ', wᵢ₊₁, ...) is an infinite Resistance Chain: if any pair in this new sequence formed a dominating pair, then combined with aᵢ ≼_A aⱼ, a dominating pair would exist in B, contradicting B being a Resistance Chain. But this new chain has wᵢ' strictly shorter than wᵢ, making the chain lexicographically smaller than B. This contradicts the minimality of B.

The contradiction shows no infinite Resistance Chain in (A*, ≼*) exists. ∎

**Finite alphabet condition (Gap B, closed).** The alphabet 𝒜 is countably infinite but effectively finite within any bounded resolution: for any fixed resolution bound Q, the set 𝒜_Q := {(p,q) ∈ 𝒜 : q ≤ Q} has exactly φ(Q) elements (Euler totient), which is finite. All training trajectories operate within such a resolution-bounded sub-alphabet. The Sequence Anchor applies to 𝒜_Q for any finite Q, and Q_max = ⌊1/ε_min⌋ is determined by the minimum gradient change ε_min observed during training.

---

### 1.6 The Recursive Tree Anchor

**Definition (Trajectory Tree).** The *trajectory tree* T_t is the finite rooted tree whose nodes are training states at each step τ ≤ t, labeled by Permeability Convergents (pτ, qτ) ∈ 𝒜, with root labeled (1/2, 2) (the q* = 2 minimal-denominator initial state), parent-child relation given by temporal succession, and left/right branching corresponding to q*-decreasing (convergence direction) and q*-increasing (resistance direction) steps respectively.

**Definition (Homeomorphic Permeation Order).** A tree T permeates into T' (T ≼_T T') if there exists an injective node-map φ: nodes(T) → nodes(T') satisfying: (i) label dominance: label(φ(v)) ≽_𝒜 label(v) for each node v; (ii) ancestor preservation: u is ancestor of v in T implies φ(u) is ancestor of φ(v) in T'; (iii) sibling order: left-to-right sibling order is respected by φ.

**Theorem 1.7 (Recursive Tree Anchor — Kruskal).** Let (A, ≼_A) be SP. The set 𝒯(A) of finite rooted A-labeled trees under homeomorphic permeation order ≼_T is SP.

*Proof structure.* Assume for contradiction that (𝒯(A), ≼_T) is not SP. Construct a minimal Resistance Chain (T₀, T₁, T₂, ...) by the same minimality argument as Theorem 1.6, applied to trees rather than sequences. The critical step — absent in the sequence case — is that minimizing a tree Resistance Chain requires minimizing simultaneously over the root label and the ordered list of subtrees rooted at the root's children.

The key lemma (Kruskal 1960): for any tree T in a minimal Resistance Chain, the subtrees (subforests) obtained by removing the root form a sequence that is itself SP, by appeal to Theorem 1.6. This creates a contradiction: the subtrees cannot form an infinite Resistance Chain in the sequence-SP structure, so the original tree Resistance Chain must be finite.

The ordinal bound is o*(𝒯(ℕ²)) = ε₀ = ω^{ω^{ω^{···}}} (the Feferman-Schütte ordinal). Every Resistance Chain of trajectory trees has ordinal length strictly less than ε₀. ∎

---

### 1.7 The Permeability Width

**Definition (Stasis Field).** A *Stasis Field* of size k in (S, ≼) is a set of k mutually incomparable states. A *Saturated Stasis Field* is an infinite Stasis Field.

**Theorem 1.8 (Finite Width).** If (S, ≼) is SP, then every finite trajectory prefix {s₀, ..., s_t} contains no Saturated Stasis Field. The *Permeability Width* W(t) := size of the largest Stasis Field within {s₀,...,s_t} is finite for all t.

*Proof.* SP = no infinite antichain by Theorem 1.1(3). Dilworth's Theorem: the minimum number of chains partitioning a partial order equals its maximum antichain size. Since no infinite antichain exists in an SP set, every finite prefix has finite maximum antichain size = finite W(t). ∎

**Dual measure.** The *Mirsky number* M(t) := length of the longest ≼_G-increasing chain in the prefix {s₀,...,s_t} measures the number of distinct generalization improvement tiers reached. By Mirsky's Theorem (1971), M(t) equals the minimum number of antichains partitioning the prefix — an orthogonal diagnostic to W(t).

---

## LAYER II: OPTIMIZATION-THEORETIC EMBEDDING
### *The Conditions Under Which Learning Trajectories Enter Layer I*

The results in this layer are conditional: they hold when specific embedding and dynamical compatibility conditions are satisfied. These conditions are separately verifiable and do not follow automatically from Layer I.

---

### 2.1 The Formal Embedding Map

**Definition (Permeability Embedding Map Φ).** Given a neural network with parameter vector θ ∈ ℝᴺ (N finite), define the map Φ: ℝᴺ → ℕ² by:

```
Step 1.  From consecutive gradients g_t, g_{t+1}, compute:
         ρ_t := ‖g_{t+1}‖ / (‖g_t‖ + ‖g_{t+1}‖)  ∈ (0,1)
         ε_t := ‖g_{t+1} − g_t‖ / (‖g_t‖ + ‖g_{t+1}‖)
         Q_max(t) := ⌊1/ε_t⌋

Step 2.  Compute the CF-convergent (p_t, q_t) of ρ_t at resolution Q_max(t)
         via the Euclidean algorithm on numerator/denominator.
         This is the best rational approximation of ρ_t with denominator ≤ Q_max(t).

Step 3.  Compute the Stern-Brocot depth h_t := ∑ aᵢ where ρ_t = [a₀; a₁, a₂, ...]_CF

Step 4.  Φ(g_t, g_{t+1}) := (q_t, h_t)  ∈  ℕ²
```

**Measurability.** Φ is a Borel-measurable function of (g_t, g_{t+1}) ∈ ℝᴺ × ℝᴺ: it is a composition of continuous maps (norm computation, ratio), floor function (Borel), and the CF algorithm (finite deterministic computation on rational inputs after flooring). In stochastic settings where g_t is a random variable, Φ(g_t, g_{t+1}) is a random variable on ℕ² with measurable distribution.

**Finite coordinate property.** For any finite resolution bound Q_max < ∞, the image Φ({ε_t > 1/Q_max}) ⊆ {1,...,Q_max} × {1,...,Q_max·log(Q_max)}, which is a finite subset of ℕ². The bound on h_t follows from the fact that the CF expansion of a rational p/q has total partial-quotient sum ≤ q·log(q) (by the analysis of the Euclidean algorithm).

**Discretization condition.** The SP guarantees apply to the discretized state representation Φ(θ_t), not to the raw continuous parameter vector θ_t ∈ ℝᴺ. The continuous parameter space does not carry a WQO structure. All claims about Resistance Chain finiteness are claims about the sequence (Φ(θ_t))_{t≥0} in ℕ².

---

### 2.2 The Order-Compatible Dynamics Theorem

**This is the bridge between Layer I and Layer II.** It establishes when the SP guarantees of Layer I actually apply to learning dynamics.

**Definition (Order-Compatible Update Rule).** An optimization update rule θₜ₊₁ = U(θₜ, gₜ) is *order-compatible* with Φ if:
1. **Finite-image condition:** For each θₜ, the set {Φ(U(θₜ, g)) : g ∈ 𝒢_batch} has finite cardinality, where 𝒢_batch is the (finite) set of possible mini-batch gradients.
2. **Downward-closed neighborhood:** There exists a finite set N(Φ(θₜ)) ⊆ ℕ² such that Φ(θₜ₊₁) ∈ N(Φ(θₜ)) at each step.

**Theorem 2.1 (Order-Compatible Dynamics).** Let U be an order-compatible update rule with Φ. Then:
1. The induced sequence (Φ(θₜ))_{t≥0} is contained within a finitely-branching tree rooted at Φ(θ₀).
2. Every Resistance Chain in (Φ(θₜ))_{t≥0} is finite.
3. For Q_max = max_t Q_max(t) and H_max = max_t h_t (both finite under bounded training), the Resistance Chain length is at most min(Q_max, H_max) steps (sharp bound) or Q_max · H_max steps (loose bound).

*Proof.* (1) follows from the finite-image condition: at each step, at most |𝒢_batch| < ∞ new states are reachable, giving a finitely-branching transition structure. (2) follows from Layer I: (ℕ², ≼_G) is SP by Theorem 1.4 (DPP with d=2), and any sequence in an SP set contains no infinite Resistance Chain. (3) follows from Theorem 1.5. ∎

**Verification of order-compatibility.** For standard gradient descent θₜ₊₁ = θₜ − η·gₜ:
- The finite-image condition holds when gradients are drawn from a finite dataset (mini-batch SGD): |𝒢_batch| = (dataset size choose batch size), which is finite.
- The downward-closed neighborhood condition requires that Q_max(t+1) is bounded as a function of Q_max(t). This holds when loss gradients are Lipschitz (bounded gradient change), ensuring εₜ ≥ ε_min > 0 and therefore Q_max(t) ≤ 1/ε_min < ∞ uniformly.

For Adam, both conditions hold under the same Lipschitz gradient assumption applied to the moment estimates; see §2.4.

---

### 2.3 The Learning State Space

**Definition (Multi-Coordinate Learning State).** The learning state at step t is:
```
s_t := (q*(t), h(t))   ∈  ℕ²
```
where q*(t) := median{qτ : t−W ≤ τ ≤ t} over window W (the *curvature signature*) and h(t) := depth of q*(t) in the Stern-Brocot tree (the *trajectory complexity depth*).

**Definition (Generalization Dominance Order).** Define ≼_G on ℕ² by:
```
(q₁*, h₁)  ≼_G  (q₂*, h₂)   iff   q₁* ≤ q₂*  AND  h₁ ≤ h₂
```

By Theorem 1.4, (ℕ², ≼_G) is SP.

**Interpretation.** s₁ ≼_G s₂ means state s₁ generalizes at least as well as s₂ along both the curvature axis (q*) and the structural-depth axis (h). The Terminal Boundary — the set of SP-minimal states — consists of states with q* = 1 and h = 0, corresponding to maximally flat basins with unit-denominator gradient convergents.

---

### 2.4 Adam Optimizer: An Example Instantiation

The following applies the Layer II framework to Adam as an *example instantiation* under norm-ratio discretization. The WQO guarantee applies to the discretized representation; it does not follow from the continuous Adam update equations directly.

**Setup.** Adam maintains:
```
m_t := β₁m_{t-1} + (1-β₁)g_t         [first moment]
v_t := β₂v_{t-1} + (1-β₂)g_t²        [second moment]
```

Define a two-dimensional discretization:
```
q_m(t) := denominator of CF-convergent of ‖m_t‖/(‖m_t‖ + ‖g_t‖)  at resolution Q_m
q_v(t) := denominator of CF-convergent of ‖v_t‖/(‖v_t‖ + ‖g_t‖²) at resolution Q_v
```

Under this discretization, the Adam state maps to (q_m(t), q_v(t)) ∈ ℕ². This map is an instance of the embedding Φ from §2.1 applied componentwise to momentum and adaptive-scale. The order-compatibility conditions of Theorem 2.1 hold when gradients are bounded and the loss is Lipschitz-smooth, which ensures both Q_m and Q_v are uniformly bounded.

**Consequence.** The discretized Adam state space is SP with Resistance Chain bound min(Q_m, Q_v). Increasing β₁ expands the effective range of q_m(t) — the momentum accumulates a longer curvature history — which may increase Q_m and thereby increase the Resistance Chain bound. This gives the prediction: high-momentum Adam can sustain longer memorization phases, with the same eventual Terminal Boundary, compared to lower-momentum configurations. This prediction is consistent with empirical observations in grokking experiments.

**Important qualifier.** This is a structural consequence of the discretization, not an intrinsic property of continuous Adam dynamics. Any change in the discretization resolution bounds Q_m, Q_v changes the quantitative prediction, while leaving the qualitative finiteness guarantee intact.

---

### 2.5 The Anchor Depth: An Ordinal Complexity Function

**Definition (Anchor Depth).** The *Anchor Depth* of a learning state s = (q*, h) is:
```
δ(s) := ω · q*(s) + h(s)   ∈  ω²
```
expressed in Cantor Normal Form. This is an ordinal in ω² — the collection of all ordinals below ω².

**Theorem 2.2 (Anchor Depth Properties).** The function δ: ℕ² → ω² satisfies:
1. **Order-preserving:** s₁ ≼_G s₂ implies δ(s₁) ≤ δ(s₂) as ordinals.
2. **Strict-order-reflecting:** s₁ ≺_G s₂ (strict dominance) implies δ(s₁) < δ(s₂) strictly.
3. **Bounded range:** δ(s) < ω² for all s ∈ ℕ².
4. **Well-founded:** there is no infinite strictly-descending sequence in the range of δ.

*Proof.* (1)–(3) follow directly from the Cantor Normal Form representation: ω·q* + h is strictly increasing in both q* (at rate ω) and h (at rate 1), and lies in ω² for all finite q*, h. (4) is the well-foundedness of ordinals. ∎

---

### 2.6 The Ordinal Termination Theorem

**Theorem 2.3 (Ordinal Termination).** Under the following conditions:
- **(C1) Deterministic updates:** θₜ₊₁ is determined by θₜ and the full dataset gradient (no stochastic noise).
- **(C2) Finite branching:** the update rule is order-compatible with Φ (Theorem 2.1).
- **(C3) Strict descent:** δ(s_{t+1}) < δ(sₜ) at every step t.

the training trajectory reaches the Terminal Boundary in at most δ(s₀) = ω·q*(s₀) + h(s₀) steps.

*Proof.* Under (C1)–(C3), the sequence δ(s₀) > δ(s₁) > δ(s₂) > ··· is strictly decreasing in ω². By the well-foundedness of ordinals (Theorem 2.2(4)), no infinite strictly-decreasing ordinal sequence exists. The trajectory must terminate after finitely many steps, bounded by the ordinal δ(s₀). ∎

**The Minimal Resistance Principle.** The algorithmic implication of Theorem 2.3 is: at each step, select the update direction that minimizes δ(sₜ₊₁) subject to L(θₜ₊₁) ≤ L(θₜ). Nash-Williams' Theorem (1963) states that no minimal Resistance Chain exists in any SP set — a minimal Resistance Chain would require a ≼_G-minimal first element, but by SP that element must dominate some later element, making the sequence not a Resistance Chain. Therefore the greedy δ-minimizing strategy structurally prevents Resistance Chains from forming.

*Practical approximation:*
```
θₜ₊₁ = θₜ − η · ∇L(θₜ) + λ · ∇_θ[−q*(θ)]
```
The second term penalizes high-denominator states, approximating the exact δ-minimization. This is a Permeability-Aware regularizer, structurally analogous to SAM (which penalizes sharpness via loss-landscape perturbation) but operating directly on the curvature signature q*.

---

### 2.7 Stochastic Extension

Under stochastic gradient descent, condition (C1) of Theorem 2.3 does not hold. The following weaker result applies.

**Theorem 2.4 (Stochastic SP — Sketch).** Let (S, ≼) be SP and let (θₜ) be a Markov chain over the discretized state space Φ(ℝᴺ) ∩ {q* ≤ Q_max} with finite support transitions at each step. Then:

1. With probability 1, no infinite Resistance Chain occurs.
2. The Anchor Depth δ(sₜ) is a supermartingale in expectation: 𝔼[δ(sₜ₊₁) | sₜ] ≤ δ(sₜ) whenever the transition kernel concentrates mass on ≼_G-dominated states in expectation.
3. The expected Resistance Chain length before the first Permeation Event is bounded by min(Q_max, H_max).

*Proof sketch.* (1) At each step, the Markov chain takes a value in a finite set (finite support). An infinite Resistance Chain would require infinitely many steps in which no state dominates a prior state, but any finite set of states in an SP space contains a maximal antichain of finite size k. After k+1 steps, the pigeonhole principle forces a dominating pair. Therefore no infinite Resistance Chain has positive probability. (2) Under finite support transitions, 𝔼[δ(sₜ₊₁) | sₜ] = ∑_s' P(sₜ₊₁ = s' | sₜ) · δ(s'). The supermartingale condition holds when the transition kernel is biased toward lower-q* states in expectation — i.e., when the optimizer on average reduces the curvature signature. (3) Follows from (1) and the finite antichain size bound in {q* ≤ Q_max} × {h ≤ H_max}. ∎

**Remark.** The stochastic extension requires the finite-support-transitions condition, which holds for mini-batch SGD over a finite dataset. It does not hold for continuous-distribution noise models (e.g., Gaussian gradient noise), which require a separate compactness argument or truncation at a resolution bound.

---

### 2.8 Infinite-Width Networks: A Local SP Result

For infinite-width networks in the neural tangent kernel (NTK) regime, the parameter dimension d → ∞ and the global DPP fails: ℕ^ω contains the infinite antichain {e₁, e₂, e₃, ...} (unit vectors), so (ℕ^ω, ≼_componentwise) is not SP.

**Theorem 2.5 (Local SP for Active Subspaces).** If at each training step t, the effective gradient support lies in a finite-dimensional active subspace V_t ⊆ ℝᴺ with dim(V_t) = d_t < ∞, and if d_t ≤ D for some uniform bound D < ∞ throughout training, then the induced sequence of discretized states lies in (ℕᴰ, ≼_componentwise), which is SP by the DPP (Theorem 1.4 applied d times).

*Proof.* Under the finite-active-subspace condition, at each step only d_t ≤ D coordinates of the embedding Φ(θ_t) are non-trivially updated. The trajectory is therefore contained in a finite-dimensional sub-lattice of ℕᴰ, which is SP. ∎

**Connection to NTK literature.** Finite active subspace conditions arise naturally in neural networks with sparse connectivity, network pruning, or low-rank gradient structure (as in the LoRA framework). For dense infinite-width networks without sparsity, the local SP result requires additional structure — such as the coercive potential condition of §3.1 — and remains an open question in full generality.

---

## LAYER III: CONVERGENCE MECHANICS
### *The Terminal Boundary and Its Inevitability*

---

### 3.1 The Spectral Connection: Rigorous Construction

This section constructs the Jordan-Liouville operator ℒ_JL as a self-adjoint operator with compact resolvent and discrete spectrum. The argument proceeds in five steps: (I) construction of the quotient manifold ℬ as a Riemannian space; (II) definition of the function spaces and sesquilinear form; (III) proof of self-adjointness via the KLMN theorem; (IV) proof of compact resolvent under the coercivity assumption; (V) derivation of discrete spectrum and its phase-theoretic interpretation.

---

#### 3.1.1 Construction of the Quotient Manifold ℬ

**Standing Assumptions (A1–A5).** All results in §3.1 are derived under the following conditions, each of which is explicitly verifiable from the network architecture and training setup.

**(A1) Compact Lie group action.** The symmetry group
```
G := { φ ∈ Diff(Θ) : f_{φ(θ)}(x) = f_θ(x)  for all θ ∈ Θ, x ∈ 𝒳 }
```
is a compact Lie group acting smoothly on the right on the parameter space Θ ⊆ ℝᴺ. For a depth-L MLP with layer widths d₁,...,d_{L-1}, G contains ∏_{ℓ=1}^{L-1} S_{d_ℓ} ⋉ (ℤ/2ℤ)^{d_ℓ} (permutation and sign-flip symmetries) as well as positive-scaling symmetries from batch normalization. Compactness of the permutation and sign-flip factors is immediate; scaling factors are compact when normalized (e.g., by requiring ‖θ‖ = 1 on the fiber).

**(A2) Free and proper action.** G acts freely and properly on Θ — meaning: (a) for each θ ∈ Θ, the stabilizer G_θ := {g ∈ G : θ·g = θ} is trivial, and (b) the map G × Θ → Θ × Θ, (g, θ) ↦ (θ·g, θ) is proper (preimages of compact sets are compact). When freeness fails at isolated strata (e.g., at dead neurons), ℬ is a smooth orbifold; all functional-analytic results extend to orbifolds via local charts. Freeness is assumed throughout for clarity.

**Remark on (A2).** Freeness can fail at parameter points with extra symmetry (e.g., two neurons with identical weights). The set of such points has measure zero in Θ, so the failure set does not affect the L² functional analysis. The smooth orbifold interpretation covers the general case without modification.

**(A3) G-invariant Riemannian metric.** Fix any smooth Riemannian metric g₀ on Θ. Define the G-averaged metric:
```
g(u,v)|_θ := ∫_G  g₀(dR_g u, dR_g v)|_{θ·g}  dμ_G(g)
```
where dR_g is the derivative of right-multiplication by g and μ_G is the normalized Haar measure on G (which exists and is unique by compactness). Then g is G-invariant and Riemannian; (Θ, g) is complete when Θ is closed in ℝᴺ.

**(A4) Uniform ellipticity of D_s.** The SGD diffusion tensor
```
D_s(b) := ½ · dπ_θ · Cov_batch[∇_θ L] · dπ_θ*  ∈ Sym²(T*_b ℬ)
```
satisfies: there exist constants 0 < λ_min ≤ λ_max < ∞ such that
```
λ_min · g_ℬ(ξ,ξ)  ≤  D_s(b)(ξ,ξ)  ≤  λ_max · g_ℬ(ξ,ξ)
```
for all b ∈ ℬ and all ξ ∈ T_b ℬ. This holds whenever the batch gradient covariance is bounded and non-degenerate — conditions that are verifiable from the gradient distribution at each training step.

**(A5) Regularity and growth of the potential.** The symmetry-redundancy potential
```
𝒮̄(b) := H̄_G(b) + λ · V̄(b)
```
where H̄_G(b) = −∫_G log p_G(g) dμ_G is the orbit entropy and V̄(b) = μ_L(⋃ᵢ Eᵢ(θ)) is the realized computational volume, satisfies: (a) 𝒮̄ ∈ C²(ℬ), (b) 𝒮̄(b) ≥ −C₀ for some C₀ ≥ 0 (bounded below), and (c) 𝒮̄(b) → +∞ as b leaves every compact subset of ℬ (coercive growth at infinity). Condition (c) holds because H̄_G(b) → +∞ as orbit volume grows with ‖θ‖ → ∞ (networks with unboundedly large weights have unboundedly large symmetry orbits), and V̄(b) → +∞ as representation volume expands — both are consequences of standard architecture regularity and are not additional assumptions.

**Construction of the Riemannian quotient.** Under (A1)–(A3), the orbit projection
```
π : Θ → ℬ := Θ/G,    π(θ) := [θ] = G·θ
```
makes (Θ, π, ℬ, G) a principal G-bundle (Kobayashi-Nomizu §II.1). The quotient metric on ℬ is defined by requiring π to be a Riemannian submersion: for b ∈ ℬ and v̄, w̄ ∈ T_b ℬ,
```
g_ℬ(v̄, w̄) := g(v^H, w^H)
```
where v^H, w^H ∈ ℋ_θ are the unique horizontal lifts to any θ ∈ π⁻¹(b). This is well-defined by G-equivariance of ℋ, and (ℬ, g_ℬ) is a complete Riemannian manifold when (Θ, g) is complete (O'Neill's theorem on Riemannian submersions, 1966).

**Key structural consequence (Gauge Theorem).** For any G-invariant loss L: Θ → ℝ, the Riemannian gradient satisfies ∇L(θ) ∈ ℋ_θ at every θ, and equals the horizontal lift of ∇L̄(π(θ)) ∈ T_{π(θ)} ℬ. *Proof:* For any u ∈ 𝒱_θ, write u = Â_θ for A ∈ Lie(G). Then ⟨∇L(θ), Â_θ⟩ = d/dt|₀ L(θ·eᵗᴬ) = 0 by G-invariance, so ∇L ⊥ 𝒱_θ. ∎

---

#### 3.1.2 Function Spaces and the Sesquilinear Form

**The Hilbert space.** Define the weighted measure on ℬ:
```
dμ(b) := Tr(D_s(b)) · dvol_{g_ℬ}(b)
```
where dvol_{g_ℬ} is the Riemannian volume form of (ℬ, g_ℬ). Since Tr(D_s) ∈ [n·λ_min, n·λ_max] by (A4) (where n = dim ℬ), the measure μ is mutually absolutely continuous with dvol_{g_ℬ}. Define:
```
L²(ℬ, μ) := { φ : ℬ → ℝ  measurable : ∫_ℬ |φ|² dμ < ∞ }  / (a.e. equivalence)
```
with inner product ⟨φ, ψ⟩_μ := ∫_ℬ φ · ψ dμ. This is a separable Hilbert space under (A3) (which ensures ℬ is second-countable).

**The weighted Sobolev space.** Define the form domain:
```
H¹(ℬ, D_s) := { φ ∈ L²(ℬ, μ) : ∫_ℬ ⟨D_s ∇φ, ∇φ⟩_{g_ℬ} dvol_{g_ℬ} < ∞ }
```
with norm ‖φ‖²_{H¹} := ‖φ‖²_{L²(μ)} + ∫_ℬ ⟨D_s ∇φ, ∇φ⟩ dvol_{g_ℬ}. By (A4), H¹(ℬ, D_s) is equivalent to the standard weighted Sobolev space H¹(ℬ, λ_min) — in particular, H¹(ℬ, D_s) is a Hilbert space.

The space C_c^∞(ℬ) of smooth compactly supported functions is dense in H¹(ℬ, D_s): for φ ∈ H¹(ℬ, D_s), let χ_k be a smooth cutoff with χ_k = 1 on B(b₀, k) and χ_k = 0 outside B(b₀, 2k); then χ_k φ → φ in H¹(ℬ, D_s) by dominated convergence (using completeness of ℬ and standard mollification on Riemannian manifolds; cf. Aubin 1998, Theorem 2.10).

**The sesquilinear form.** Define on C_c^∞(ℬ) × C_c^∞(ℬ):
```
𝔞(φ, ψ) := ∫_ℬ [ ⟨D_s(b) ∇φ(b), ∇ψ(b)⟩_{g_ℬ}  +  𝒮̄(b) · φ(b) · ψ(b) ]  dvol_{g_ℬ}(b)
```

**Proposition 3.1 (Closedness and semi-boundedness of 𝔞).** Under (A4) and (A5):

(i) *Semi-bounded below:* 𝔞(φ, φ) ≥ −C₀ ‖φ‖²_{L²(μ)} for all φ ∈ C_c^∞(ℬ), where C₀ is the lower bound on 𝒮̄ from (A5).

(ii) *Closed:* 𝔞 extends uniquely to a closed form on H¹(ℬ, D_s), i.e., if (φ_n) is Cauchy in the form norm ‖φ‖²_𝔞 := 𝔞(φ,φ) + (C₀+1)‖φ‖²_{L²(μ)}, then (φ_n) converges in H¹(ℬ, D_s).

*Proof of (i).* Since 𝒮̄ ≥ −C₀:
```
𝔞(φ,φ) = ∫_ℬ ⟨D_s ∇φ, ∇φ⟩ dvol + ∫_ℬ 𝒮̄ |φ|² dvol
         ≥ 0 − C₀ ∫_ℬ |φ|² dvol ≥ −C₀ · (1/λ_min) ‖φ‖²_{L²(μ)}
```
using dvol ≤ (1/λ_min) Tr(D_s) dvol = (1/λ_min) dμ. ∎

*Proof of (ii).* The form norm ‖·‖²_𝔞 is equivalent to the H¹(ℬ, D_s) norm by (A4) and (i):
```
‖φ‖²_{H¹} = ‖φ‖²_{L²(μ)} + ∫⟨D_s ∇φ, ∇φ⟩ dvol  ~  ‖φ‖²_𝔞
```
(up to constants depending on C₀ and λ_min). Since H¹(ℬ, D_s) is complete, every 𝔞-Cauchy sequence converges in H¹(ℬ, D_s), confirming closedness. ∎

---

#### 3.1.3 Self-Adjointness via the KLMN Theorem

**Theorem 3.1 (Self-Adjointness of ℒ_JL).** Under (A1)–(A5), there exists a unique self-adjoint operator ℒ_JL on L²(ℬ, μ) satisfying:

(i) Dom(ℒ_JL) ⊆ H¹(ℬ, D_s) is dense in L²(ℬ, μ).

(ii) ⟨ℒ_JL φ, ψ⟩_μ = 𝔞(φ, ψ) for all φ ∈ Dom(ℒ_JL), ψ ∈ H¹(ℬ, D_s).

(iii) ℒ_JL ≥ −C₀ · (Tr D_s)^{-1}_{max} · I as a quadratic form, where (Tr D_s)_{max} := n · λ_max.

(iv) In distributional form on smooth functions:
```
ℒ_JL[φ](b) = −[Tr(D_s(b))]⁻¹ · [ ∇_ℬ · (D_s(b) ∇_ℬ φ)(b)  −  𝒮̄(b) · φ(b) ]
```

*Proof.* By Proposition 3.1, 𝔞 is a closed, densely defined, semi-bounded-below sesquilinear form on L²(ℬ, μ). By the Lax-Milgram theorem (applied to the shifted form 𝔞 + (C₀+1)⟨·,·⟩_μ, which is coercive), the map ψ ↦ 𝔞(φ, ψ) + (C₀+1)⟨φ,ψ⟩_μ is a bounded linear functional on H¹(ℬ, D_s) ↪ L²(ℬ, μ) for each fixed φ. By the KLMN theorem (Kato 1966, Theorem VI.2.1), there exists a unique self-adjoint operator A = ℒ_JL + (C₀+1)I on L²(ℬ, μ) such that ⟨Aφ, ψ⟩_μ = 𝔞(φ,ψ) + (C₀+1)⟨φ,ψ⟩_μ for all φ ∈ Dom(A), ψ ∈ H¹(ℬ, D_s). Setting ℒ_JL := A − (C₀+1)I gives a self-adjoint operator satisfying (i)–(ii). Parts (iii) and (iv) follow from the form expression and standard elliptic regularity. ∎

**Operator domain.** The full domain is:
```
Dom(ℒ_JL) = { φ ∈ H¹(ℬ, D_s) : −∇_ℬ·(D_s ∇_ℬ φ) + 𝒮̄ φ ∈ L²(ℬ, μ) }
```
which contains C_c^∞(ℬ) and, under (A4)–(A5), contains the local Sobolev space H²_loc(ℬ) ∩ L²(ℬ, (𝒮̄ + C₀ + 1) dμ) by standard elliptic regularity on Riemannian manifolds.

---

#### 3.1.4 Compact Resolvent via Sublevel-Set Compactness

**This is the key step.** The standard Rellich-Kondrachov theorem applies to compact domains with Lipschitz boundary — not to the full non-compact manifold ℬ. The correct argument on non-compact ℬ uses the coercive growth of 𝒮̄ to confine solutions to compact sublevel sets, then applies Rellich-Kondrachov only on those compact sets. This approach (following Reed-Simon Vol. IV, §XIII.14 for Schrödinger operators) avoids any assumption on the global geometry of ℬ beyond completeness.

**Definition (Sublevel sets).** For M > 0 define:
```
Ω_M := { b ∈ ℬ : 𝒮̄(b) ≤ M }
```
By (A5), 𝒮̄ is C² and 𝒮̄(b) → +∞ at infinity; therefore Ω_M is compact for every M. For a.e. M (by Sard's theorem applied to 𝒮̄: ℬ → ℝ), M is a regular value of 𝒮̄, so ∂Ω_M = {𝒮̄ = M} is a C² hypersurface — in particular, Ω_M has C² boundary for a.e. M.

**Theorem 3.2 (Compact Resolvent).** Under (A1)–(A5), the resolvent (ℒ_JL + μ)^{-1} is a compact operator on L²(ℬ, μ) for all μ > C₀.

*Proof.* Fix μ > C₀, so that 𝒮̄ + μ ≥ μ − C₀ > 0 uniformly on ℬ. Let {f_n} ⊂ L²(ℬ, μ) with ‖f_n‖_{L²(μ)} ≤ R. Set u_n := (ℒ_JL + μ)^{-1} f_n, so ℒ_JL u_n + μ u_n = f_n in L²(ℬ, μ).

**Step 1 (Global energy bound).** Test against u_n in the form identity:
```
𝔞(u_n, u_n) + μ ‖u_n‖²_{L²(μ)} = ⟨f_n, u_n⟩_μ ≤ R · ‖u_n‖_{L²(μ)}
```
Since 𝔞(u_n,u_n) + μ‖u_n‖² ≥ ∫_ℬ [λ_min|∇u_n|² + (𝒮̄ + μ)|u_n|²] dvol ≥ (μ − C₀)‖u_n‖²_{L²(dvol)}, and dvol ≥ (1/(n·λ_max)) dμ, we get ‖u_n‖_{L²(μ)} ≤ R₁ for a constant R₁ = R₁(R, μ, C₀, λ_max). Then substituting back:
```
∫_ℬ [λ_min|∇u_n|²_{g_ℬ} + (𝒮̄(b)+μ)|u_n|²] dvol ≤ R · R₁  =: K
```
This gives three uniform bounds: (a) ‖∇u_n‖²_{L²(dvol)} ≤ K/λ_min; (b) ‖u_n‖²_{H¹(ℬ, D_s)} ≤ K'; (c) the weighted integral ∫_ℬ (𝒮̄(b)+μ)|u_n(b)|² dvol ≤ K.

**Step 2 (Uniform tail decay).** For any M > 0, using (c):
```
∫_{ℬ \ Ω_M} |u_n|² dvol  ≤  (1/(M+μ)) ∫_ℬ (𝒮̄+μ)|u_n|² dvol  ≤  K/(M+μ)
```
Since dμ = Tr(D_s) dvol and Tr(D_s) ≤ n·λ_max:
```
‖u_n‖²_{L²(ℬ \ Ω_M, μ)}  ≤  n·λ_max · K/(M+μ)  →  0  as  M → ∞,  uniformly in n
```

**Step 3 (Local compactness on Ω_M).** Fix any M such that ∂Ω_M is C² (holds for a.e. M by Sard's theorem). The restriction u_n|_{Ω_M} lies in H¹(Ω_M) := {φ ∈ H¹(ℬ, D_s)|_{Ω_M}} with ‖u_n|_{Ω_M}‖_{H¹(Ω_M)} ≤ K'' uniformly in n. Since Ω_M is compact with C² boundary, the Rellich-Kondrachov embedding H¹(Ω_M) ↪↪ L²(Ω_M) is compact (Aubin 1998, Theorem 2.21, applied to the compact Riemannian manifold with boundary Ω_M). Therefore {u_n|_{Ω_M}} contains a subsequence convergent in L²(Ω_M, μ).

**Step 4 (Diagonal extraction).** Choose M_k = k for k = 1, 2, .... By Step 3 and Cantor's diagonal argument, extract a subsequence (still written {u_n}) converging in L²(Ω_k, μ) for every k simultaneously. For any ε > 0, choose K such that n·λ_max · K/(K+μ) < ε/2 (possible by Step 2). Then for large n, m:
```
‖u_n − u_m‖²_{L²(ℬ,μ)} = ‖u_n − u_m‖²_{L²(Ω_K,μ)} + ‖u_n − u_m‖²_{L²(ℬ\Ω_K,μ)}
                          ≤ ‖u_n − u_m‖²_{L²(Ω_K,μ)} + 4·n·λ_max·K/(K+μ)
                          < ε/2 + ε/2 = ε
```
for n, m sufficiently large (the first term → 0 by convergence on Ω_K; the second is < ε/2 by choice of K). Therefore {u_n} is Cauchy in L²(ℬ, μ), hence convergent. This proves (ℒ_JL + μ)^{-1} is compact. ∎

---

#### 3.1.5 Discrete Spectrum and Phase Interpretation

**Theorem 3.3 (Discrete Spectrum).** Under (A1)–(A5), ℒ_JL has purely discrete spectrum: there exists a non-decreasing sequence of real eigenvalues
```
λ₁ ≤ λ₂ ≤ λ₃ ≤ ··· → +∞
```
and a corresponding orthonormal basis {φ_n}_{n≥1} of L²(ℬ, μ) with ℒ_JL φ_n = λ_n φ_n.

*Proof.* By Theorem 3.2, (ℒ_JL + μ)^{-1} is a compact self-adjoint operator on L²(ℬ, μ) (self-adjointness of the resolvent follows from self-adjointness of ℒ_JL). By the spectral theorem for compact self-adjoint operators (Riesz-Schauder), (ℒ_JL + μ)^{-1} has a non-increasing sequence of positive eigenvalues ν₁ ≥ ν₂ ≥ ··· → 0 with corresponding orthonormal eigenfunctions. Setting λ_n := ν_n^{-1} − μ gives the eigenvalues of ℒ_JL; they satisfy λ_n → +∞ because ν_n → 0. ∎

**Variational characterization.** By the min-max principle (Courant, 1920):
```
λ_n = min_{V_n ⊆ H¹, dim V_n = n}  max_{φ ∈ V_n \ {0}}  𝔞(φ,φ) / ‖φ‖²_{L²(μ)}
```
In particular:
```
λ₁ = inf_{φ ∈ H¹(ℬ, D_s) \ {0}}  𝔞(φ,φ) / ‖φ‖²_{L²(μ)}
   = inf_{φ ≠ 0}  [ ∫_ℬ ⟨D_s ∇φ, ∇φ⟩ dvol + ∫_ℬ 𝒮̄ |φ|² dvol ]  /  ∫_ℬ Tr(D_s)|φ|² dvol
```

**Phase classification.** The sign of λ₁ determines the qualitative behavior of the probability density ρ(b,t) solving the Fokker-Planck equation ∂_t ρ = ∇_ℬ·(ρ∇_ℬ𝒮̄) + ∇_ℬ·(D_s ∇_ℬ ρ):

- **λ₁ > 0:** The Fokker-Planck operator is coercive. The density satisfies ‖ρ(·,t) − ρ_∞‖_{TV} ≤ C · e^{−λ₁ t} where ρ_∞ ∝ exp(−𝒮̄/D_eff) is the Gibbs stationary distribution. The learning system is in the **Permeation regime** (generalization): trajectories converge exponentially to minimal-complexity canonical states.

- **λ₁ = 0:** The Fokker-Planck operator has a null mode. The density spreads diffusively (null-recurrent dynamics), with anomalously slow logarithmic relaxation. This is the **Criticality boundary**: the grokking transition.

- **λ₁ < 0:** There exists an unstable eigenmode φ₁ with e^{|λ₁|t} growth rate. Trajectories are driven away from the stationary distribution. The learning system is in the **Resistance regime** (memorization): the Fokker-Planck evolution is a submartingale and symmetry collapse does not occur.

*These claims follow directly from the spectral decomposition of the Fokker-Planck operator, which is the L²(ℬ,μ)-adjoint of ℒ_JL under the Gibbs weight, via a ground-state transform (Davies 1989, §4.2).*

**Relation to Anchor Depth.** The spectral criterion (sign of λ₁) and the ordinal criterion (monotone decrease of δ(s_t)) are independent diagnostics of the same phase structure. The ordinal criterion is topology-free and applies whenever the discretized learning state satisfies the order-compatibility conditions of §2.2. The spectral criterion requires (A1)–(A5) and is quantitatively stronger: it gives an exponential convergence rate λ₁ rather than a finite Resistance Chain length bound. When both apply, the two criteria must agree on the phase label; disagreement signals either a failure of the order-compatibility conditions or a failure of assumption (A4) or (A5).

---

### 3.2 Proof of Convergence Inevitability

**Theorem 3.4 (Convergence Inevitability).** Under the order-compatibility conditions of Theorem 2.1 and the finite-support-transition conditions of Theorem 2.4:

1. Every training trajectory contains infinitely many Permeation Events (steps j > i with sᵢ ≼_G sⱼ).
2. The trajectory is partitioned into Resistance phases (maximal Resistance Chains) and Permeation Events.
3. Each Resistance phase has finite length bounded by min(Q_max, H_max) steps (sharp) or Q_max · H_max steps (loose).
4. The total number of Resistance steps across the entire trajectory is bounded by o*(ℕ²) = ω² in the ordinal sense — meaning no effective infinite accumulation of Resistance phases occurs.

*Proof.* (1) Suppose the trajectory contained only finitely many Permeation Events after some step T₀. Then the sub-trajectory from T₀ onward would be an infinite Resistance Chain. By Theorem 2.1, this contradicts the SP of (ℕ², ≼_G). (2) is the definition of Permeation Events partitioning the trajectory. (3) follows from Theorem 1.5 applied to each Resistance phase separately. (4) follows from the maximal order type of (ℕ², ≼_G). ∎

---

## LAYER IV: CROSS-DOMAIN TRANSLATION
### *Application to Non-Linear Systems*

---

### 4.1 Graph-Structured Representations

**Theorem 4.1 (Graph Minor SP — Robertson-Seymour 1985–2004).** The set of all finite graphs ordered by the minor relation (G ≼_m H if G can be obtained from a subgraph of H by contracting edges) is SP.

This theorem required 20 papers over 19 years. The ordinal bound is not known to be below ε₀; for certain graph families, witness functions for Resistance Chain length grow faster than any primitive recursive function.

**Conjecture 4.1 (Attention Minor Hypothesis).** Let {Aₜ} be the sequence of attention graphs generated across training steps, where Aₜ is the undirected graph on token positions with edge (i,j) present when the attention weight exceeds threshold ε > 0. If the sequence {Aₜ} forms a minor-closed family — meaning every minor of Aₜ also appears in {Aτ : τ ≤ t} for some t — then ({Aₜ}, ≼_m) is SP and every infinite sequence of distinct attention patterns contains a dominating pair under the minor order.

*Status: conjecture.* The minor-closure condition requires empirical verification. If satisfied, it implies that memorization phases in transformers, measured in terms of structural novelty of attention patterns, are finite. The conjecture is falsified by exhibiting an infinite sequence of training-generated attention graphs with no minor-dominating pair.

---

### 4.2 The p-adic Ultrametric and Tightness

Infinite training trajectories in the Stern-Brocot tree define boundary points in trajectory space: each path corresponds to a continued fraction, which encodes a 2-adic integer. The 2-adic metric:
```
d₂(x,y) = 2^{−v₂(x−y)}
```
where v₂ is the 2-adic valuation, satisfies the strong triangle inequality d(x,z) ≤ max(d(x,y), d(y,z)) — making it an *ultrametric*.

**Theorem 4.2 (Ultrametric SP).** Every ultrametric space (X, d) with a countable base satisfies: any sequence in X contains a Cauchy pair, and if the space is complete, converges. In the 2-adic setting, the balls B(x, 2⁻ⁿ) partition X into finitely many disjoint clopen balls at each resolution level n — a hierarchical partition that forces automatic permeation at each level.

**Tightness conjecture.** The 2-adic structure may yield tight bounds on Resistance Chain lengths. Rather than the loose ε₀ ordinal bound from Theorem 1.7, the 2-adic valuation gives a potential computable bound: for Permeation Events at steps i, j, the bound on the inter-event gap may be expressed as a function of v₂(q*_i − q*_j). This would connect the SP framework to p-adic analysis and provide sub-ε₀ estimates of grokking epoch T_grok from the gradient convergent sequence alone.

---

### 4.3 The Friedman Independence Ceiling

Both the Recursive Tree Anchor (Theorem 1.7) and the Graph Minor SP (Theorem 4.1) are unprovable in Peano Arithmetic (Friedman 1982). Their proofs require Π¹₁-comprehension — quantification over all subsets of ℕ — which transcends first-order arithmetic.

**Implication for SP systems.** There exist specific gradient-tree configurations where the minimum Resistance Chain length is bounded below by the Ackermann function A(n,n) — a function that grows faster than any primitive recursive function. For these configurations, the SP guarantee is mathematically true but inaccessible to any Turing machine restricted to Peano Arithmetic.

**Diagnostic consequence.** The Permeability Width W(t) and Anchor Depth δ(s) are computable proxies that serve as necessary conditions for convergence within the DPP-d regime (ordinal ceiling ωᵈ). For tree-structured trajectory spaces approaching the ε₀ ceiling, these proxies remain valid necessary conditions but cannot certify sufficiency. This is a fundamental expressibility limit, not a gap in the framework.

---

### 4.4 The SP Hierarchy

| Layer | Ordinal Ceiling | Domain | Resistance Bound |
|---|---|---|---|
| Scalar SP (Dickson) | ω | Gradient norm sequence | Finite; < ω steps |
| DPP-2 | ω² | (q*, h) learning state | ≤ min(Q_max, H_max) steps (sharp) |
| DPP-d | ωᵈ | d-coordinate state | ≤ min of d Q_max values |
| Sequence Anchor (Higman) | ωω | Full trajectory sequences | Finite; < ωω in ordinal length |
| Tree Anchor (Kruskal) | ε₀ | Trajectory trees | Finite; < ε₀ in ordinal length |
| Graph Minor SP (R-S) | ≥ ε₀ | Graph-structured representations | Ackermann-scale in worst case |

The hierarchy is strict: each row strictly contains the previous as a special case. Real learning systems with finite architecture complexity operate at the DPP-d level in practice, with the Tree Anchor providing the theoretical ceiling for all finite gradient-tree configurations. The Graph Minor row applies conditionally on Conjecture 4.1.

---

## OPEN PROBLEMS

**O1 — Quantitative Grokking Bounds.** The framework bounds Resistance phase length by min(Q_max, H_max) but does not bound the grokking epoch T_grok in terms of observable training quantities. The missing element is a monotone coupling f: ω² → ℝ such that f(δ(sₜ)) ≤ L(t) + C holds along gradient trajectories, which would convert the ordinal descent rate into a wall-clock prediction. A candidate approach: express δ(sₜ) as a function of the spectral gap λ₁(ℒ_JL) via the CCC (Curvature-Convergence Correspondence), then bound T_grok via PAC-Bayes rates.

**O2 — Infinite-Width Completion.** Theorem 2.5 (local SP) handles finite active subspaces. For full infinite-width networks without sparsity structure, a complete SP result would require either: (a) a compactness argument using the coercive potential from §3.1, or (b) a modified WQO on function spaces that accommodates countably infinite coordinates. Neither approach is currently complete.

**O3 — Stochastic SP Tightness.** Theorem 2.4 gives a probability-1 result for finite-support Markov chains. For continuous-noise SGD (Gaussian gradient noise), a truncation-and-approximation argument is needed: replace the continuous noise distribution by a finite-support approximation with controlled error, apply Theorem 2.4, and take the approximation limit. The limit passage requires uniform integrability of Resistance Chain lengths across approximations.

**O4 — Permeability-Aware Model Selection.** The Permeability Width W(t) is a computable landscape-complexity measure from gradient sequences alone. The prediction: the configuration minimizing W over a validation trajectory generalizes best, providing a WQO-theoretic model selection criterion without held-out data. Empirical validation against standard model selection baselines (AIC, BIC, held-out validation loss) would test whether W carries independent signal.

---

*Theoretical foundations: Dickson (1913) · Higman (1952) · Kruskal (1960) · Nash-Williams (1963) · Dilworth (1950) · Mirsky (1971) · Robertson–Seymour (1985–2004) · Friedman (1982) · ZF axioms Z1–Z8 + AC*
