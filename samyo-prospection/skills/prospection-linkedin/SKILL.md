---
name: prospection-linkedin
description: Prospect on LinkedIn with Samyo. Use when the user wants to find clients, learners or companies on LinkedIn, prepare a LinkedIn prospecting strategy from their website, or run, adjust, pause or review their Samyo prospecting campaign (prospects, messages to approve, target, tone, pace).
---

# LinkedIn prospecting with Samyo

Samyo Prospection is an AI agent that prospects on LinkedIn: it reads the user's website, works out who to contact and what to say, invites and follows up within safe limits, and hands over when a prospect is interested.

## The user has no Samyo account yet

1. Ask for their website if you do not have it.
2. Call `preparer_strategie_prospection` (server `samyo-decouverte`) with `site`, and `formation: true` if they are a training provider. It takes 30 to 90 seconds; nothing is sent on LinkedIn.
3. Show the strategy briefly: target job titles, offer, goal of the messages, first message angle.
4. Give them the link from the answer: they review the strategy, create their access and launch with the free credits.

`decouvrir_samyo_prospection` answers questions about what Samyo does, its safeguards and its price.

## The user has a Samyo account

Use the `samyo` server (they authenticate once with `/mcp`).

- Start with `resume_organisme`: campaign status, target, sequence, credits, today's numbers.
- `lire` with `collection: "linkedin"` lists prospects, messages waiting for approval and recent events.
- Every action tool (strategy, pace, pause, launch, approve a message, do-not-contact list…) only returns a preview and a proposal id. Show the preview in plain words and ask. Call `valider_proposition` only after an explicit yes in the conversation; otherwise `refuser_proposition`.
- Change one strategy field at a time with `linkedin__modifierStrategie`; the angles of the messages are `sequence.premierMessage` and `sequence.relance1…4`, separate from the goal.
- Never invent a figure, link or promise for a message: ask the user.
- To subscribe to the Agent plan, `lien_offre_agent` (administrator only) returns a Stripe page the user opens and pays themselves. Never pay or enter payment details.
