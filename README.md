# DSC 200: Data Science Programming

**Fall 2026 · UC San Diego**

**Instructor:** Duncan Watson-Parris · **TA:** TBD

## Course description

Programming for data science in the age of coding agents. Most working code is now produced by steering AI agents from loosely defined requirements (whether business, research, or product) rather than by hand-writing library calls. What remains valuable is the judgment around the code: turning ambiguous requirements into precise specifications, choosing data structures, algorithms, and architectures with the right trade-offs, validating that generated code and its outputs are actually correct, and knowing when a project is *done*. 

This course teaches Python and the PyData ecosystem at the fluency level needed to **read, verify, and steer**; teaches algorithms and data structures as the vocabulary for predicting the consequences of an agent's implementation choices; and covers the durable engineering skills needed in todays world: using coding agents, software engineering fundamentals, and shaping the build.

## Learning outcomes

By the end of the course, students can:

1. Read and critically review Python data science code (NumPy/Pandas/xarray/matplotlib) well enough to spot incorrect logic, silent data errors, and misuse of the libraries — whether written by a human or an agent.
2. Explain and apply effective practice for working with coding agents: harness configuration, context management, task scoping, planning vs. execution, and closing the loop with verifiers.
3. Recognize the data structures and algorithms that code relies on (including code hidden behind library calls), predict its time and memory scaling, measure that scaling, and identify better alternatives.
4. Translate vague stakeholder requirements into specs, acceptance criteria (including performance budgets), and evaluation plans; decide what to build next from feedback; recognize "done."
5. Make and defend software design decisions: flexibility vs. structure, architecture patterns, data storage, and cost/scalability/reliability/speed trade-offs.
6. Design testing and validation strategies appropriate to AI-generated code: unit/property/regression tests, data validation, statistical sanity checks, CI.
7. Identify the risks of agent use and the controls for them: sandboxing and permissions, secrets hygiene, prompt injection, data governance, and cost/latency budgets.
8. Explain, at a working level, how an LLM-based coding agent functions (tokens, context windows, tool calling, the agentic loop) and why the harness matters as much as the model.

## Course structure

29 class meetings, Monday/Wednesday/Friday from Fri Sep 25 (Week 0) to Fri Dec 4 (Week 10): 25 teaching sessions including a midterm, one project clinic, and three sessions of project presentations in the last week of classes. No class on Veterans Day (Wed Nov 11) or Thanksgiving (Thu–Fri Nov 26–27). The final exam is in finals week, in the registrar-assigned slot.

### Module A — Foundations for reading and verifying code (S1–S7, Weeks 0–2)

*Python and the PyData stack, to the level where you can read and verify code.*

| # | Date | Topic |
|---|---|---|
| S1 | Fri Sep 25 | **Orientation.** Why the course changed; the skills map; Python on DataHub; Git/GitHub. Live demo: an agent builds a small analysis and the class dissects the transcript (what did it assume? where could it be wrong?). |
| S2 | Mon Sep 28 | **Python essentials I.** Types, control flow, functions, core containers (list/dict/set/tuple). |
| S3 | Wed Sep 30 | **Python essentials II — reading & debugging.** Exceptions and tracebacks, comprehensions, modules/imports, scripts vs. notebooks; regular expressions as something you *verify* rather than write. |
| S4 | Fri Oct 2 | **NumPy.** Arrays, vectorization, broadcasting; first look at cost: the same computation as a Python loop vs. vectorized. |
| S5 | Mon Oct 5 | **Pandas I.** Series/DataFrame, indexes and alignment, selection. |
| S6 | Wed Oct 7 | **Pandas II.** Group-by, merge/join, reshape, tidy data; silent failure modes (misalignment, NaN propagation, dtype/timezone traps, chained assignment). |
| S7 | Fri Oct 9 | **xarray & matplotlib.** Labeled multi-dimensional data; figure anatomy. |

### Module B — Using coding agents (S8–S13, Weeks 3–4)

*How coding agents actually work, and how to steer and check them.*

| # | Date | Topic |
|---|---|---|
| S8 | Mon Oct 12 | **LLM foundations for users.** Tokenization, context windows, sampling, knowledge cutoffs, tool/function calling — and their behavioral consequences (hallucinated APIs, context placement, caching and cost). |
| S9 | Wed Oct 14 | **Anatomy of a harness.** The agentic loop: model + system prompt + tools + permissions + context management. Why the harness is as much of the product as the model. A real session traced from prompt to diff. |
| S10 | Fri Oct 16 | **The agentic workflow.** Requirements → spec → plan → implement → verify. Case study: the same task run from a vague and a precise spec. Introduces the spec template for project M1. |
| S11 | Mon Oct 19 | **Context management & evaluation-driven development.** What goes into context and what stays out; when to start fresh; giving the agent verifiers (tests, evals, type checks) so it can close loops. Case study: the same task with and without a test suite. |
| S12 | Wed Oct 21 | **Security.** Sandboxing and permission models; secrets hygiene; prompt injection via untrusted files and data (live demo). |
| S13 | Fri Oct 23 | **Cost, data constraints & reproducibility.** Token/cost and latency budgets; sensitive and licensed data; reproducibility of agent-assisted work; logs and audit trails. |

**S14 — Midterm exam, Mon Oct 26** (in class, closed-AI; Modules A–B).

### Module C — Algorithms & data structures: reasoning about the agent's choices (S15–S20, Weeks 5–7)

*Recognising the structures and algorithms behind code, and predicting how they scale.*

