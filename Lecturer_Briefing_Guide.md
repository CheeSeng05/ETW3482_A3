---
description: Key points from the lecturer's A3 briefing video that the instruction PDF and rubric don't already state, plus answers to the groundwork thread's open questions. Read before writing the A3 report or scoring.
---
# A3 lecturer briefing: what it adds beyond the brief and rubric

Source: lecturer's A3 briefing transcript (uploaded 2026-10-19). Points already stated explicitly in the instruction PDF or rubric are left out. Timestamps are from the recording.

## Overall
- The instructions outrank the rubric. The rubric is a marker's tool; markers still check every instruction requirement even if the rubric doesn't mention it (1:04:33).
- The aim is to show you're a "mature modeller", not a trial-and-error one: for every setting you change, say what it does to the model (more complex, more overfit, more non-linear, able to catch a specific relationship) and what the result says about the data (11:20–15:17).
- Example of the expected reasoning: a smaller tree beating a larger tree means the target–input relationship isn't very complicated (11:51).

## Pipeline (one pipeline only)
- You may build several sandbox pipelines to experiment, but the report shows ONLY the final pipeline. Screenshots of other pipelines go against the instructions and can lose marks (54:06, 1:07:43).
- No limit on nodes; 20+ is fine (1:08:39). Every taught model needs at least one node; more per model is up to your strategy (26:08).
- Delete or ignore the experiment nodes. The technical manager wants what you discovered, not the exploration process (55:11).
- Changes to A2 preprocessing nodes are allowed, aren't assessed, and don't need to be reported (6:44, 58:20).

## Section 1
- Not assessed; it only orients the marker, who won't go back to your A2. Keep it short (25:11).

## Section 2: hyperparameter investigation
- Don't try every hyperparameter. Adjust one or two that push the model in a clear direction (more/less complex, more/less flexible) and see if the data rewards it (27:14).
- Changing one or several hyperparameters at once are both fine. What matters is that the changes all push the model the same way (e.g. depth up + leaf size change both to grow a bigger tree). Changes that pull in opposite directions are hard to explain (51:22).
- A family that clearly doesn't suit the data can stay at one node, if you explain why. Example: regression and decision tree both lose to the neural network, so the relationship is non-linear, so one regression node is enough and effort goes into the non-linear models (59:44).
- Present the final nodes as a clean "storyline", not as the trial-and-error path (56:27).

## Section 3: champion
- Model Studio defaults to KS; change it either in Project Settings (applies to all pipelines) or in the Model Comparison node (that pipeline only) (28:04).
- You can change the metric after running the project, but you must rerun the whole pipeline. Only the data partition can't be changed later (1:08:55).

## Section 4.1: performance chart
- One chart only, "not too greedy" (29:29). He won't say which chart; revise what each chart (lift, gain, response, ROC, misclassification) is used for from the slides and videos (30:46, 58:48).
- Example he gave: lift shows how the model compares with random selection (29:57).

## Section 4.2: interpretability
- Turn the tools on in the champion's properties panel (bottom of the panel), as in the Week 10 SVM tutorial: variable importance, PD, ICE, LIME, HyperSHAP. Pick only the few that answer the questions (31:42, 1:00:56).
- Even a white-box champion (decision tree, logistic regression) must be interpreted with the interpretability tools, not its own coefficients or splits. Inputs kept by a predictive model aren't necessarily significant; they're there because they help prediction. Doing it from coefficients means the grade "should not be more than credit" (33:45, 1:01:48).
- "Predictor" is defined in the Week 4 slides; "influential predictor" in Week 10 (1:13:52).

## Section 5: scoring dataset and scored output
Scoring dataset (input):
- Take the same CSV you uploaded to Model Studio in A2 (19:47, 50:36).
- Pick 100 rows with a mix of yes and no, not mostly one class, so predictions aren't all the same (20:25).
- Choose rows with NO missing values. Missing inputs cause problems when scoring; outliers and skew are fine because the score code applies the transformations (36:46, 56:54).
- Keep every column exactly as in the CSV, including inputs rejected in SAS, with names unchanged. Remove only the target (21:27, 1:05:36). Columns already removed from the CSV itself in A2 can stay removed (1:06:12).
- If there's no ID column, add one as the first column (1 to 100 is enough) (22:20).
- Give the file a simple, short name for uploading to SAS Viya; avoid long names (38:53).

Scored output (submitted CSV):
- It's the dataset Model Manager generates; you download it via SAS Manage Data (1:09:22).
- Don't submit every column. Keep only the few a downstream team (e.g. marketing) needs to act on; a full output table would leave them lost (1:10:19).

