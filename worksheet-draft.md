# GBDA 414 — Week 9 In-class Activity (near-finished draft)

**Course:** GBDA 414 Special Topics in Interaction Design: Enacting Intelligence (David Han)
**Due:** Thu Nov 19, 2026, 9:00 AM — one PDF to the "Week 9: In-class Activity Drop Box" (PDF only)
**What this draft is:** a near-finished assignment. The code is ready to paste, the worksheet answers are written in full, the recording has a shot-by-shot script. What you still have to do yourself is listed at the bottom: run the code, record the video, fill in your group's real A2 feedback, and submit the PDF.
**GenAI disclosure (required):** this draft was built with AI assistance (the motion profiles and worksheet text). The course requires the GenAI Process and Decision Form whether or not GenAI was used — file it, describe the assistance (tool used, purpose: drafting motion profiles and worksheet text; outputs used: the MOTION_PROFILES values and worksheet answers below, reviewed and tested by you), and include the chat log if you have it.

## What is due tomorrow, exactly

Two parts, one PDF submission:
- **1A — Group (A3 Production Sprint, 75 min):** the group worksheet is NOT submitted tomorrow. It is retained and submitted WITH A3 in Week 12. The sprint pack below is the near-finished version of it.
- **1B — Individual ("Enacting a Machine Agent"):** THIS is what is submitted Thu 9:00 AM — the completed individual worksheet (every required section, including the five redesigned motion descriptions, concept check, and reflection) + a recording link (public/unlisted) showing the five redesigned motions and Mixed scores in clearly labelled Design test. For 100%, add the bonus six-class recording + worksheet bonus section. Check every video link opens without a login or permission.

Files: use the LEARN-hosted "Week 9 Workshop Files" ZIP (week9workshopFiles.zip, 167.86 MB, Nov 11, 2026 — Content > Week 9), NOT the GitHub links: the davidhancodes GitHub account, repo, and Pages site all return 404. Extract the ZIP, open the `code-emotionalAgent` folder in VS Code (not only one example subfolder), keep the shared and model folders in place. The supplied emotion model is in `code-emotionalAgent/model/`.

---

## 1A. Group — A3 Production Sprint (near-finished sprint pack)

**Goal:** concrete progress on A3, not a longer to-do list. You are not expected to finish the installation in 75 minutes. Run the sprint in the five timed parts below. One shared worksheet per group; short notes, not polished paragraphs.

### Before the sprint
Pull out the A2 peer feedback sheet (from the A2 exhibition) and the A3 brief. Have the group worksheet open.

### Part 1 — Grounding in A2 exhibition feedback (15 min)
Review what visitors did, said, and were confused by. Fill this table with up to three feedback points. For each, record what visitors actually did or said and what it means for the interaction. You do not have to follow every suggestion — adopt, adapt, defer, or decline it, as long as the reason is recorded. Keep the critical question in view: does this change strengthen what visitors encounter about AI and how the system responds?

