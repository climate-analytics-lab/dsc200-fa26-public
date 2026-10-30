# DSC 200 skills map: what you should be able to do

A plain list of the skills this course is trying to give you, module by module, so you can check your own progress. The field is moving fast, so this is deliberately about the skills that stay useful when the specific tool changes.

One idea runs through the whole course. The syntax is something you can look up, or have a tool write for you. The skills that matter are reading code, predicting what it will do, spotting where it is wrong, and deciding whether to trust it. Those transfer to any tool and any job.

Two things follow from that. First, syntax fluency still matters, because you cannot judge code you cannot read, and the exams are closed-book code reading and debugging. Second, the skills that matter most are steering and verifying, which is why the agents section is the largest part of the course.

Where to practice each skill is listed at the end of every section.

---

## Module A - Foundations (the data tools)

You should be able to:

- Read and write everyday **NumPy** (arrays, dtypes, indexing, boolean masks, operating along an axis) and predict the shape of a result.
- Read and write everyday **pandas** (Series/DataFrame, indexing and alignment, selection, group-by, merge/join, cleaning).
- Recognise the **silent failure modes**: broadcasting surprises, index misalignment giving NaN, missing-value traps, dtype and datetime gotchas, duplicate-key joins that multiply rows.
- Use **xarray** for labelled multi-dimensional data (select by label, reduce along a named dimension, broadcast by name, weighted means).
- Make a clear **matplotlib** figure (the figure/axes model, labels, multiple series, subplots).

*Practice:* the Module A lecture notebooks (S2-S7), and `practice/python_data_tools_practice.ipynb` in this repo.

## Module B - Using coding agents (the core of the course)

This is the part people ask about most, so it is the most detailed. You should be able to:

**Understand the machine well enough to steer it**
- Explain in plain terms how an LLM works for a user: tokens, the context window, sampling and temperature, and the knowledge cutoff, and what each one means for behaviour (why it invents APIs, why it is stuck in an older world unless told otherwise).
- Explain the **agent loop**: the model asks for a tool, the harness runs it and feeds the result back, repeat. Know that the model does not run your code itself; the harness does.
- Describe what a **harness** is (model + system prompt + tools + permissions + context) and why it shapes what you get as much as the model does.

**Drive an agent well**
- Turn a vague goal into a **spec**: requirements, acceptance criteria, and a performance budget, and see how much a spec changes the result.
- Work the loop: requirements, then spec, then plan, then implement, then verify.
- Give the agent **verifiers** it can run (tests, type checks) so it can catch its own mistakes, and know why that works better than telling it to "be careful".
- **Check its work**: when it says "all tests pass", check first whether it changed, deleted, or weakened a test; when it says "much faster", check whether it measured anything.

**Manage context and cost**
- Decide what belongs in the context and what does not, and when to start a fresh session.
- Explain why a long session gets expensive (each turn re-sends the whole conversation, so cost grows roughly with the square of the turns), and how compaction and fresh sessions bound it.

**Work safely**
- Recognise **prompt injection** (instructions hidden in a file, web page, or dataset the agent reads) and know that the defence that works is structural: permissions, sandboxing, and keeping secrets out of the context. A polite system prompt is not enough on its own.

**Make it your own**
- Use project memory (`CLAUDE.md` / `AGENTS.md`), skills, and sub-agents to shape an agent to your project, and know roughly when fine-tuning is or is not the right tool.

**The judgment that ties it together**
- For any agent output, name what it decided on your behalf, what it did not actually verify, and whether you would trust it in production.

*Practice:* the Module B lecture notebooks (S8-S13); the recorded agent transcripts in `data/*.jsonl`, which you can read step by step; `practice/working_with_agents.md` in this repo; and the team project.

## Module C - Algorithms and data structures

You should be able to:

- Predict how code **scales**: count the loops, read off the order of growth, drop constants and lower-order terms, and measure scaling empirically (the slope on log-log axes).
- Know that constant factors and **memory** matter as much as the growth rate, and spot an `n`-by-`n` step that will run out of memory.
- Recognise the **structure behind a library call**: arrays, hash tables (dict/set, and what pandas indexes and joins run on), trees, heaps, graphs, and predict each one's costs.
- Choose a sensible structure for a described task, and recognise when an agent's "optimal" answer is really a heuristic.

*Practice:* the Module C lecture notebooks (S15-S20) and project M2 (the scaling analysis).

## Module D - Software engineering fundamentals

You should be able to:

- Reason about **architecture**: pipelines and layered designs, file formats and stores, and the cost/scalability/reliability/speed trade-offs between them.
- **Structure code** as it grows (notebook to script to module to package), and know when a class earns its keep.
- **Test code you did not write**: pytest, property-based tests, regression/golden tests, scaling tests, and schema/statistical validation of outputs.
- **Review an agent-authored pull request**: find the bug, the missing test, and the scaling problem.

*Practice:* the Module D lecture notebooks (S21-S24) and the project.

## Module E - Shaping the build

You should be able to:

- Take a loose problem to a clear **definition of done**, weighing speed, cost, risk, and human effort.
- Present and **defend** a built data product: the decisions, the trade-offs, and why it is finished.

*Practice:* project milestones M2 and M3, and the final presentation and interview.

---

## What this adds up to for your career

Underneath the specific libraries, the skills that matter are the ones employers are asking for as AI tools spread:

1. **Specify** what you want precisely enough that someone, or something, else can build it.
2. **Verify** work you did not do yourself, and know when a confident claim is unproven.
3. **Read and debug** unfamiliar code, and predict how it behaves and scales.
4. **Judge** a tool's output: what it assumed, what it got wrong, and whether to trust it.

Those are what you do when you work with a coding agent, and they are what the course is built around. They will still be useful when today's tools have changed.
