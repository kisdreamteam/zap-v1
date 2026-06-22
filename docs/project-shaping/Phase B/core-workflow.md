# Phase B.4 — Core Workflow Snapshot

> V1 shaping (in progress). Phase A defines product identity; this doc defines workflow and locked V1 decisions.
>
> Related: [Phase A/problem-definition.md](Phase%20A/problem-definition.md) · [Phase A/product-boundaries.md](Phase%20A/product-boundaries.md) · [v1-scope.md](../v1-scope.md) · [product-principles.md](../product-principles.md)

---

## Overview

Zap! is a teacher-controlled, AI-assisted classroom storytelling activity designed for projected classroom use with ESL/EFL students ages 6–8.

**Core question:** "What happens next?"

The story is the vehicle. Engagement is the goal.

The workflow prioritizes:

* classroom discussion
* low preparation
* minimal cognitive load
* rapid classroom pacing
* resilience when AI fails

### Product Identity (from Phase A)

Zap! is:

* a teacher-controlled, AI-assisted classroom storytelling activity
* designed for ESL/EFL teachers of ages 6–8
* projected on a classroom screen
* used with the whole class
* built around discussion and participation

Zap! is not:

* a story generator
* a curriculum platform
* a classroom management system
* a student-facing product

---

## Locked Decisions (Phase B.4)

| # | Topic | Status | Decision |
|---|-------|--------|----------|
| Q1 | Story Visibility | Locked | Only the current scene and three choices are visible on the projector. No full transcript, previous scenes, or story history. |
| Q2 | Choice Flow | Locked | Teacher clicks a choice → new scene → new choices. No confirmation screen, preview screen, or additional clicks. |
| Q3 | Resume Behavior | Locked | Opening a draft goes directly into Story Workspace. No summary screen, resume wizard, or recap page. |
| Q4 | Recovery | Current position | Robust error recovery is desirable but not required for V1. Candidate V2 feature (distinct from basic draft resume in Q3). |
| Q5 | End Story | Locked | Teacher chooses AI Ending or Manual Ending → Review → Complete. |
| Q6 | Regeneration | Locked | Regenerate changes choices only. The current scene never changes. |
| Q7 | Custom Choice | Locked | Custom Choice opens a large text area so teachers can capture full student ideas, not just short commands. |
| Q8 | AI Failure | Locked | Failure screen shows `[ Try Again ]` only. Workspace controls (regenerate, custom choice) remain available during normal flow. |
| Q9 | Dashboard | Locked | Dashboard contains only `+ New Story` and `+ Saved Stories`. |
| Q10 | Onboarding | Locked (V1) | No onboarding in V1. Future: one-time tooltip. |

---

## Principles

1. Teacher authority is always preserved.
2. AI acts as a creative guide, not the decision maker.
3. Classroom momentum is prioritized over perfection.
4. Stories emerge through interaction.
5. Students influence the story through discussion.
6. Drafts can be resumed in V1 (Q3). Robust error recovery is deferred (Q4).
7. Completed stories become classroom artifacts.
8. Every major action should be understandable by a first-time teacher.
9. No single error should permanently interrupt a classroom session.
10. Simplicity is preferred over flexibility whenever possible.

### Emerging Principles

These emerged from workflow decisions and were not explicitly chosen upfront:

1. Classroom momentum beats software elegance.
2. Every extra click must justify itself.
3. Teacher authority beats AI automation.
4. The present matters more than history.
5. Zap! should feel like running a classroom activity, not operating a platform.

---

## User Journey

### Authentication

Users are not allowed directly into the application. All teachers must authenticate.

```text
Landing
├─ Login
├─ Signup
├─ Forgot Password
└─ Reset Password
```

Authentication is required because:

* AI usage has associated costs
* stories are stored
* teacher identity is required
* future integrations are possible

### Dashboard (Q9)

After login, teachers arrive at the Dashboard.

```text
Dashboard

+ New Story
+ Saved Stories
```

The dashboard intentionally remains minimal. It is not a management portal. The teacher wants to start an activity, not manage software.

**Not included:**

* analytics
* usage reports
* teacher widgets
* settings clutter
* admin features

---

## Workflow 1 — Create New Story

> **Validation pending:** Template Selection and Setup Wizard are the current assumed path but still require validation before locking for build.

### Current Assumed Path

```text
Dashboard
    ↓
New Story
    ↓
Template Selection
    ↓
Setup Wizard
    ↓
Opening Scene
    ↓
Story Workspace
```

### Template Selection

The teacher chooses a template or a blank story. This provides a fast starting point while preserving flexibility.

### Setup Wizard

The wizard collects story setup information. Examples may include:

* characters
* setting
* theme (optional)
* style (optional)
* creativity mode
* other story inputs

The wizard is temporary. No story record exists yet.

#### Wizard Abandonment

If the teacher exits during the wizard:

```text
Progress Lost
```

No draft is created. No wizard state is saved.