| # | Date | Topic |
|---|---|---|
| S15 | Wed Oct 28 | **Complexity & empirical scaling.** Order of growth, Big-O vs. Θ, best/worst/average case; space complexity (memory is often the binding constraint in data science); amortized cost; constant factors (interpreted loops vs. vectorized C). Measuring scaling empirically (time and peak memory across *n*, log–log slope). Performance budgets as acceptance criteria. Coda: the complexity of the agent itself — cumulative token cost over a session. |
| S16 | Fri Oct 30 | **Arrays, linked lists & hash tables.** Contiguous vs. linked storage; dynamic arrays and amortized append (why `np.append`/`pd.concat` in a loop is quadratic); hash tables — dict/set membership, hashability, and the hashing behind pandas indexes, group-by, and joins; many-to-many join blow-up. |
| S17 | Mon Nov 2 | **Stacks, queues & recursion.** LIFO/FIFO abstract data types and their applications; the call stack and reading tracebacks; recursion depth limits and iterative rewrites; `deque` vs. `list.pop(0)`. |
| S18 | Wed Nov 4 | **Binary search trees & kd-trees.** BST property, search cost ∝ height, traversals, insertion and removal (traced by hand); degeneracy on sorted input and why balanced trees and B-tree indexes exist; binary search on sorted arrays as the array analogue; kd-trees for spatial nearest-neighbour search. |
| S19 | Fri Nov 6 | **Heaps & sorting.** Heap property and array representation; priority queues and top-*k*; sorting algorithms compared (time, extra memory, stability); what Python/NumPy/pandas actually use; stability and reproducibility; out-of-core merge. |
| S20 | Mon Nov 9 | **Graphs & DAGs.** Adjacency matrix vs. list (and sparse storage); DFS/BFS in O(\|V\|+\|E\|); shortest paths; DAGs and topological sort as the basis of pipelines and task schedulers; dependency resolution; recognizing when an "optimal" answer to an intractable problem is really a heuristic. |
| — | Wed Nov 11 | *Veterans Day — no class.* |

### Module D — Software engineering fundamentals (S21–S24, Weeks 7–8)

*Architecture, code structure, and testing.*

| # | Date | Topic |
|---|---|---|
| S21 | Fri Nov 13 | **Architecture & data stores.** Pipelines and layered designs; file formats and stores (CSV/Parquet/NetCDF/Zarr/databases); cost–scalability–reliability–speed trade-offs, stage by stage. Case study: the same climate calculation as a one-off analysis, a nightly pipeline, and a shared package. |
| S22 | Mon Nov 16 | **Structuring code.** Notebook → script → module → package; interfaces and contracts; functions vs. classes; OOP where it earns its keep; the central trade-off of flexibility vs. structure. Case study: one prototype under diverging change requests, where both over- and under-structured designs pay. |
| S23 | Wed Nov 18 | **Testing I.** What to test when you didn't write the code: pytest, property-based testing, regression/golden tests, scaling tests. |
| S24 | Fri Nov 20 | **Testing II & code review.** Schema and statistical validation of data outputs; CI on GitHub; reviewing an agent-authored pull request. |

### Module E — Shaping the build and project presentations (S25–S29, Weeks 9–10)

*From loose requirements to "done".*

| # | Date | Topic |
|---|---|---|
| S25 | Mon Nov 23 | **Shaping the build.** Turning stakeholder language into buildable scope (the business-analyst skill); synthesizing user signals into fast product decisions; iterating when prototypes take a day; speed–cost–risk–human-effort trade-offs; definition of done. |
| S26 | Wed Nov 25 | **Project clinic.** No new content; teams work with instructor and TA on M2 feedback. |
| — | Thu–Fri Nov 26–27 | *Thanksgiving — no class.* |
| S27 | Mon Nov 30 | **Project presentations** (≈6 teams). |
| S28 | Wed Dec 2 | **Project presentations** (≈6 teams). |
| S29 | Fri Dec 4 | **Project presentations** (≈6 teams). Last day of instruction. |
| Finals | Dec 5–12 | **Final exam** (closed-AI, cumulative, weighted toward Modules C–E), in the registrar-assigned slot. |

## AI policy

Use of AI assistants and coding agents is permitted in the project and quizzes, and must be disclosed and logged in the project. You are accountable for everything you submit: "the agent wrote it" is not a defense — validating it was the job. Exams are closed-AI and certify individual understanding.

## Logistics

- Websites: Canvas (syllabus of record, quizzes), GitHub (materials), Gradescope (exams, project), ClassBuzz (participation), DataHub (Python environment)
- Office hours: TBD
- Academic integrity: UCSD policy applies; undisclosed AI use in the project, or any AI use in exams, is an integrity violation.

## Key references

- A. Ng, *The AI Engineering Skills Map* and the four "in detail" letters (The Batch, DeepLearning.AI, Aug–Sep 2026): overview; using coding agents; software engineering fundamentals; building and deploying AI applications; shaping the build.
- Anthropic, Claude Code documentation (harness, permissions, hooks) — https://code.claude.com/docs
- B. Miller & D. Ranum, *Problem Solving with Algorithms and Data Structures using Python* (open textbook, Runestone Academy) — optional reference for Module C.
- M. Gorelick & I. Ozsvald, *High Performance Python*, 2nd ed. (O'Reilly, 2020) — optional reference for profiling and NumPy/pandas performance.
- Course texts from FA25 remain optional references for the PyData stack.

## Lectures

Lecture notebooks are published to [`lectures/`](lectures) as they are delivered.
They are Jupyter notebooks; run them on [DataHub](https://datahub.ucsd.edu) —
nothing to install. Datasets used in the lectures are in [`data/`](data).

License: CC-BY-4.0
