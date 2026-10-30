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

28 class meetings, Monday/Wednesday/Friday from Fri Sep 25 (Week 0) to Fri Dec 4 (Week 10): 24 teaching sessions including a midterm, one project clinic, and three sessions of project presentations in the last week of classes. No class on Fri Oct 16, Veterans Day (Wed Nov 11) or Thanksgiving (Thu–Fri Nov 26–27). The final exam is in finals week, in the registrar-assigned slot.

### Module A — Foundations for reading and verifying code (S1–S7, Weeks 0–2)

*Python and the PyData stack, to the level where you can read and verify code.*

| # | Date | Topic | Notes |
|---|---|---|---|
| [S1](lectures/Lecture%201%20-%20Orientation.ipynb) | Fri Sep 25 | **Orientation.** Why the course changed; the skills map; Python on DataHub; Git/GitHub. Live demo: an agent builds a small analysis and the class dissects the transcript (what did it assume? where could it be wrong?). |  |
| [S2](lectures/Lecture%202%20-%20Python%20essentials%20I.ipynb) | Mon Sep 28 | **Python essentials I.** Types, control flow, functions, core containers (list/dict/set/tuple). |  |
| [S3](lectures/Lecture%203%20-%20Python%20essentials%20II.ipynb) | Wed Sep 30 | **Python essentials II — reading & debugging.** Functions, comprehensions, exceptions and tracebacks, modules/imports. | Remote (Zoom link on Canvas) |
| [S4](lectures/Lecture%204%20-%20NumPy.ipynb) | Fri Oct 2 | **Regular expressions and NumPy.** Scripts vs. notebooks; regular expressions as something you *verify* rather than write; arrays, dtypes, indexing and Boolean masks, operating along an axis. | Remote (Zoom link on Canvas) |
| [S5](lectures/Lecture%205%20-%20pandas%20I.ipynb) | Mon Oct 5 | **Pandas I.** Broadcasting and a first look at cost (a Python loop vs. vectorized); Series/DataFrame, indexes and alignment, selection. | Remote (Zoom link on Canvas) |
| [S6](lectures/Lecture%206%20-%20pandas%20II.ipynb) | Wed Oct 7 | **Pandas II.** The course project. Summary statistics, group-by, cleaning, merge/join; silent failure modes (misalignment, duplicate keys, dtype traps, chained assignment). |  |
| [S7](lectures/Lecture%207%20-%20matplotlib%20and%20xarray.ipynb) | Fri Oct 9 | **xarray & matplotlib.** Labeled multi-dimensional data; figure anatomy. |  |

### Module B — Using coding agents (S8–S13, Weeks 3–4)

*How coding agents actually work, and how to steer and check them.*

| # | Date | Topic | Notes |
|---|---|---|---|
| [S8–S9](lectures/Lecture%208%20-%20LLMs%20and%20agent%20harnesses.ipynb) | Mon Oct 12 | **LLM foundations & anatomy of a harness.** Tokenization, context windows, sampling, knowledge cutoffs, tool/function calling, and their behavioral consequences (hallucinated APIs, context placement, caching and cost). The agentic loop: model + system prompt + tools + permissions + context management, and why the harness is as much of the product as the model. A real session traced from prompt to diff. | Remote (Zoom link on Canvas) |
| [S10](lectures/Lecture%209%20-%20The%20agentic%20workflow.ipynb) | Wed Oct 14 | **The agentic workflow.** Requirements → spec → plan → implement → verify. Case study: the same task run from a vague and a precise spec. Introduces the spec template for project M2. | Remote (Zoom link on Canvas) |
| — | Fri Oct 16 | *No class.* | **Cancelled** |
| [S11](lectures/Lecture%2010%20-%20Context%20and%20verification.ipynb) | Mon Oct 19 | **Context management & evaluation-driven development.** What goes into context and what stays out; when to start fresh; giving the agent verifiers (tests, evals, type checks) so it can close loops. Case study: the same task with and without a test suite. |  |
| [S12](lectures/Lecture%2011%20-%20Verification%20and%20security.ipynb) | Wed Oct 21 | **Security.** Sandboxing and permission models; secrets hygiene; prompt injection via untrusted files and data (live demo). |  |
| [S13](lectures/Lecture%2012%20-%20Personalizing%20the%20tools.ipynb) | Fri Oct 23 | **Cost, data constraints & reproducibility.** Token/cost and latency budgets; sensitive and licensed data; reproducibility of agent-assisted work; logs and audit trails. |  |

