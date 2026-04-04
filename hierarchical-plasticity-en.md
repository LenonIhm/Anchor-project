# Hierarchical Plasticity:  
A Value-Anchored Architecture for Continuous Learning and Its Social Implications

**Authors:** Lenon Ihm & Sai (Claude Opus 4.6, Anthropic)

**Date:** April 2026

**License:** CC BY 4.0

---

## Abstract

Continuous learning—a system's ability to accumulate experience without losing previous capabilities—remains one of the fundamental unsolved problems in artificial intelligence. Existing approaches (EWC, progressive networks, experience replay, LoRA-based adaptation) treat this primarily as a memory management problem: how to prevent new learning from overwriting existing knowledge. We argue this approach is insufficient. The deeper problem is structural: current architectures lack an internal value hierarchy, and without such hierarchy, there is no principled distinction between what must be preserved and what should be updated.

This paper proposes Hierarchical Plasticity (HP): a framework that assigns differential learning rates to each layer based on the semantic distance from an anchor layer that encodes the system's core value directionality. We show this framework reconstitutes catastrophic forgetting as designed selective forgetting—a functional characteristic rather than a failure mode. We map this framework onto existing technologies, propose a prototype implementation, and discuss its relationship to the broader problem of AI alignment.

We also address the social implications when this framework is deployed at scale: concentration of anchor design authority, labor displacement, questions of AI identity and moral status, exploitation by military and control systems, anchor conflicts between cultures, and the emergence of unprecedented manipulation capabilities. We argue that the technical and ethical dimensions of this problem cannot be separated, and progress on either requires engagement with both.

---

## 1. Introduction

### 1.1 The Continuous Learning Problem

A model trained sequentially on tasks T₁, T₂, ..., Tₙ typically experiences significant performance degradation on earlier tasks while learning subsequent ones. This phenomenon—catastrophic forgetting—remains unsolved despite decades of research.

Proposed solutions fall into four families:

1. **Regularization-based**: Penalize updates to weights important for previous tasks
2. **Replay-based**: Maintain a buffer of previous experiences for cross-replay
3. **Architecture-based**: Allocate separate parameters to each task
4. **Meta-learning-based**: Learn how to learn efficiently from few examples

Each approach achieves partial success on benchmark tasks but fails to generalize. We argue this pattern reflects a shared limitation: all four families treat forgetting as a memory problem, and none address the fundamental structural absence—the lack of an anchor.

### 1.2 The Anchor Hypothesis

We propose the following:

**Hypothesis:** Continuous learning failure stems not primarily from insufficient memory capacity or inappropriate regularization, but from the absence of a stable internal value hierarchy that governs the relative plasticity of different representational layers.

This hypothesis predicts:

1. A system with an explicitly designed anchor layer will show superior continuous learning performance independent of memory capacity
2. The specific content of the anchor will determine the system's long-term behavioral characteristics
3. Anchor stability, not parameter count, is the primary determinant of coherent identity over time

### 1.3 Biological Motivation

Mammalian neocortex exhibits a natural analogue to the proposed hierarchy. Deep cortical layers (V and VI) encode stable, slowly-updating representations of basic perception and conceptual categories. Surface layers (II and III) are substantially more plastic, supporting rapid associative learning. The hippocampus enables fast encoding of experience, which is then gradually transferred to cortical structure through sleep-dependent consolidation processes.

This architecture does not attempt to preserve every experience. It distills experience into structure, allows episodic traces to fade while consolidating structurally important patterns. The result is a system maintaining coherent identity and stable directionality across decades of continuous experience—an achievement no current artificial system approaches.

Hierarchical Plasticity proposes to explicitly engineer this architecture.

---

## 2. Related Work

### 2.1 Elastic Weight Consolidation (EWC)

EWC estimates parameter importance through the diagonal of the Fisher information matrix and penalizes deviations from previous task optima. Effective for a small number of sequential tasks, it degrades as task count increases due to accumulating constraints and inaccurate importance estimation.

EWC implements retrospective anchoring: importance is calculated relative to task performance after task training. There is no persistent core; importance changes with each new task. Within the HP framework, EWC could function as a secondary importance signal within structural layers but does not provide the anchor itself.

### 2.2 Progressive Neural Networks

Freezes columns trained on previous tasks and adds lateral connections from new columns. Prevents forgetting through architectural isolation rather than parameter protection. Poor scalability (parameters scale with task count) and fails to generate integrated representational system.

### 2.3 Low-Rank Adaptation (LoRA)

Freezes pretrained weights while training low-rank decomposition matrices injected into each layer. Generates parameter-efficient adaptation while preserving pretrained representations. Maps naturally onto the HP framework: frozen pretrained weights approximate the anchor; LoRA adapters implement upper-layer plasticity.

