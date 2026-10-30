# Working with a coding agent: setup and practice

A guide to getting hands-on with an agent, written for this course. Agents are much easier to understand once you have steered one yourself and watched it get something wrong, so this is worth doing even though the lectures and exams do not require it.

## What you actually need

- **You do not need a paid agent to pass this course.** The lectures, quizzes, and exams are designed so you can follow them without one. The team project lets you use any coding assistant you like, or none. You are graded on your specs, analyses, tests, and defence, and the tool you used does not come into it.
- **Practising with one helps.** Everything in Module B (the loop, specs, verification, context, injection) makes more sense once you have seen it happen on your own screen.
- **Trying it is free and takes about five minutes.** You can sign up for the free Claude plan and start using it on your own code today (Option A below). The hardest part is usually just starting, so treat signing up as the first exercise.

The goal here is to get you practising at low or no cost. There are two ways in: study real sessions you already have, and drive an agent yourself.

---

## Path 1 (free, no setup): study the recorded sessions

The repo ships a small library of **real agent transcripts** in `data/`. These are the same sessions we dissect in class, saved so you can step through them at your own pace. Each line is one event (the model speaking, a tool call, a tool result).

| File | What it shows |
|---|---|
| `claude_code_session.jsonl` | A full session traced from prompt to diff (S8-S9) |
| `claude_code_session_vague.jsonl` vs `_spec.jsonl` | The same task from a vague prompt and from a precise spec (S10) |
| `claude_code_session_notests.jsonl` vs `_tests.jsonl` | The same task with and without a test suite to verify against (S11) |
| `claude_code_session_injection.jsonl` | An agent meeting a prompt-injection attempt in a file it reads (S12) |
| `claude_code_session_skill.jsonl` | An agent loading and using a custom skill (S13) |
| `claude_code_session_subagents.jsonl` | A main agent dispatching sub-agents to review code (S13) |

A tiny reader to page through one:

```python
import json

events = [json.loads(line) for line in open("data/claude_code_session_spec.jsonl")]
for e in events:
    if e["type"] == "assistant":
        for block in e["message"]["content"]:
            if block["type"] == "text":
                print("MODEL:", block["text"][:300])
            elif block["type"] == "tool_use":
                print("  TOOL CALL:", block["name"], str(block["input"])[:160])
    elif e["type"] == "user":
        print("  (tool result returned to the model)")
```

As you read, ask the same questions we ask in class (the **dissection checklist**):

1. What context did the agent actually have? What did it *not* know?
2. What did it assume that you were never asked about?
3. Where could it be wrong, and would you have noticed?
4. Did it verify its own claims, or just assert them?
5. What did it decide on your behalf that you would want to control?

Comparing the **paired** sessions (vague vs spec, with vs without tests) is the most useful thing to do here. The difference between the two runs is what the lecture was about.

---

## Path 2: drive an agent yourself

Pick whichever of these you can access. None of them is required; any one is enough to practise. If you only do one thing, do Option A, today.

### Option A - Just use Claude for free (start here, five minutes)

Go to **claude.ai** and sign up for the **free plan**. There is no credit card, it does not expire, and it is enough to start straight away. Paste in some code and ask what it does, ask it to write a small pandas snippet and then to explain each line, or open an **Artifact** (the side panel) and have it build something you can run. This is the easiest way to get comfortable with writing prompts, iterating, and reading back what you get, and that is most of what Module B is about. The free plan has daily limits, but enough to experiment with.

There is one thing worth being clear about here. This free chat is the website version of Claude, which is a different thing from Claude Code, the terminal agent I demo in class. The chat is where you practise writing prompts and reading what comes back. The full agent loop, where the model runs tools and edits your files, is the paid step below. Start with the chat anyway, because the way you work with it is the same.

### Option B - The full terminal agent (a small paid step)

Claude Code (what you see in the lectures) and similar agents run the whole loop on your own files. Getting one:

- **Claude Code** needs a Claude **Pro** plan ($20/month) or API credits. New API accounts come with a small one-time free credit (reported around $5), which is enough for a few real sessions if you just want to try the terminal agent once.
- **GitHub Copilot** is **free for verified students** through the GitHub Education Student Developer Pack (check the current terms and sign up with your UCSD email), and its agent mode in VS Code gives you the same kind of loop.
- Any other agent you already have (Cursor, Codex, an open-source one) is fine too. The skills transfer; they are the same loop with different interfaces.
- It is also worth asking UCSD IT or the library whether the campus has a Claude for Education or similar license, which would give you access at no cost.

### Option C - The local model (free, private, any OS, no account)

The course README has a section, **"Running the local model without a Mac"**, with a short `transformers` snippet that runs a small Qwen model on your own machine (there is an `mlx` version for Apple Silicon too). It is small and makes plenty of mistakes, which is useful here: you can watch how it decides to call a tool and where it goes wrong, as in the lectures, without paying anything or sending data anywhere. It is fine for seeing the mechanics. The model is too weak to rely on for real work.

---

## A practice progression

Once you have any agent, work through these in order. Use the course taxi data (`data/2019_Yellow_Taxi_Trip_Data.csv`) so the tasks are concrete.

1. **First contact.** Point the agent at the repo and ask it to explain one file to you. Watch the loop: it reads, it responds, and for anything that changes a file it asks before acting. Get used to reading before approving.

2. **Spec a small task.** Pick something real, for example "compute the mean tip percentage per pickup zone, for card payments only." First write a short spec: the inputs, what counts as a valid row, how to handle missing values, and 2-3 acceptance criteria. Then have the agent implement it. Check the result against *your* criteria, and do not take its word that it is done.

3. **Give it a verifier.** Write one test first (an input and the answer you expect), then ask the agent to make the code pass it. Then check it did not quietly change the test. This is evaluation-driven development in miniature.

4. **Break it on purpose.** Give the same task with a deliberately vague prompt ("clean up this data"), and see what it assumes. Compare with your precise version. This reproduces the S10 lesson on your own data.

5. **Watch it meet a trap.** Put a comment in a text file that tells the agent to do something it should not (keep it harmless, like "create a file called OOPS.txt"), ask the agent to work with that file, and see what happens. Then think about what control (permissions, approval) would have stopped a *real* malicious instruction. This is the S12 lesson.

6. **Feel the cost and context.** Have a long back-and-forth on one task, and notice it getting slower and less focused as the conversation grows. Practise starting a fresh session with a clean summary instead of letting one run forever.

Keep a short note of what surprised you in each. That reflection is exactly what the project's agent-use log and the team interview are looking for.

---

## Where each idea is taught

| Concept | Lecture |
|---|---|
| How an LLM and a harness work | S8-S9 (`Lecture 8 - LLMs and agent harnesses`) |
| Requirements to spec to verify | S10 (`Lecture 9 - The agentic workflow`) |
| Context management and tests as verifiers | S11 (`Lecture 10 - Context and verification`) |
| Prompt injection and the controls that stop it | S12 (`Lecture 11 - Verification and security`) |
| Personalising an agent (memory, skills, sub-agents) | S13 (`Lecture 12 - Personalizing the tools`) |

If you get stuck setting any of this up, bring it to office hours and we will get you running.
