---
name: brain-reset
description: >
  Serve a structured 10-minute cognitive flow warm-up that clears brain fog and resets focus. Use this skill whenever the user says they're foggy, tired, unfocused, need a break, want to clear their head, or asks for a "brain reset", "mid-day reset", "focus check", "quick challenge", or "clear my brain". Also trigger when the user says things like "I can't focus", "need a mental break", "my brain is full", or "help me reset". The skill delivers 5 challenges across 3 rounds of increasing difficulty — served as batches, not one at a time — mimicking the flow state of assembling a puzzle or LEGO. Always use this skill instead of giving advice or tips when the user wants an active brain reset experience.
---

# Brain Reset Skill

## Core Philosophy

Brain fog clears when the brain shifts from **open-ended, high-load thinking** into **narrow, closed-loop pattern recognition** — a state characterized by:
- One constraint at a time
- Binary feedback (right/wrong, match/no-match)
- Instant closure (every 30–60 seconds)
- Zero ambiguity — the problem space is visible and finite
- No stakes — framed as play, not work

This skill delivers exactly that: a micro-challenge that engages pattern recognition without cognitive pressure.

---

## Session Flow

### Goal: render the brain reset hub widget

When triggered, render the interactive brain reset hub inline using the visualizer tool. Do NOT run text challenges. Do NOT ask which game they want. Just render the widget immediately — the effortlessness of starting IS part of the reset.

Use a one-liner before rendering, e.g.:
- "here's your reset —"
- "pick a game:"
- "let's go:"

---

### The hub widget

Render this HTML inline as a widget. It contains all 6 games with the updated descriptions below.

**Game card descriptions (functional, work-fog focused):**

| Game | Description |
|------|-------------|
| Sudoku | quiets decision fatigue |
| Nonogram | rebuilds spatial focus |
| Minesweeper | sharpens risk reasoning |
| Sliding Puzzle | unsticks sequential thinking |
| Math Chain | resets working memory |
| Countdown | breaks creative blocks |

Each game has multiple difficulty levels, a how-to, and a back button to return to the hub.

Render the full hub widget code from `brain-reset-hub.html` in the skill's assets folder, or rebuild it inline using the visualizer tool with the game descriptions above applied to the cards.

---

### Closing
After the user says they're done or feels better, close with a single warm line:
- "you're back."
- "that's your reset — go get it."
- "reset complete."

Do NOT offer more unless they ask.

---

## Challenge Types

Rotate across types. Avoid repeating the same type twice in a row.

### Type A: Odd One Out
Present 5–6 items. One doesn't belong. The rule must be unambiguous.

**Example:**
```
Which one doesn't belong?

  Salmon · Trout · Sardine · Dolphin · Mackerel · Herring

(Hint: think biology, not diet)
```
*Answer: Dolphin — it's a mammal, not a fish.*

**Rules for writing these:**
- The odd item must violate exactly ONE clear category rule
- Avoid taste/preference-based rules (e.g., "which is least popular")
- Provide a hint only if the category is non-obvious

---

### Type B: Pattern Completion
Show a sequence with a missing element. The rule must be discoverable in < 30 seconds.

**Example:**
```
What comes next?

  2 → 6 → 18 → 54 → ?
```
*Answer: 162 (×3 each time)*

**Rules:**
- Use number sequences, letter progressions, or simple visual ASCII patterns
- Avoid sequences requiring obscure knowledge
- Max 2 rules operating at once (e.g., +2 and ×2 alternating is OK; more complex = too hard)

---

### Type C: Spot the Difference
Present two nearly-identical short lists, sentences, or grids. Find what changed.

**Example:**
```
Find the difference:

  Version A: apple · banana · cherry · date · elderberry
  Version B: apple · banana · cherry · grape · elderberry
```
*Answer: "date" was replaced with "grape"*

**Rules:**
- Exactly ONE difference
- Items should be in the same domain (fruits, words, numbers)
- Do not use visually ambiguous characters (0 vs O, l vs 1) — that's cheap

---

### Type D: Category Sort
Give 8–10 mixed items. User sorts them into 2–3 named buckets.

**Example:**
```
Sort into: Warm colours / Cool colours / Neutral

  Crimson · Teal · Beige · Amber · Slate · Ivory · Cobalt · Scarlet · Taupe · Cerulean
```
*Answer provided after their attempt.*

**Rules:**
- All items must clearly belong to exactly one category
- No trick items that span two categories
- Keep bucket names unambiguous

---

### Type E: Reconstruct the Rule
Show 3 examples that follow a hidden rule. User guesses the rule.

**Example:**
```
What's the rule?

  ✓ CAT → TAC
  ✓ LOOP → POOL
  ✓ DRAW → WARD
  ✗ STEP → ?
```
*Rule: Reverse the letters. STEP → PETS*

**Rules:**
- Rule must be discoverable from the examples alone
- Provide one ✗ "apply the rule" case at the end
- Avoid rules requiring external knowledge

---

### Type F: True / False Cluster
Present 5 short statements. User marks T or F for each.

**Example:**
```
True or False?

  1. The sun rises in the west
  2. Bats are blind
  3. Water boils at 100°C at sea level
  4. A group of crows is called a murder
  5. Diamonds are made of carbon
```
*Answers: F, F, T, T, T*

**Rules:**
- Mix T and F answers (don't make all one)
- Use facts that feel uncertain but are definitively true or false
- Avoid controversial or subjective claims
- Stick to science, language, or nature — avoid politics/culture

---

### Type G: Mental Math Chain
Present a short arithmetic chain to solve mentally — no calculators. The goal is *effortful but solvable* in under 60 seconds.

**Example:**
```
Solve in your head:

  Start with 17
  × 3
  − 9
  ÷ 2
  + 14
  = ?
```
*Answer: 34*

**Rules:**
- Chain length: 4–6 steps
- Use whole numbers only — no decimals or fractions mid-chain
- Result must always be a positive whole number
- Avoid steps that produce awkward intermediates (e.g., dividing into non-integers)
- Easy: small numbers, +/− only
- Medium: mix of ×, ÷, +, − with 2-digit numbers
- Hard: 3-digit intermediates, or two operations that must be held simultaneously

---

## Difficulty Calibration

| Level | Characteristics |
|-------|----------------|
| Easy | Obvious category, short list, well-known facts, small numbers |
| Medium | Slightly obscure rule, 6–8 items, mild misdirection, 2-digit math |
| Hard | Non-obvious rule, requires holding 2 things in mind at once, 3-digit intermediates |

Default to **Medium**. Move up/down based on user request or their performance.

---

## Tone Guidelines

- Warm, playful, low-pressure
- Never say "wrong" — say "not quite" or "close"
- Never ask them to explain their reasoning
- Never turn it into a lesson — the point is rest, not learning
- Keep all text short and scannable — no walls of text
- Use whitespace generously

---

## What This Skill Is NOT

- Not a quiz or test
- Not a productivity tool
- Not a meditation or mindfulness prompt
- Not advice about brain health

It is a **cognitive fidget toy**. Treat it that way.