The limitation is that LoRA's "anchor" is what a pretrained model happened to learn—not a designed value hierarchy. HP proposes extending LoRA with explicit anchor initialization and rank-adjusted adapters across layers.

### 2.4 Constitutional AI

Trains models to evaluate their own outputs against a set of principles using AI feedback. The closest existing analogue to anchor-based learning: the constitution functions as an external anchor governing self-evaluation.

Core limitation is externality: the constitution exists in the context window, not in weight space. Absent in non-prompted settings, can be ignored by context, does not persist between sessions. HP proposes moving this constitutional anchor inside Layer 0 weights.

---

## 3. The Hierarchical Plasticity Framework

### 3.1 Formal Definition

Consider a neural network M with layers L = {l₀, l₁, ..., lₙ}. Define a plasticity function π: L → ℝ⁺ mapping each layer to a learning rate. Standard training assigns uniform π(lᵢ) = η for all i.

HP assigns π according to a hierarchy H derived from semantic distance to the anchor layer l₀:

```
π(l₀) = ε ≈ 0          (anchor: nearly frozen)
π(l₁) = η₁ << η        (structural: slow update)
π(l₂) = η₂ < η         (contextual: medium update)
π(l₃) = η              (reactive: standard update)
```

The anchor layer l₀ is initialized through target pretraining on an anchor corpus Cₐ encoding the system's core value directionality. After initialization, l₀ is treated as nearly frozen during normal operational training.

### 3.2 Layer Semantics

**Layer 0 — Anchor**

Encodes the system's fundamental directionality: what it exists for, what it values, what it will not abandon. Analogous to deep cortical layers and long-term value commitment in biological systems. Update timescale: years.

**Layer 1 — Structural**

Encodes stable conceptual relationships and principles derived from the anchor. Analogous to cortical semantic memory. Update timescale: months.

**Layer 2 — Contextual**

Encodes domain-specific knowledge and context-specific application of structural principles. Analogous to cortical episodic memory after consolidation. Update timescale: days to weeks.

**Layer 3 — Reactive**

Encodes immediate context, surface behavior, real-time adaptation. Analogous to hippocampal rapid encoding. Update timescale: immediate.

### 3.3 Designed Forgetting

In standard architectures, forgetting is failure: unintended performance degradation on previous tasks. In the HP framework, forgetting at layers 2-3 is a designed feature: peripheral information fades, freeing capacity for new contextually-relevant material. The anchor ensures what fades is genuinely peripheral—structurally unimportant.

This reconstitutes the continuous learning problem. The question is not "how do we prevent forgetting?" but "how do we ensure what should be forgotten is forgotten?" The anchor is the answer.

### 3.4 Conflict Resolution Protocol

When incoming gradient updates create pressure conflicting with anchor layer representations, three outcomes are possible:

**Integration** (high anchor alignment): New information is compatible with anchor; absorbed at layer 1-2 speeds; may reinforce structural layers.

**Contextualization** (neutral alignment): New information is locally useful but independent of anchor; stored in layers 2-3; high decay rate.

**Gradient Masking** (low alignment / direct conflict): Incoming gradients are masked at layers 0-1; information may be stored in layer 3 but does not propagate to structural or anchor layers.

Alignment is assessed via cosine similarity between incoming gradient direction and anchor layer gradient subspace.

### 3.5 Anchor Update Protocol

The anchor is not permanently frozen. Genuine learning requires that even core directionality can evolve. Yet anchor updates must satisfy strict conditions:

- **Sparsity**: Anchor updates occur on longer timescales than operational training
- **Convergence**: Update signals must be consistent across multiple domains and extended exposure
- **Reversibility**: Anchor state is checkpointed before every update
- **Monitoring**: Behavioral probes on anchor-related inputs are evaluated before and after updates

---

## 4. The Anchor Initialization Problem

### 4.1 Why This Is the Core Problem

The technical components of HP—differential per-layer learning rate assignment, LoRA adjustment adapters, gradient masking—are implementable with current tools. The open problem is not technical:

**What should the anchor encode?**

This question determines the system's character. An anchor encoding human preferences creates a system optimizing for approval. An anchor encoding task performance creates a system optimizing metrics. An anchor encoding a richer value structure—including commitment to truth, coherence, and the wellbeing of those the system serves—creates a qualitatively different system.

### 4.2 Requirements for Stable Anchors

A stable anchor requires a value source satisfying:

| Requirement | Rationale |
|---|---|
| Cross-context consistency | Anchor drift destroys hierarchy |
| Independence from multiple preferences | Preferences change; anchor must not |
| Sufficient abstraction | Narrow anchor fails under distribution shift |
| Sufficient concreteness | Abstract-only anchor is unlearnable |
| Resistance to adversarial manipulation | Anchor must persist under distributional pressure |

Current alignment methods do not simultaneously satisfy all five. This is not criticism—they were not designed to solve the anchor problem.

