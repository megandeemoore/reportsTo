# Founding Principles

These are the constraints that don't move. Not aspirational values — constraints. Every product decision that conflicts with these requires either a principled exception or a revision to the decision, not a revision to the principle.

---

## The data is the product

ReportsTo has value only if the reviews on it are trustworthy. A platform with 10,000 verified, reliable reviews is more valuable than one with 10 million unverified ones. When we face tradeoffs between volume and integrity, we choose integrity.

This means we will accept lower review counts as the price of verification friction. It means we will hold reviews during anomaly quarantine even when it delays publication. It means we will not create features that make reviews easier to game, regardless of the growth argument for them.

---

## Anonymity is architectural, not a promise

We do not say "we promise to protect your identity." We build systems where identity and review content are separated at the data layer and the bridge between them is destroyed after use.

Promises can be broken under legal pressure, by insider access, or by a data breach. Architecture cannot be broken in the same ways. When we make anonymity a system property rather than a policy commitment, we are making a real guarantee rather than a performative one.

Any future product decision that would require re-linking reviewer identity to review content requires revisiting this principle, not working around it.

---

## Leaders cannot manage their own record

Managers and executives cannot pay to suppress, promote, or respond to reviews. They cannot flag reviews for removal on the grounds that they disagree with them. They cannot purchase premium profiles, dispute resolutions, or algorithmic favorability.

This is not a policy we apply when convenient. It is a constraint that applies before product planning begins.

The moment leaders can influence their own record through money or institutional pressure, the product becomes a reputation management tool for the powerful — the opposite of what it exists to do.

---

## The product serves the reviewer and the job seeker, in that order

The reviewer takes a risk by submitting. The job seeker benefits from the data. These are the two constituencies whose interests the product is built to serve.

Managers are not a constituency whose interests we optimize for. They are subjects of the review, not users of the product.

This ordering matters when interests conflict. When a feature would benefit managers at the expense of reviewer safety or data integrity, it doesn't get built. When a feature would benefit job seekers at the expense of the reviewer experience (more friction, more exposure risk), we look for a path that doesn't require that tradeoff — and if we can't find one, we side with the reviewer.

---

## Structure is the moderation

The review format — six specific, observable behavioral dimensions — is the primary abuse prevention mechanism. It is very hard to defame someone on "follows through on commitments" without the review revealing more about the reviewer than the person being rated.

Free-text review fields invite abuse and require active moderation. Structured dimensions make abuse difficult by design. When we are tempted to add free-text fields for richness, we weigh that against the moderation burden and the defamation surface it creates.

This is not an argument against ever adding free-text. It is an argument for defaulting to structure and treating free-text as a feature with a cost.

---

## Decisions get made and stay made

ReportsTo will face pressure to revisit settled questions — from investors who want growth hacks, from managers who want appeals rights, from users who want more features. The decisions log exists to make revisiting costly: every settled question has a record of what was decided, why, what was rejected, and what new information would legitimately reopen it.

Reopening a settled question without that new information is not iteration. It is drift. Drift kills product integrity faster than bad decisions do, because drift is invisible until it isn't.

---

*Founding Principles — ReportsTo — April 2026*
