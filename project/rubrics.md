# Project rubrics: M3, presentation, interview, peer evaluation

DSC 200, Fall 2026. The project is 60% of the course grade:

| Part | Weight | Graded |
|---|---|---|
| M1 proposal | 5% | done |
| M2 design | 10% | done |
| **M3 final repository and report** | **30%** | per team |
| **Presentation and interview** | **15%** | presentation per team, interview per student |

Peer evaluation can change your share of the team marks (see the end). The presentation timetable is on Canvas.

---

## M3: final repository and report (30 points)

Due **Friday Dec 4**, 11:59 pm. Submit the link to your repository and the report on Gradescope.

| Criterion | Points | Full marks | Partial marks |
|---|---|---|---|
| **1. It does what the spec says** | 8 | Each acceptance criterion from your M2 spec is met, and you show how you know (a test, a number, a plot). Changes to the spec are listed with the reason. | Some criteria are met, or met without evidence. |
| **2. Tests and validation** | 8 | Tests run in CI and pass. They check the acceptance criteria and some edge cases, not only that the code runs. The input data is checked (types, ranges, missing values, joins). | Tests exist but are loose, or only some run, or the data is not checked. |
| **3. Scaling** | 5 | You measured how the main steps scale with data size, at a realistic size. You say whether you met your performance budget, and if not, why. | Scaling is discussed but not measured, or measured only on small data. |
| **4. Code and repository** | 4 | The README says what it is and how to install and run it. The environment is pinned. The code is in functions or modules, not one long notebook. Someone else could run it. | It runs, but only with help, or the structure is hard to follow. |
| **5. Report** | 3 | Short (about 2 pages). Gives the evidence that the result is correct, the main trade-offs you made, the limits, and why you think it is done. | Describes what you did, but not why, or not how you know it works. |
| **6. Agent-use log** | 2 | Says which tools you used and for what. Includes at least one case where the agent was wrong and how you found out. | A list of tools with no detail. |

---

## Presentation (team)

In class on Nov 30, Dec 2 or Dec 4. About **4 minutes**, then about **3 minutes of questions**. Everyone in the team should be there. It does not matter who speaks.

| Criterion | Points |
|---|---|
| The problem, and who it is for | 1 |
| What you built, shown working (a demo or a result) | 1 |
| How you know it works (a test, a check, a comparison) | 1 |
| One design decision or trade-off, and why you made it | 1 |
| Clear, on time, and answers the questions | 1 |

---

## Interview (individual)

One student with the instructor or TA, about **5 minutes**, in the same week as the presentations. No AI, no notes. You can have your team's repository open. The questions are about **your team's project**, and we expect you to understand all of it, not only your own part.

We will ask about some of these:

| Area | Example question | Points |
|---|---|---|
| **Your part** | Walk me through this function you wrote. What does this line do? | 2 |
| **The whole project** | How does the data get from the input to the result? Explain a part a teammate built. | 2 |
| **Scaling** | What happens with 10 times more data? Which step would be slowest? | 2 |
| **Testing** | What does this test check? What is not tested? | 2 |
| **Decisions and agents** | Why did you choose this design over another? When was the agent wrong, and how did you notice? | 2 |

Each area is scored **2** (clear and correct), **1** (partly), or **0** (cannot explain).

---

## Peer evaluation

Due **Friday Dec 4** with M3. Each person fills in the form on their own. Answers are private to the course staff.

1. Split **100 points** between the members of your team, including yourself, by how much each person contributed.
2. For each teammate, one or two sentences: what did they work on?
3. Anything else we should know (optional).

**How it is used.** Most teams split the work fairly, and then nothing changes. If teammates agree that someone did much less than an equal share, that person's marks for the team parts (M3 and the presentation) are reduced in proportion. Small differences are ignored. We read the comments and the repository history before changing any grade.
