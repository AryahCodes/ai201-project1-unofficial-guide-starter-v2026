# The Unofficial Guide

<!-- Replace this line with your name and which corpus you picked. -->

> **This file is your submission.** Fill it in as you go — most sections get
> written during the milestone that produces them, not at the end.
>
> How the starter works, and every command you'll need, is in `RUNNING.md`.
> Leave that file alone.
>
> **Paste everything as text.** No screenshots, no video. A typed table gets
> full credit; a picture of the same table gets none.
>
> Delete these instruction blocks as you replace them. The `<!-- -->` comments
> are notes to you and don't show up when the page renders — you can leave them
> or remove them.

---

# Unit 1

## What This Does

<!-- Three or four sentences. Which corpus you picked, and the kinds of
     questions your system answers. Write it for someone who has never seen
     this repo.

     Milestone 5. -->

## Chunking Strategy

**Chunk size:** approximately 500 characters maximum
**Overlap:** 0 characters

I used paragraph-aware chunking because the `campus_life` corpus is made up of short posts that are usually only a few paragraphs long. The starter's 800-character fixed-window chunker produced 88 chunks from 88 documents, which showed that most posts were already short enough to stand alone. I chose a target maximum of about 500 characters and split only at paragraph boundaries so sentences and complete thoughts would not be cut in half. I used no overlap because the chunks preserve complete paragraphs instead of cutting through sentences.

## Sample Chunks

**Chunk 1** — source: `admin_add_drop_deadline.txt#0` — produced by: `chunker.py::split_documents`

```text
On the add/drop deadline

You can add a course through the end of the second week. Dropping is a longer window — through the end of week six — but a drop after week two shows as a W on your transcript. Nothing anywhere on the registrar's site says this plainly, and students find out from each other.
```

**Chunk 2** — source: `course_biol_160_exams.txt#0` — produced by: `chunker.py::split_documents`

```text
BIOL 160 Cell Biology — assessment

Four unit tests and a cumulative final. Not curved.

The unit tests come fast, roughly every three weeks; falling behind once is very hard to recover from.
```

**Chunk 3** — source: `course_math_220_exams.txt#0` — produced by: `chunker.py::split_documents`

```text
MATH 220 Linear Algebra — assessment

Two midterms and a cumulative final. Curved to a b- median.

The problem sets are the course; the lectures make sense afterwards rather than during.
```

**Chunk 4** — source: `dining_the_ridgeway_cafe.txt#0` — produced by: `chunker.py::split_documents`

```text
The Ridgeway Café

Second-year here. Wait times: 10 to 15 minutes at 12:30, none after 2:00. The thing worth going for is the only place on campus with real espresso. The thing to know is that seating is tight; about 40 seats for a building of 900.

Hours are 7:00am to 4:00pm weekdays only. Costs declining balance only, no meal swipes.
```

**Chunk 5** — source: `housing_morrow_house.txt#0` — produced by: `chunker.py::split_documents`

```text
Morrow House — what it's actually like

Just finished a year in this building. Built 1954, partially renovated 2008. Rooms are singles and doubles, hall bathrooms.

The good: cheapest housing tier by about $900 a year, and the singles are real singles.

The bad: known damp problem on the ground floor; two rooms were taken offline in 2024.

Laundry costs $1.50 wash, $1.25 dry, coin or card. On noise: loud until about 1am on weekends, no enforced quiet hours.
```


<!-- One complete question and answer, pasted as text, with the source line
     visible. Milestone 4. -->

**Question:**

**Answer:**

```
```

**My relevance cutoff:** `0.6`

I kept the relevance cutoff at 0.6 because there was a clear gap between questions covered by the corpus and questions outside the corpus. My five in-corpus questions had best distances from 0.2197 to 0.4307, while the five out-of-scope questions had best distances from 0.8246 to 0.9340. A cutoff of 0.6 falls well between those groups, allowing all five in-corpus questions through while rejecting all five out-of-scope questions.

