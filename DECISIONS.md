# Decisions Made

*A record of product decisions: what was decided, why, what was rejected, and what new information would legitimately reopen each question. This log exists to make revisiting settled decisions costly — not impossible, but deliberate.*

---

## Product & Reviewer Model

### Two reviewer paths: direct reports and cross-functional partners
*Decided: April 2026*

ReportsTo surfaces reviews from two distinct relationship types, each routed to a different question set and displayed separately on the profile.

Direct reports see the full power-dynamic dimensions: protects the team, gives credit, grows and promotes people, follows through on 1:1 commitments. Cross-functional partners see the externally-visible dimensions: communicates decisions, consistent behavior under pressure, follows through on cross-team commitments.

**Why:** Asking a cross-functional partner to rate "protects the team" is asking them to speculate about a dynamic they didn't witness. That's noise, not signal. The two vantage points are complementary and non-substitutable — a manager can be an exceptional advocate downward while being adversarial to every team around them. That gap is real, common, and currently invisible on every existing platform.

**What was rejected:** A single question set for all reviewer types. Rejected because it either asks reviewers to speculate beyond their observational access, or forces the question set to the lowest common denominator and loses the power-dynamic dimensions most valuable to job seekers.

**Revisit if:** POC testers consistently struggle to self-identify their relationship type, or if the cross-functional path produces materially lower submission completion rates than the direct report path.

---

## Verification & Appeals

### Appeals surface is factual only — not score-based
*Decided: April 2026*

Managers can dispute a review only on factual grounds: employment dates do not overlap, therefore this person cannot have worked with me during the period claimed. Score, dimension ratings, and characterization of behavior are not subject to challenge.

**Why:** Allowing managers to dispute scores requires adjudicating subjective experience, which is both impossible to do fairly and creates a mechanism for powerful people to suppress legitimate reviews. Limiting disputes to verifiable facts keeps the appeals surface narrow, consistent, and defensible. The appeals process is essentially a second pass of the verification logic.

**What was rejected:** A tiered appeals system where managers with worse records face a higher bar to dispute. Conceptually sound, but legally complex and adds system state that creates liability.

**Revisit if:** Legal counsel flags the factual-only standard as insufficient protection against defamation exposure, or if a high-profile dispute reveals a gap the factual standard can't resolve.

---

### Re-attestation path for disputed reviews
*Decided: April 2026*

When a manager successfully disputes on factual grounds, the review is temporarily held — not removed. The reviewer is notified and given a chance to re-attest with higher-bar evidence. The review is not presumed invalid; the reviewer is not presumed dishonest. If re-attestation confirms the relationship, the review is reinstated.

**Why:** Removing a review automatically on manager complaint gives managers a low-cost suppression tool. Re-attestation keeps the burden of proof on the factual question.

**Revisit if:** Legal counsel advises that holding a disputed review during re-attestation creates liability, or if re-attestation completion rates are so low that the mechanic effectively becomes auto-removal in practice.

---

## Scoring & Abuse Prevention

### Rate limiting and anomaly flagging over score-gating
*Decided: April 2026*

Abuse prevention uses rate limiting (one review per manager per rolling 90 days; volume caps on new submissions per week) and anomaly flagging (volume spikes trigger quarantine and a cooling-off period with re-confirmation ask).

**Why the score-gate was rejected:** Requiring a reviewer to submit a positive review before submitting a negative one creates an incentive to file a dishonest positive review to unlock the negative one. That's manufactured signal — worse than no signal, because you've traded one integrity problem for another.

**Why the quarantine mechanic:** A volume spike — regardless of score direction — is the signal worth acting on. The holding period filters rage-submitters, gives time for coordinated campaign patterns to reveal themselves, and creates a natural buffer between triggering events (layoffs, public blowups) and data going live. The 30-day re-confirmation ask also functions as a quality filter.

**Note:** Anomaly detection is score-agnostic. Coordinated positive review bombs are equally corrosive to signal quality.

**Revisit if:** Quarantine rates are materially suppressing legitimate review volume (threshold too sensitive), or a coordinated campaign successfully evades the mechanic (trigger logic needs tightening). Confirmation window length (currently 30 days) should be revisited once there is data on where in the job search cycle most reviewers are submitting.

---

*Last updated: May 2026*