**S14 — Midterm exam, Mon Oct 26** (in class, closed-AI; Modules A–B).

### Module C — Algorithms & data structures: reasoning about the agent's choices (S15–S20, Weeks 5–7)

*Recognising the structures and algorithms behind code, and predicting how they scale.*

| # | Date | Topic | Notes |
|---|---|---|---|
| [S15](lectures/Lecture%2013%20-%20Complexity%20and%20empirical%20scaling.ipynb) | Wed Oct 28 | **Complexity & empirical scaling.** Order of growth, Big-O vs. Θ, best/worst/average case; space complexity (memory is often the binding constraint in data science); amortized cost; constant factors (interpreted loops vs. vectorized C). Measuring scaling empirically (time and peak memory across *n*, log–log slope). Performance budgets as acceptance criteria. Coda: the complexity of the agent itself — cumulative token cost over a session. |  |
| S16 | Fri Oct 30 | **Arrays, linked lists & hash tables.** Contiguous vs. linked storage; dynamic arrays and amortized append (why `np.append`/`pd.concat` in a loop is quadratic); hash tables — dict/set membership, hashability, and the hashing behind pandas indexes, group-by, and joins; many-to-many join blow-up. |  |
| S17 | Mon Nov 2 | **Stacks, queues & recursion.** LIFO/FIFO abstract data types and their applications; the call stack and reading tracebacks; recursion depth limits and iterative rewrites; `deque` vs. `list.pop(0)`. |  |
| S18 | Wed Nov 4 | **Binary search trees & kd-trees.** BST property, search cost ∝ height, traversals, insertion and removal (traced by hand); degeneracy on sorted input and why balanced trees and B-tree indexes exist; binary search on sorted arrays as the array analogue; kd-trees for spatial nearest-neighbour search. |  |
| S19 | Fri Nov 6 | **Heaps & sorting.** Heap property and array representation; priority queues and top-*k*; sorting algorithms compared (time, extra memory, stability); what Python/NumPy/pandas actually use; stability and reproducibility; out-of-core merge. |  |
| S20 | Mon Nov 9 | **Graphs & DAGs.** Adjacency matrix vs. list (and sparse storage); DFS/BFS in O(\|V\|+\|E\|); shortest paths; DAGs and topological sort as the basis of pipelines and task schedulers; dependency resolution; recognizing when an "optimal" answer to an intractable problem is really a heuristic. |  |
| — | Wed Nov 11 | *Veterans Day — no class.* |  |

### Module D — Software engineering fundamentals (S21–S24, Weeks 7–8)

*Architecture, code structure, and testing.*

| # | Date | Topic | Notes |
|---|---|---|---|
| S21 | Fri Nov 13 | **Architecture & data stores.** Pipelines and layered designs; file formats and stores (CSV/Parquet/NetCDF/Zarr/databases); cost–scalability–reliability–speed trade-offs, stage by stage. Case study: the same climate calculation as a one-off analysis, a nightly pipeline, and a shared package. |  |
| S22 | Mon Nov 16 | **Structuring code.** Notebook → script → module → package; interfaces and contracts; functions vs. classes; OOP where it earns its keep; the central trade-off of flexibility vs. structure. Case study: one prototype under diverging change requests, where both over- and under-structured designs pay. |  |
| S23 | Wed Nov 18 | **Testing I.** What to test when you didn't write the code: pytest, property-based testing, regression/golden tests, scaling tests. |  |
| S24 | Fri Nov 20 | **Testing II & code review.** Schema and statistical validation of data outputs; CI on GitHub; reviewing an agent-authored pull request. |  |