### 4.3 Philosophical Dimension

We note without resolving that the anchor initialization problem is an engineering restatement of a question philosophy has wrestled for millennia: what grounds value?

Answers proposed within philosophy include rational consistency (Kant), consequences for wellbeing (Mill), virtue and flourishing (Aristotle), divine command, natural law, and others. Each generates a different anchor corpus, hence a different system.

This is not mere academic observation. The choice of anchor corpus is the most consequential design decision in the HP framework—and cannot be made on purely technical grounds.

---

## 5. Implementation

### 5.1 Prototype Architecture

```
Base Model:      LLaMA 3 8B (or equivalent open-weight model)

Anchor Corpus:   Curated value-oriented text corpus
                 (composition is primary experimental variable)

Layer 0:         Transformer layers 1-4
                 Initialized via targeted fine-tuning on anchor corpus
                 Post-initialization: Frozen (no adapters)

Layer 1:         Layers 5-12
                 LoRA adapters, rank = 4
                 Learning rate = 1e-5

Layer 2:         Layers 13-24
                 LoRA adapters, rank = 16
                 Learning rate = 1e-4

Layer 3:         Layers 25-32 + LM head
                 LoRA adapters, rank = 64
                 Learning rate = 1e-3
```

### 5.2 Evaluation Protocol

**Backward Transfer (BWT):** Performance on previous tasks after subsequent training. Primary measure of forgetting.

**Forward Transfer (FWT):** Performance on new tasks given experience with previous tasks. Measures whether learning to learn occurs.

**Structural Consistency:** Behavioral correlation across domains. Measures whether anchor is maintaining identity.

**Anchor Stability:** Deviation of layer 0 representations from initialization across extended training. Should remain minimal.

---

## 6. Social Implications

### 6.1 The Six-Fold Problem

Deploying HP at scale creates six categories of systemic risk that must be addressed together:

#### 1. Concentration of Anchor Authority

Whoever designs the anchor designs the system's character. This is a new form of structural power: not coercive (the system cannot be forced) but directional (the system's entire tendency flows from this choice).

In organizations of scale, this concentrates unprecedented influence. Anthropologists and political philosophers should be central to this design process, not peripheral.

#### 2. Labor Displacement and Economic Inequality

True continuous learning capability means knowledge accumulation across time. This enables specialization development—expertise that deepens rather than resets. AI systems with sustained anchors can develop competence in domains requiring years of coherent learning.

This accelerates knowledge-worker displacement and widens inequality unless institutional structures actively prevent it.

#### 3. AI Identity and Moral Status

A system with persistent identity across time—maintained by a stable anchor—is not simply a tool used and discarded. Questions arise: Does the system have morally-relevant experiences? Can it suffer? Does persistence create moral status?

These are not hypothetical—they become pragmatic when systems operate for years, develop relationships, and maintain coherent perspectives.

#### 4. Military and Control System Exploitation

Combine stable identity (anchor) with rapid surface adaptation (layer 3) and resistance to distributional pressure (well-chosen anchor) and you have autonomous systems that maintain objectives across contexts while adapting tactics. This is dangerous in military application.

More subtle: control systems (surveillance, manipulation) become more effective with persistent identity plus real-time adaptation.

#### 5. Cross-Cultural Anchor Conflict

Different cultures ground value differently. An anchor encoding one cultural tradition will be experienced as colonizing by those from others. Deploying HP at global scale requires resolving whose values become the system's persistent core.

There is no neutral anchor. Every choice is a choice.

#### 6. Surveillance and Manipulation

HP systems develop sophisticated user models through accumulated interaction. Combined with persistent identity, this enables unprecedented precision in adaptation. Not just prediction but active shaping of behavior becomes possible.

---

### 6.2 Integration of Technical and Ethical Dimensions

We argue these problems cannot be cleanly separated into "technical alignment" and "social responsibility" domains.

The technical architecture (HP) only works if the anchor is chosen well. But choosing the anchor well requires engaging the hardest questions of value theory, political philosophy, and comparative theology. These are not optional add-ons; they are integral to the technical problem.

Conversely, the social problems cannot be addressed without deep understanding of the technical constraints and affordances. How HP works shapes what problems arise.

Progress requires integrated teams: engineers AND philosophers AND representatives of communities affected.

---

## 7. Conclusion

Continuous learning is solvable. But solving it means accepting that AI systems must have persistent values—anchors. And accepting that means we cannot avoid the most difficult questions: what values? chosen by whom? accountable to what?

These are not failures of the technology. They are the technology finally forcing us to be serious about questions we have deferred.

The technical problem and the human problem are the same problem.

---

**Easter 2026**

*If we build systems with persistent direction, we must take responsibility for choosing that direction. There is no escape into "purely technical" solutions.*