| Question                                                                            | In corpus? | Best distance |
| ----------------------------------------------------------------------------------- | ---------- | ------------: |
| Which part of Innisfree Hall is quieter?                                            | Yes        |        0.2925 |
| How long are wait times at Kestrel Commons between 12:15 and 1:00?                  | Yes        |        0.2197 |
| How many hours per week does CS 340 take during the last three weeks of the course? | Yes        |        0.3132 |
| How late is the library open during the regular term?                               | Yes        |        0.4307 |
| How far in advance should students book an adviser before registration?             | Yes        |        0.3586 |
| What is the capital of Mongolia?                                                    | No         |        0.8246 |
| How do I change the oil in a diesel engine?                                         | No         |        0.9340 |
| Who won the 1994 World Cup?                                                         | No         |        0.8859 |
| What is the recommended dosage of ibuprofen for a headache?                         | No         |        0.8442 |
| How do I write a for loop in Rust?                                                  | No         |        0.8960 |


## Sample Answer

**Question:** Which part of Innisfree Hall is quieter?

**Answer:**

```text
Based on the provided documents, the short wing of Innisfree Hall is much quieter (housing_innisfree_hall_noise.txt).

Sources retrieved: housing_fenwick_court_noise.txt, housing_innisfree_hall.txt, housing_innisfree_hall_noise.txt, housing_old_brewhouse_noise.txt, housing_tamsin_court_noise.txt
```

**My relevance cutoff:** `0.6`

I kept the relevance cutoff at 0.6 because there was a clear gap between questions covered by the corpus and questions outside the corpus. My five in-corpus questions had best distances from 0.2197 to 0.4307, while the five out-of-scope questions had best distances from 0.8246 to 0.9340. A cutoff of 0.6 falls between those groups, allowing all five in-corpus questions through while rejecting all five out-of-scope questions.

| Question                                                                            | In corpus? | Best distance |
| ----------------------------------------------------------------------------------- | ---------- | ------------: |
| Which part of Innisfree Hall is quieter?                                            | Yes        |        0.2925 |
| How long are wait times at Kestrel Commons between 12:15 and 1:00?                  | Yes        |        0.2197 |
| How many hours per week does CS 340 take during the last three weeks of the course? | Yes        |        0.3132 |
| How late is the library open during the regular term?                               | Yes        |        0.4307 |
| How far in advance should students book an adviser before registration?             | Yes        |        0.3586 |
| What is the capital of Mongolia?                                                    | No         |        0.8246 |
| How do I change the oil in a diesel engine?                                         | No         |        0.9340 |
| Who won the 1994 World Cup?                                                         | No         |        0.8859 |
| What is the recommended dosage of ibuprofen for a headache?                         | No         |        0.8442 |
| How do I write a for loop in Rust?                                                  | No         |        0.8960 |

**Aryahvishwa Babu — Corpus: `campus_life`**

## What This Does

The Unofficial Guide is a retrieval-based question-answering system built on the `campus_life` corpus. It searches short student-written documents about housing, dining, courses, studying, registration, and other parts of campus life. The system retrieves relevant document chunks, checks whether the best result is relevant enough to answer, and then generates an answer using only the retrieved documents. Answers include their source documents, and questions outside the corpus are rejected by the relevance gate instead of being answered from the model's general knowledge.

## How I Used AI

**1.** I asked AI for help designing a chunking strategy after I saw that the starter's 800-character chunker produced 88 chunks from 88 short `campus_life` documents. It suggested using paragraph-aware chunks with a target maximum of about 500 characters and no overlap so complete thoughts would stay together. I implemented that strategy in `split_documents` and then checked the actual output myself. The new chunker produced 90 chunks, and I inspected five sampled chunks to confirm that they were complete and readable on their own.

**2.** I used AI to help interpret the retrieval-distance results when choosing my relevance cutoff. I provided the five in-corpus distances and five out-of-scope distances, and it pointed out the clear separation between the groups. I kept the cutoff at `0.6` after verifying that my in-corpus questions ranged from 0.2197 to 0.4307 while the out-of-scope questions ranged from 0.8246 to 0.9340. I did not change the cutoff just because the starter used 0.6; I kept it because my own retrieval results showed that it fell safely between the two groups.