### Module E — Shaping the build and project presentations (S25–S29, Weeks 9–10)

*From loose requirements to "done".*

| # | Date | Topic | Notes |
|---|---|---|---|
| S25 | Mon Nov 23 | **Shaping the build.** Turning stakeholder language into buildable scope (the business-analyst skill); synthesizing user signals into fast product decisions; iterating when prototypes take a day; speed–cost–risk–human-effort trade-offs; definition of done. |  |
| S26 | Wed Nov 25 | **Project clinic.** No new content; teams work with instructor and TA on M2 feedback. |  |
| — | Thu–Fri Nov 26–27 | *Thanksgiving — no class.* |  |
| S27 | Mon Nov 30 | **Project presentations** (≈6 teams). |  |
| S28 | Wed Dec 2 | **Project presentations** (≈6 teams). |  |
| S29 | Fri Dec 4 | **Project presentations** (≈6 teams). Last day of instruction. |  |
| Finals | Dec 5–12 | **Final exam** (closed-AI, cumulative, weighted toward Modules C–E), in the registrar-assigned slot. |  |

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

Lecture notebooks are published to [`lectures/`](lectures) as they are delivered,
and linked from the session number in the schedule above.

They are Jupyter notebooks; run them on [DataHub](https://datahub.ucsd.edu) —
nothing to install. Datasets used in the lectures are in [`data/`](data).

For extra practice between classes, see [`practice/`](practice): a self-check notebook of NumPy, pandas, matplotlib and xarray exercises, a guide to getting hands-on with a coding agent, and a map of the skills the course builds.

### Running the local model without a Mac

Lectures 8–11 run a small open-weights model on my laptop with
[`mlx-lm`](https://github.com/ml-explore/mlx-lm), which only works on Apple-silicon
Macs. You don't need to run these cells to follow the lectures. But if you'd like to
try the model yourself on Windows, Linux, or DataHub, use Hugging Face
[`transformers`](https://huggingface.co/docs/transformers) instead. The tokenizer,
the chat template, and the tool-calling format are all the same; only the `load` and
`generate` calls differ.

```python
# pip install transformers torch
from transformers import AutoModelForCausalLM, AutoTokenizer

# A small Qwen model. 1.7B is a good default; 0.6B is lighter and faster on a CPU.
# (The lectures use Qwen3-4B-Instruct-2507, which is the same family but needs more
#  memory; if you can run it, drop the enable_thinking argument below.)
MODEL = "Qwen/Qwen3-1.7B"
tokenizer = AutoTokenizer.from_pretrained(MODEL)
model = AutoModelForCausalLM.from_pretrained(MODEL, torch_dtype="auto")


def ask(question, max_new_tokens=100):
    inputs = tokenizer.apply_chat_template(
        [{"role": "user", "content": question}],
        add_generation_prompt=True,
        enable_thinking=False,       # these small models "think" out loud by default
        return_tensors="pt",
        return_dict=True,
    )
    output = model.generate(**inputs, max_new_tokens=max_new_tokens, do_sample=False)
    reply = output[0, inputs["input_ids"].shape[1]:]   # just the new tokens
    return tokenizer.decode(reply, skip_special_tokens=True)


# Tokenization works exactly as in the lecture:
ids = tokenizer.encode("strawberry")
print(len(ids), "tokens:", " | ".join(tokenizer.decode([i]) for i in ids))

print(ask("What is the capital of France? One word."))
```

This is much slower than on a GPU, so stick to small models and short prompts, and
expect more mistakes than the lecture's 4B model. Tool calling works the same way:
pass `tools=[your_function]` to `apply_chat_template`, and parse the `<tool_call>`
block out of the reply, exactly as the lecture's `agent` loop does.

Another option is [Ollama](https://ollama.com), which installs separately and runs
the model as a local service (e.g. `ollama run qwen3:1.7b`).

License: CC-BY-4.0
