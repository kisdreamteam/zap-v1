# Phase B — Product Flow (Draft)

> Not yet shaped under Phase B workflow.
>
> Related: [Phase A/problem-definition.md](Phase%20A/problem-definition.md) · [Phase A/product-boundaries.md](Phase%20A/product-boundaries.md)

---

## V1 Product Flow

### Landing

Teacher sees:

* New Story
* Saved Stories

---

### New Story Wizard

Teacher is guided step-by-step:

1. Choose template or blank story
2. Add characters
3. Add setting
4. Add options
5. Start story

---

### Story Options

V1 includes:

* Theme, optional
* Style, optional
* Creativity mode:
  * Safe
  * Balanced
  * Wild

---

### Story Workspace

The app shows:

* current scene
* optional discussion prompts
* 3 choices
* teacher controls

Teacher can:

* select Choice A/B/C
* regenerate choices
* enter custom choice
* continue story
* end story

---

### Story Length

V1 uses a hybrid structure:

* minimum 3 choice rounds
* maximum 5 choice rounds
* teacher can end after round 3

---

### Completion

At the end:

* AI creates a conclusion
* app shows a combined story view
* story is saved

---

## Story Visibility

V1 uses a hybrid display:

### During Creation

Card-based scenes:

* Opening
* Round 1
* Round 2
* Round 3

This helps classroom navigation.

### After Completion

Single combined story view.

This makes the story easy to reread later.

---

## Saving Stories

V1 should save stories using Supabase.

For V1:

* saved stories are read-only archives
* teachers can reopen and read them
* teachers cannot continue or fork them

Future version:

* continue story
* fork story
* alternate endings
* branching paths

---

## Discussion Prompts

V1 should include optional discussion prompts.

Example:

> Ask your students:
> What do you think will happen next?

These are optional, not forced.

Purpose:

* help new teachers
* reduce dead silence
* support discussion
* keep the activity classroom-centered

---

## Generation Speed

> Generate one step ahead when possible.

Reason:

In a projected classroom activity, waiting kills energy.

Technical principle:

> Minimize classroom dead air.

This may require simple prefetching, but not an overcomplicated background system.
