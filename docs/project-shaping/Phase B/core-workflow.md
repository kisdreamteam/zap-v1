# Phase B — Core Workflow

> Phase B draft (in progress).
>
> Related: [Phase A/problem-definition.md](Phase%20A/problem-definition.md) · [Phase A/product-boundaries.md](Phase%20A/product-boundaries.md) · [v1-scope.md](../v1-scope.md)

---

## Overview

Zap! is a teacher-controlled, AI-assisted classroom storytelling activity designed for projected classroom use with ESL/EFL students ages 6–8.

The workflow prioritizes:

* classroom discussion
* low preparation
* minimal cognitive load
* rapid classroom pacing
* resilience when AI fails

The story is not the goal.

The story is the vehicle used to create participation, discussion, creativity, collaboration, and shared ownership.

---

## Principles

1. Teacher authority is always preserved.
2. AI acts as a creative guide, not the decision maker.
3. Classroom momentum is prioritized over perfection.
4. Stories emerge through interaction.
5. Students influence the story through discussion.
6. Drafts are recoverable.
7. Completed stories become classroom artifacts.
8. Every major action should be understandable by a first-time teacher.
9. No single error should permanently interrupt a classroom session.
10. Simplicity is preferred over flexibility whenever possible.

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
* future integration with external systems may occur

### Dashboard

After login, teachers arrive at the Dashboard.

```text
Dashboard

+ New Story
+ Saved Stories
```

The dashboard intentionally remains minimal. It is not a management portal or an analytics dashboard. It exists only to direct teachers into the two primary workflows.

---

## Workflow 1 — Create New Story

### Template Selection

```text
Dashboard
    ↓
New Story
    ↓
Template Selection
```

The teacher chooses a template or a blank story. This provides a fast starting point while preserving flexibility.

### Setup Wizard

```text
Template Selection
    ↓
Setup Wizard
```

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

### Discussion Prompts

Discussion prompts are always visible. They should remain concise and easy to read.

Purpose:

* help inexperienced teachers
* encourage discussion
* reduce classroom silence
* support participation

### Choices

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

### Custom Choice

Teachers may override AI suggestions. Selecting **Custom Choice** opens:

```text
Custom Direction

[ Large Text Area ]

[ Submit ]
[ Cancel ]
```

The teacher may enter any story direction. Example:

```text
The dragon becomes friendly and offers to help.
```

The AI then continues the story from that direction.

### Regenerate Choices

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
History is immutable.
Future options are flexible.
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

Drafts are recoverable.

### Story Length

The teacher may end a story at any time. There is no minimum length and no maximum length.

The system may recommend approximately 3–5 rounds, but does not enforce it. Teacher authority always wins.

### Ending and Completion

```text
Teacher Clicks End Story
        ↓
AI Generates Conclusion
        ↓
Review Screen
        ↓
Teacher Clicks Complete
        ↓
Story Marked Complete
```

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

### Draft Stories

Draft stories may be resumed.

```text
Draft Stories
    ↓
Open Draft
```

The teacher sees:

```text
Resume Story

[ Continue ]
[ Regenerate Choices ]
```

The story state is preserved. The teacher decides whether to keep or refresh the available choices.

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

## Failure Handling

If generation fails:

```text
Generation Error
```

The teacher sees:

```text
Something went wrong.

[ Try Again ]

[ Regenerate Choices ]

[ Enter Custom Choice ]
```

**Product rule:** No single AI failure should end the classroom activity. The teacher must always be able to rescue the lesson.