## Section 6: strategy
- Build it from the scored output: who is flagged and what you'd do with that list (40:31).
- Consider privacy (don't expose who was flagged) and practical interventions, such as grouping flagged cases for targeted action (41:00).

## Report and admin
- 3,000 words is a hard cap; no 10% leeway, over-length reports may be rejected (42:02).
- Headings and subheadings count toward the words (1:08:20).
- Don't move prose into tables to dodge the word count (42:42).
- Reflection is optional; if included it goes in the appendix (42:34).
- If 3,000 feels short, cut repetition and unfocused points (42:52).
- The template already has the required formatting, so use it as is (43:41).
- All work must be done in SAS Viya Model Studio and Model Manager. Output that looks SAS-like but isn't got very low marks (44:11).
- AI use: no detail beyond the brief and Moodle (44:48).
- The lecturer can't grant extensions or waive late penalties; everything goes through the Monash system (44:54).

## Answers to the groundwork thread's open questions
| Question | Answer from the briefing |
|---|---|
| Stratified 50/50 scoring sample OK? | Yes. He only asks that it's not mostly one class. |
| Scoring rows overlap the modelling data? | Fine. He says to sample from the same 8,000-row CSV. |
| Missing values in scoring rows? | Not addressed in the brief. He says use complete rows only. Our current ETW3482_Scoring.csv has 21 rows with blanks, so it should be regenerated from complete rows before scoring. |
| Report structure (funnel vs model by model) | No preference given. Report only the final pipeline as a clean storyline; the manager wants findings, not the process. |
| Show trial-and-error values or removed nodes? | No. Only nodes in the final pipeline. No screenshots of other pipelines. |
| Variable Selection change from A2 | Allowed. Preprocessing changes aren't assessed and needn't be reported. |
| Is 2–4 settings per model enough? | No set number. At least one node per model; a weak family can stay at one node if justified. |
| Is AUC itself graded? | Not stated. The emphasis is on explaining behaviour, not chasing performance. |
| Top 3 from which importance? | Must come from the interpretability tools (Model Interpretability results), not the model's own internal output. |
| Champion picked via project Rules = software pick? | Changing the metric in Project Settings is one of his two endorsed methods. You still justify the metric yourself. |
| Scored CSV columns | Only the useful ones: ID plus the prediction fields a downstream team needs. Not all inputs. |
| Business cutoff in the file? | Not addressed. |
| AI acknowledgement | Not addressed beyond the brief. |
| Lift/PD on validation or train? | Not addressed. |

---
# Clinic session (second transcript, uploaded 2026-10-19)
Only points not already in the brief, rubric or the briefing above. Timestamps are from the clinic recording.

## Grading focus
- Marks come from the insight you get from the process, not from how well the model performs. Even if every model performs poorly, explaining why with predictive-modelling principles can still earn an HD (15:14).
- Your choices show understanding. For example, if only regression performs well, tuning copies of every model mechanically shows you didn't read the evidence (27:57).
- Results that are surprising or all roughly equal are normal. Explain them rather than chase better numbers (32:24).

## Strategy (Section 2)
- Running all six at defaults, then tuning in a chosen direction, is "one possible strategy". He won't prescribe one (16:33).
- Autotuning or brute-force search is allowed as early sandbox exploration, but it gives no insight. Section 2 still has to explain the behaviour (23:13).
- For each change, say which direction you're moving the model (more flexible or non-linear, smoother, more rigidly linear). If performance improves, the hidden relationship has that shape (25:05).
- Any number of nodes per model is fine (e.g. six SVM nodes) as long as each fits the exploration storyline and is justified (30:52).
- Variable Selection: reporting its criteria is your call. Include it only if you think it tells you something about the target–input relationship (29:31).

## Evidence, tables, appendix
- Evidence must be SAS Viya screenshots, which prove the work was done there (2:37).
- Every table and figure needs a numbered caption (e.g. "Figure 2.1") and must be referred to in the text (5:41).
- Anything you explain in the text belongs in the main body, not the appendix. Making the reader flip to the back is "not appropriate" (8:23).
- The appendix is optional extra material (more model results, code), and each item still needs a pointer in the text (6:26, 9:46).

## References
- References are a must (10:30).
- Non-academic sources are fine: SAS documentation, SAS forums, IBM, YouTube, news, annual reports, government sites (10:58).
- Use APA 7th edition; the Monash Library site has the guide (22:16).

## Template
- Keep the main sections 1–7 exactly as in the template. Subsection headings (2.1, 2.2 …) can be renamed or reorganised to fit your exploration (18:39, 20:27).

## Scoring
- Score through Model Manager as in the Week 10 tutorial. Don't use SAS Studio code or the exported score code unless you're fluent in SAS coding and its library system (0:16, 1:54).

## Admin
- Next week's tutorials are physical clinics, your last chance to ask about results (11:39).

## Groundwork-thread questions this settles
| Question | Answer from the clinic |
|---|---|
| Is AUC itself graded? | No. Insight is graded, not performance. |
| Funnel structure OK? | Yes. Defaults first, then directed tuning, is an endorsed strategy. Rename the 2.x subsections to fit it. |
| Avoid Autotuning / untaught options? | Autotuning is fine as a sandbox only; the report must explain behaviour. Extra nodes or options are fine if justified. |
| Report Variable Selection criteria? | Optional; include only if it informs the target–input relationship. |
| APA citations needed? | Yes, references are required (APA 7). |
| Tables with explanation, appendix role | Explain in the text. The appendix is extras only, referenced from the text. |