### Opening Scene and Draft Creation

```text
Setup Wizard
    ↓
Generate Opening Scene
    ↓
Create Draft Story
    ↓
Story Workspace
```

This is the transition point between setup and activity. The opening scene becomes the beginning of the story.

Immediately after the opening scene is successfully generated, the first persistent record is created. This becomes the official draft story.

---

## Story Workspace

The Story Workspace is the heart of Zap!. This is where classroom discussion occurs.

### Layout

```text
------------------------------------------------

Current Story Scene

------------------------------------------------

Discussion Prompt

------------------------------------------------

Choice A

Choice B

Choice C

------------------------------------------------

[ Custom Choice ]

[ Regenerate Choices ]

[ End Story ]

------------------------------------------------
```

### Story Visibility (Q1)

**Visible on the projector:**

* current scene
* three choices

**Not visible:**

* full story transcript
* previous scenes
* long story history

Reason: projector readability. The present matters more than history.

### Core Loop

```text
AI presents situation
        ↓
AI proposes actions
        ↓
Students discuss
        ↓
Teacher chooses
        ↓
AI continues
        ↓
Repeat
```

This loop continues until the teacher decides to end the story.

### Discussion Prompts (locked)

Discussion prompts are always visible. They should remain concise and easy to read.

Purpose:

* help inexperienced teachers
* encourage discussion
* reduce classroom silence
* support participation

### Choices (Q2)

The AI always presents three choices:

```text
Choice A
Choice B
Choice C
```

These choices represent possible directions for the story. Students discuss the options. The teacher decides.

When the teacher selects a choice:

```text
Teacher Clicks Choice
        ↓
AI Generates Next Scene
        ↓
Auto Save
        ↓
Display New Scene
        ↓
Display New Choices
```

There is no confirmation screen, no preview screen, and no additional clicks. The goal is to minimize classroom dead air.

### Custom Choice (Q7)

Teachers may override AI suggestions. Selecting **Custom Choice** opens:

```text
Custom Direction

[ Large Text Area ]

[ Submit ]
[ Cancel ]
```

The teacher may enter any story direction. Example:

```text
The dragon becomes friendly and joins the picnic.
```

The AI then continues the story from that direction.

### Regenerate Choices (Q6)

Teachers may regenerate choices at any time.

```text
Current Scene
        ↓
Regenerate Choices
        ↓
New Choices
```

Only the choices change. The current scene remains unchanged.

```text
History is fixed.
Future is flexible.
```

---

## Story Lifecycle

### Auto Saving

The story automatically saves:

* after opening scene generation
* after every story round
* after every successful continuation

Teachers never manually save progress.

### Draft vs Completed States

Stories in progress remain drafts.

```text
Draft
    ↓
In Progress
    ↓
Completed
```

### Story Length

The teacher may end a story at any time. There is no minimum length and no maximum length.

The system may recommend approximately 3–5 rounds, but does not enforce it. Teacher authority always wins.

### Ending and Completion (Q5)

When the teacher clicks **End Story**, they choose how the story concludes:

```text
Teacher Clicks End Story
        ↓
    ┌───────────────┴───────────────┐
    ↓                               ↓
AI Ending                      Manual Ending
    ↓                               ↓
AI Generates Conclusion    Teacher Writes Ending
    └───────────────┬───────────────┘
                    ↓
            Review Screen
                    ↓
        Teacher Clicks Complete
                    ↓
        Story Marked Complete
```

Manual ending preserves teacher authority when the class already knows how the story should end.

Stories are not automatically completed. The teacher explicitly confirms completion.

---

## Workflow 2 — Saved Stories

```text
Dashboard
    ↓
Saved Stories
```

Saved Stories contains:

```text
Saved Stories

├─ Draft Stories
└─ Completed Stories
```

### Draft Stories (Q3)

Draft stories may be resumed directly into Story Workspace.

```text
Draft Stories
    ↓
Open Draft
    ↓
Story Workspace
```

No summary screen, resume wizard, or recap page. The teacher wants to continue immediately.

Regenerate Choices remains available inside the workspace after resume — not as a gate before entry.

### Completed Stories

Completed stories are archives.

```text
Completed Stories
    ↓
Open Story
    ↓
Read Only View
```

Completed stories:

* cannot be continued
* cannot be forked
* cannot create alternate endings

They exist as classroom artifacts.

---

## Failure Handling (Q8)

If generation fails:

```text
Generation Error
```

The teacher sees:

```text
Something went wrong.

[ Try Again ]
```

Regenerate choices and custom choice remain **workspace controls during normal flow** (Q6/Q7). Offering them on the failure screen is a future enhancement, not V1.

**Product rule:** No single AI failure should end the classroom activity. The teacher must always be able to rescue the lesson.

---

## First-Time Teacher Guidance (Q10)

**V1:** No onboarding. The workflow should be self-explanatory.

**Future:** One-time tooltip for first-time teachers.
