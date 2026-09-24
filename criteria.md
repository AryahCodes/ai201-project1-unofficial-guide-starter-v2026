# Acceptance criteria — The Unofficial Guide

Five criteria that say what "working" means for this system, written in unit 1
**before** any results existed.

An acceptance criterion names a target: a number, a count, a rate, or something
a person could plainly observe. *"Retrieval works"* is an opinion. *"For at
least 4 of my 5 test questions, the top results include a chunk containing the
answer"* is a criterion.

Under each one, write a sentence or two on **why that target** and not a
stricter or looser one. A reason that says something about your corpus or your
pipeline earns credit; *"80% seemed reasonable"* does not.

> Missing your own targets next unit costs you nothing. Setting a target so
> easy you can't miss it does.

### Criterion 1 — Why this target

The `campus_life` corpus contains short posts where most useful information is concentrated in one document, so I expect retrieval to find the answer for most of my specific questions. I chose 4 of 5 instead of 5 of 5 because one question could still retrieve a closely related post instead of the exact one.

### Criterion 2 — Why this target

Every generated answer should name a source because the system already keeps track of the documents used during retrieval. Requiring all answers to include a source makes it possible to check where each answer came from instead of trusting the generated response by itself.

### Criterion 3 — Why this target

The five out-of-scope questions are completely unrelated to campus life, so the relevance gate should reject almost all of them. I chose 4 of 5 because similarity search can occasionally return an unrelated chunk that is still close enough to pass the cutoff.


## 4. Something about your chunks

At least 4 of 5 sampled chunks should read as a complete thought on their own, with no sentence cut off at the beginning or end.

**Why this target:**

The `campus_life` documents are short posts, and my current indexing produced 88 chunks from 88 documents, so most posts already fit naturally into a single chunk. I chose 4 of 5 because I want the chunker to preserve that context while still allowing for an occasional post that may need to be split.

---

## 5. Answers contain the expected fact and correct source

For at least 4 of my 5 test questions, the generated answer should contain the expected fact listed in `questions.py` and cite the document that contains that fact.

**Why this target:**

Retrieving a relevant chunk is not enough if the final answer leaves out the important fact or cites the wrong source. I chose 4 of 5 because I expect the system to answer most of my specific test questions correctly while still leaving room for one retrieval or generation failure.



---

<!-- ─────────────────────────────────────────────────────────────────────────
     UNIT 2 — read this before you change anything above.

     If a criterion turns out to be BROKEN rather than merely unmet, you can
     revise it, and that earns credit. But never delete or edit the original
     line. Add the revision underneath it, like this:

         ## 1. Retrieved chunks contain the answer

         For at least 4 of my 5 test questions, the retrieved chunks include
         one that contains the answer.

         **Why this target:** ...

         > **Revised in unit 2:** For at least 4 of 5 questions, the top three
         > results contain the answer.
         >
         > **Why revised:** I couldn't judge "the chunks include one that
         > contains the answer" the same way twice — I scored two questions
         > differently on Monday than on Wednesday. The new version is
         > something I can actually check.

     That's a revision because the criterion couldn't be MEASURED.

     Lowering a target because you missed it is not a revision, and it costs
     you the point:

         ✗ "I said 4 of 5 but got 2 of 5, so 2 of 5 is more realistic."

     A number you missed stays where it is, gets diagnosed, and gets a fix
     attempted. That's where the points are.

     The whole reason the originals stay visible is so someone can see what you
     said before you knew the answer.
     ───────────────────────────────────────────────────────────────────────── -->