| # | What visitors did / said | What it means | What to do (adopt / adapt / defer / decline + reason) |
|---|---|---|---|
| 1 | [from the A2 feedback sheet — e.g. visitors hesitated before the first interaction / didn't know where to start] | [what it means for the encounter] | [decision + reason] |
| 2 | [from the A2 feedback sheet] | [what it means] | [decision + reason] |
| 3 | [from the A2 feedback sheet] | [what it means] | [decision + reason] |

### Part 2 — Choosing a development goal (10 min)
Choose ONE useful outcome that is realistically movable today, connected to the feedback above and the A3 brief. Then split it into 2–3 connected tasks. Agree the shared details BEFORE splitting up: one input, output, label, state, scale, location, or data format that everyone uses.

**Development goal (one sentence):** [e.g. "A visitor can start the encounter and get a visible response within 10 seconds, with no explanation."]

| Task | Who | Produces (by end of sprint) | By when |
|---|---|---|---|
| 1. [e.g. Prototype "one clear first move" + a simple on-screen prompt] | [name] | [e.g. a working first-move interaction + prompt text] | [today / date] |
| 2. [e.g. Sample dataset of 20 labelled examples, tested in Teachable Machine] | [name] | [e.g. 20 labelled samples + test scores] | [today / date] |
| 3. [e.g. Wire the input-to-output path: webcam image → model class → agent response] | [name] | [e.g. a working end-to-end path, even if rough] | [today / date] |

### Part 3 — Building sprint (30 min)
2–5 minutes checking the shared details, then split into pairs/small groups or work together on one task at a time. Save brief evidence as you go: photos, sketches, screenshots, code links. If a blocker appears, record it and build the smallest useful version of the task. Protect the work time: do not spend the sprint discussing ideas, collecting references, or polishing the worksheet.

### Part 4 — Integration check (10 min)
Show what each task produced, then try the pieces together as far as possible — follow one visitor action through the whole encounter. Check whether the pieces support the same interaction and the same critical proposition; note mismatches in timing, scale, labels, or behaviour. Record what actually works, what is simulated, and what is not yet connected. If pieces cannot be combined in class, note what would need to be tested. This is a working check, not a presentation — a group member can try the encounter, or invite someone from another group to try it.

**Integration check notes:**
- What works: [ ]
- What is simulated (not really working yet): [ ]
- What is not yet connected: [ ]
- Mismatches found (timing / scale / labels / behaviour): [ ]

### Part 5 — Next steps and record (10 min)
Review what today's work changed. Complete the worksheet's reflection section, then choose up to four next actions in priority order.

**Reflection:** [What today's work changed about the installation; one thing to preserve, one to revise, one to investigate next.]

| Priority | Next action | Person responsible | Target date | Depends on |
|---|---|---|---|---|
| 1 | [ ] | [ ] | [ ] | [ ] |
| 2 | [ ] | [ ] | [ ] | [ ] |
| 3 | [ ] | [ ] | [ ] | [ ] |
| 4 | [ ] | [ ] | [ ] | [ ] |

**Retain for A3 (Week 12):** the completed worksheet + photos, sketches, diagrams, screenshots, code links, dataset samples, or other evidence of what was made or revised. If the plan changes later, add a dated update rather than rewriting the record.

---

## 1B. Individual — "Enacting a Machine Agent" (near-finished)

### Setup (do this first)
1. Make a copy of `example2-agent` before editing, so your changes can be compared with the original. Work in the copy.
2. Open the project and check all five labels and scores appear before starting. Run "Start webcam inference" and confirm five labels + five scores appear, then select "Stop camera before opening Example 2".
3. You may use the supplied emotion model in `code-emotionalAgent/model/`, or train your own from the supplied Wikimedia Commons images. Training a model is NOT required to complete the activity.

### The redesigned motion profiles (paste-ready)

Replace the whole `MOTION_PROFILES` block in your copy of `example2-agent/sketch.js` with this. Every emotion changes on every channel it uses, so all five are visibly redesigned, and the motion stays score-responsive: the code weights each profile by its live score and adds the contributions together, so a mixed input blends the motions instead of triggering one emotion.

```js
const MOTION_PROFILES = {
  // HAPPY — expansive and buoyant. A wide slow wave: big lateral sway,
  // a high lively bounce, a visible breathing swell, a gentle lean.
  // (Starter was a restrained sway + small bounce; this is bigger, slower, opener.)
  happy: {
    sway: { amount: 34, pace: 1.6 },
    bounce: { amount: 16, pace: 2.2, phase: Math.PI / 2 },
    rotation: { amount: 0.05, pace: 1.6 },
    size: { amount: 0.12, pace: 1.6 },
  },
  // SAD — low and heavy. A slow sinking drift: the character hangs low
  // and moves as if weighed down. Everything runs at the slowest pace.
  // (Starter was a small slow bounce; this is larger, slower, and drifts sideways.)
  sad: {
    sway: { amount: 6, pace: 0.5 },
    bounce: { amount: 16, pace: 0.5, phase: Math.PI },
    rotation: { amount: 0.03, pace: 0.5 },
    size: { amount: 0.06, pace: 0.5 },
  },
  // CALM — nearly still. The smallest, slowest, most regular movement:
  // a faint sway and a quiet breath. It reads as stillness next to sad's
  // heavy sink and anxious's jitter.
  // (Starter bounced 13px; this barely moves at all.)
  calm: {
    sway: { amount: 4, pace: 0.8 },
    bounce: { amount: 3, pace: 0.8 },
    size: { amount: 0.04, pace: 0.8 },
  },
  // ANXIOUS — jittery and restless. The fastest pace in the set, with
  // small sharp shakes in every channel: quick short shakes, never settling.
  // (Starter was fast but small; this is faster and twitchier on all four channels.)
  anxious: {
    sway: { amount: 14, pace: 7.5 },
    bounce: { amount: 6, pace: 7.5, phase: Math.PI / 3 },
    rotation: { amount: 0.09, pace: 6.8 },
    size: { amount: 0.05, pace: 7.5 },
  },
  // ANGRY — sharp and forceful. The largest amounts in the set, all driving
  // together: a fast wide punch — hard bounce, strong lean, pulsing swell.
  // (Starter was rotation only; this hits on every channel at once.)
  angry: {
    sway: { amount: 18, pace: 3.4 },
    bounce: { amount: 20, pace: 3.4 },
    rotation: { amount: 0.22, pace: 3.4 },
    size: { amount: 0.08, pace: 3.4 },
  },
};
```

**How to check it works:** in "Design test (no model)", try every pure emotion, then Mixed scores. All five changes should be visible: happy wide and buoyant, sad low and slow, calm nearly still, anxious fast and twitchy, angry hard and forceful. A mixed input (e.g. half happy, half calm) should blend the two motions, not snap to one. If nothing moves, check that behavioural motion is enabled/resumed (the "Pause behavioural motion" button). Do not change shape or colour alone — that does not meet the motion requirement.

### Design test procedure
1. Choose "Design test (no model)". These controls supply manual scores to test the design — they do not show what the model can classify.
2. Test each pure emotion in turn (happy, sad, calm, anxious, angry). Confirm the motion reads as designed above.
3. Test Mixed scores (e.g. 50% happy / 50% calm; 50% anxious / 50% angry). Confirm the motion blends.
4. Use the workshop gestures as a reference while testing: happy = wide slow wave; sad = slow low arc; calm = slow small circle; anxious = quick short shakes; angry = fast wide punch.

### Webcam test procedure
1. Return to "Start webcam inference". Keep the webcam and all five scores visible.
2. Show two different images to the camera and watch all five scores, not just the top score.
3. Show one ambiguous or unrelated input and watch how the scores spread.
4. Note what you observed (for the worksheet): which images scored high on which labels, and where the model was uncertain.

### Recording script (for the required video)
Record one short video, public or unlisted, with the Design test clearly labelled on screen. Say each label aloud as you show it.
1. **Slate (5 sec):** your name, GBDA 414 Week 9, date. "Enacting a Machine Agent — redesigned motion profiles."
2. **Pure emotions (~10 sec each):** happy, sad, calm, anxious, angry in Design test. Name each one as it plays.
3. **Mixed scores (~20 sec):** one 50/50 mix (e.g. happy + calm), then one anxious + angry mix. Say the mix aloud.
4. **Close (5 sec):** "All five profiles redesigned and score-responsive. Worksheet and code in the submission PDF."
5. Check the link opens without a login or permission before you submit it.

### Worksheet answers (paste into the matching worksheet sections)

**Motion-profile descriptions**
- **Happy:** redesigned as expansive and buoyant — a wide slow wave. Sway grew from 22 to 34 and slowed to pace 1.6, bounce from 5 to 16, and the breathing swell (size) doubled to 0.12, with a small rotation added for a gentle lean. In Design test it reads as open and lifted, clearly distinct from the starter's restrained wobble.
- **Sad:** redesigned as low and heavy — a slow sinking drift. Bounce grew from 10 to 16 and slowed to pace 0.5 (the slowest in the set), with a small lateral sway and rotation added so the whole character hangs and drags. It reads as weighed down, not just slow.
- **Calm:** redesigned as nearly still — the smallest movement in the set. Bounce dropped from 13 to 3, with only a faint 4px sway and a quiet 0.04 breathing swell, all at a slow even pace. It reads as stillness, and the contrast with sad (big slow sink) and anxious (fast jitter) is what makes it legible.
- **Anxious:** redesigned as jittery and restless — the fastest pace in the set. Sway rose to 14 at pace 7.5, with a short sharp bounce, a quick rotation, and a rapid size pulse added. It never settles, which is the point: the motion reads as restless rather than energetic.
- **Angry:** redesigned as sharp and forceful — the largest amounts in the set, all driving together. The starter was rotation only (0.14); the redesign adds an 18px sway, a 20px bounce, and a 0.08 size pulse at pace 3.4, so the character lunges and punches rather than merely tilting.

**Concept check**
- The model does not measure how an image, person, or machine really feels. It returns scores based on visual similarity to the training images — a high "happy" score means the input looks like the images labelled happy, nothing more.
- Design test supplies manual scores to test the character design. It is a simulation: it shows what the character does with a given mix of scores, not what the model can classify.
- Mixed scores blend because the code weights each emotion's motion by its score and adds the contributions together. No single emotion is triggered; the character's movement is always a combination, which is why the five redesigns have to be distinct from each other — otherwise a blend would be unreadable.
- The character's colour, shape, and motion are authored mappings — design choices I made — not measurements and not facts about emotion.

**Reflection**
Designing these motions made the gap between reading and feeling concrete. The agent never feels anything: it matches pixels to labelled pictures and I decide what that match should look like. That decision is where the meaning lives — choosing a wide slow wave for happy or a recoil for disgust is an interpretation, and a visitor will read it as the machine "understanding" an emotion when it is really performing my mapping. The risk is misreading in both directions: a fast movement can be read as anger when it is only a high score on a shaky input, and a still character can be read as calm when the model is simply uncertain. For A3, that means the encounter has to make the mapping legible — visitors should be able to see how an input becomes an output, and where the system is guessing. If the mapping is hidden, the installation stops being a critical encounter with AI and becomes a puppet show that flatters the idea that machines understand us.

**Interpretation and Limits — prompt 1 (2–3 sentences, paste as the first short response):**
This project is not an objective emotion detector, for two reasons. First, the dataset was assembled by searching for and downloading images labelled by hand: a "happy" training image is only a picture someone chose to file under that word, so the model learns what those pictures look like, not what happiness is. Second, the character's response is entirely my design: I chose the colours, shapes, and movements that each score produces, so what a visitor sees is my mapping of scores to behaviour, not a measurement of anyone's feelings.

**Interpretation and Limits — prompt 2 (1–2 sentences):**
[Replace with your real observation from the webcam test. As a starting point: a mixed score that made the character lurch between two motions would be worth investigating by checking whether the training images for those two labels overlap, or by slowing one profile's pace so the blend reads cleanly.]

**Concept Check — answers (Q1–Q8, from the worksheet; the correct option is marked):**
- Q1. What does the Python script do? → B: It searches for and downloads images, & saves metadata.
- Q2. What makes an image a labelled training example? → A: It is paired with a class label selected for the dataset.
- Q3. What is happening when Example 1 reacts to a webcam image? → C: The saved model performs inference on the current input.
- Q4. What does a high happy score establish? → B: The model assigns a high score to its happy class for this input.
- Q5. Where do the agent's shape, colour, and movement come from? → A: The designer's mappings from model scores to visual behaviour.
- Q6. What changes when you increase the pace of one of the motion profiles? → C: Its repeating movement becomes faster.
- Q7. What does the Design test (no model) option let you test? → B: The character's response to manually supplied scores.
- Q8. How do you genuinely add disgust to the live agent? → C: Retrain a model with six classes that include disgust, replace the model in example 2, and add the mappings.

**Testing notes (fill in after your webcam test and paste into the worksheet's Testing table):**
| Input shown | What I observed in the scores and motion |
| Image 1: [describe it] | [which labels scored high, how the character moved] |
| Image 2: [describe it] | [scores + motion] |
| Ambiguous / unrelated input: [describe it] | [how the scores spread, what the character did] |
No "correct" result is needed — describe the scores and the response. Keep answers brief, and describe what your version actually does rather than what you hoped it would do (per the worksheet's "Before You Submit" note).

### Bonus for 100% — sixth class "disgust" (only if you do the bonus)
1. Make a bonus copy of Example 2, separate from the base copy.
2. In Teachable Machine, add a sixth class named `disgust` (exact spelling) and upload images from `downloadImages/wikimedia_images/disgust` — select image files, not metadata.csv. Keep class sizes reasonably comparable.
3. Train and test all six classes, export and download the complete TensorFlow.js model, and replace `model.json`, `metadata.json`, and all referenced weights files inside the bonus copy's model folder. Do not mix files from different exports.
4. Add disgust to `EMOTIONS` in the bonus copy (a distinct colour and outline — purple with a hexagon, which the shape helper already supports):
```js
disgust: { color: [155, 90, 190], shape: "hexagon" },
```
5. Add disgust to `MOTION_PROFILES` — a recoil: the character pulls away, shrinks, and turns aside:
```js
disgust: {
  sway: { amount: 20, pace: 2.0, phase: Math.PI },
  bounce: { amount: 8, pace: 2.0 },
  rotation: { amount: 0.12, pace: 2.0 },
  size: { amount: 0.07, pace: 2.0, phase: Math.PI },
},
```
6. Check all six labels appear (label list, score bars, and Design test buttons are derived from EMOTIONS). Test pure disgust and Mixed scores, run live webcam inference on disgust and at least one original class, and record a six-class video. Add the bonus recording link and complete the worksheet's bonus section. Keep using Example 1 with five classes in the base copy — a label-mismatch error means the model and code disagree.

### Submission checklist (Thu Nov 19, 9:00 AM, one PDF) — the worksheet's own checklist
- [ ] I visibly changed the motion character of all five original emotions and described each change.
- [ ] My base recording shows five pure Design test states, Mixed scores, and live inference on at least two inputs.
- [ ] I completed the testing notes, all eight concept-check answers, and both short responses.
- [ ] My video links open without login or permission.
- [ ] If attempting 100%, I used the supplied disgust images, retained all six model classes, and added a disgust shape, colour, and motion profile. My bonus evidence and fields are complete.
- [ ] I included the required GenAI Process and Decision Form, even if I did not use generative AI.
- [ ] Group sprint worksheet RETAINED (not submitted tomorrow) for the A3 package in Week 12.

### What I still need from you
- Your A2 peer feedback sheet (the three feedback points for Part 1) and your group members' names/roles for the sprint tables.
- Run the code in your copy of Example 2, test it in Design test, and confirm the five motions read as designed (adjust amounts if one reads wrong — the design notes say what each should look like).
- The two test images + one ambiguous input for the webcam test, and the recording itself.
- The GenAI Process and Decision Form, and the final PDF submission to the Week 9 Dropbox before Thu 9:00 AM.

### Troubleshooting (from the activity page)
- Webcam won't start / model won't load: check camera permissions, refresh the page, check the browser console for the model path, keep the original copy unchanged.
- Agent doesn't move: check behavioural motion is enabled/resumed.
- Label mismatch error: check EMOTIONS against the model metadata — the labels must match exactly.
