# Verification Architecture

The value of ReportsTo depends entirely on one thing: every review was written by someone who actually worked with the person being reviewed. If that breaks, the product is Yelp for managers — noise with a credibility veneer.

This document describes how verification works, why we made the choices we did, and how we thought about the tradeoffs.

---

## The core problem

Anonymous review platforms face a fundamental tension: the more friction you add to verification, the fewer reviews you get. The less friction you require, the less trustworthy the data is.

Most platforms resolve this tension by choosing low friction and calling it "community trust." Glassdoor accepts self-reported employment. Blind verifies work email — once, at account creation — and then trusts that account indefinitely. Rate My Manager has no verification at all.

The result is that all of them are gameable. ReportsTo's answer is that verification must be structural — not a policy promise, but a system property.

---

## Two reviewer populations, two verification paths

Current employees and former employees have different verification needs and different levels of friction tolerance. We solve for them differently.

---

## Current employees: work email domain confirmation

A current employee verifies by confirming a link sent to their `@company.com` email address. This proves active access to a company email account at the time of submission and that the company domain matches the manager's employer.

**Domain maintenance:** Company email domains change — acquisitions, rebrands, spinoffs. We maintain a mapping of known company domains and aliases. Reviewers who flag a domain mismatch can submit an alternative domain for review.

**Limitation:** Work email verification proves company membership, not reporting relationship or tenure overlap. This is acceptable because the question set is relationship-specific — ratings that don't cohere with the manager's profile over time are self-correcting signal.

---

## Former employees: Truework/Argyle or paystub upload

Former employees have two verification paths. The reviewer chooses based on what they have available.

### Path 1: Truework or Argyle (preferred)

Truework and Argyle are employment verification services that connect directly to payroll systems (ADP, Gusto, Rippling, Paychex, and others) and to The Work Number (Equifax's employment database, used by lenders and background check companies). The reviewer authorizes a query for their specific employer. The verification service confirms employment and tenure dates. ReportsTo receives a structured confirmation — employer name, dates — and never sees underlying documents or holds PII.

**Reviewer experience:** "Authorize this verification" — an OAuth-style consent flow, not a document upload.

**Coverage gap:** Smaller employers, nonprofits, and companies running proprietary payroll systems may not be in these databases. When automated verification returns no record, the reviewer falls through to Path 2.

### Path 2: Paystub upload (fallback)

The reviewer uploads two documents: their first paycheck and their most recent paycheck from that employer. This proves employment at the company and establishes a tenure window.

**Why two paystubs:** One proves employment at a point in time. Two prove a tenure window — what we need to validate whether the reviewer's employment overlapped with the manager's tenure.

**Why not offer letters:** Prove a start date, not an end date. Easily fabricated.

**PII handling:** Paystub uploads are processed for verification and then deleted. We do not retain payroll documents.

---

## Reviewer-built career timeline

The reviewer is responsible for building the career timeline of the person they are reviewing — not ReportsTo. When a reviewer submits a review, they attest to the manager's role and approximate tenure at the company in question. This fills in gaps that our verification data may not cover, and creates a crowd-sourced record of the manager's career history that improves with each reviewer.

This means the manager's profile on ReportsTo may be more complete than their own LinkedIn — built from the verified recollections of everyone who worked with them, not from what they chose to disclose.

---

## Anonymity architecture

Verification and review content are separated at the data layer — not by policy, but by system design.

The flow:
1. Reviewer submits verification (email confirmation, Truework/Argyle authorization, or paystub)
2. Verification system confirms employment and issues a one-time token
3. Token is presented at review submission — the only link between identity and review
4. Review is stored with no identity reference — only relationship type, tenure window, and submission timestamp
5. Token is invalidated after use

After step 5, there is no path from the review back to the reviewer. The bridge burns.

This is meaningfully different from "we promise not to reveal your identity." Promises can be broken under legal pressure or by data breach. Architectural separation means there is nothing to reveal.

---

## Abuse prevention

**Rate limiting:** One review per reviewer per manager per rolling 90 days. Volume caps on new submissions per week.

**Anomaly flagging and quarantine:** Volume spikes trigger automatic quarantine. Reviews are held, not published. Reviewers re-confirm after a 30-day cooling-off period. Anomaly detection is score-agnostic — coordinated positive review bombs are equally corrosive to signal quality.

**Appeals:** Managers can dispute on one ground only — employment dates do not overlap, therefore this person cannot have worked with me. Score and characterization are not disputable. Disputed reviews are held pending reviewer re-attestation, not removed.

---

## What we decided not to do

**LinkedIn OAuth or screenshot-based verification.** LinkedIn data is self-reported and editable. Screenshots are trivially forgeable. Neither provides structural verification. LinkedIn API dependency also creates platform risk — LinkedIn can revoke access the moment ReportsTo becomes interesting to them.

**Score-gating.** Requiring a positive review before submitting a negative one creates an incentive to file a dishonest positive review. Manufactured signal is worse than no signal.

**Indefinite account verification.** Verifying once at account creation and trusting that account forever (the Blind model). Doesn't prove the reviewer worked with a specific manager.

---

*Last updated: May 2026*
