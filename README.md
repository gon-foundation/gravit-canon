# Gravit Canon: GEVP + VEDS

> **Status on 27 November 2026.** The current revision of the mechanism is
> **[draft-gravit-gevp-12](https://datatracker.ietf.org/doc/draft-gravit-gevp/12/)** (2 Nov 2026), not -07.
> The policy is still [draft-gravit-verifiable-epistemic-decision-00](https://datatracker.ietf.org/doc/draft-gravit-verifiable-epistemic-decision/00/).
> Both are individual Internet-Drafts, not IETF standards.
>
> **Correction.** The text below (Canon v1.1, 12 Aug 2026) recommends theta 0.73 with "TPR 93.4 %, FPR 0.4 %".
> Those calibration figures could not be reproduced. GEVP-08 (12 Oct 2026) replaced them with reproducible results,
> and the threshold 0.73 is **no longer recommended**. The figures stay below only as a record of what was published.
> "Architecture is STABLE" was the view of August 2026; revisions 08 to 12 changed the specification substantially.

## Revisions of GEVP since this Canon

| Revision | Date | What changed |
|---|---|---|
| [-07](https://datatracker.ietf.org/doc/draft-gravit-gevp/07/) | 2026-08-12 | VEDS conformance mapping (Section 10); the revision this Canon describes |
| [-08](https://datatracker.ietf.org/doc/draft-gravit-gevp/08/) | 2026-10-12 | **Correction:** non-reproducible calibration figures of -00 to -07 replaced by reproducible results; theta 0.73 no longer recommended |
| [-09](https://datatracker.ietf.org/doc/draft-gravit-gevp/09/) | 2026-10-13 | Complete specification, matching reference verifier v0.6.0: record format and signature, signed result (true, false, no verdict), registry under a threshold of root keys, reproducible decision record, signed receipts |
| [-10](https://datatracker.ietf.org/doc/draft-gravit-gevp/10/) | 2026-10-22 | Safety properties (fault parameter t, forgery bound, contradiction veto), relation to RATS, time bounds from independent time-stamp authorities, CDDL data model |
| [-11](https://datatracker.ietf.org/doc/draft-gravit-gevp/11/) | 2026-10-23 | Built on SCITT (RFC 9943) and COSE Receipts (RFC 9942): each verifier an Issuer, each record a Signed Statement; encoding described, not yet implemented |
| [-12](https://datatracker.ietf.org/doc/draft-gravit-gevp/12/) | 2026-11-02 | Known limit stated: provenance is self-reported, so a relayed source can look like a second independent one; operators declare upstream sources; implementation status v0.7.0 |

Diff of any two revisions: `https://author-tools.ietf.org/iddiff?url1=draft-gravit-gevp-07&url2=draft-gravit-gevp-12`

## Where things are now

- Reference implementation: [gon-foundation/verifier](https://github.com/gon-foundation/verifier) (Python and Rust, v0.7.0)
- Reproduce every published result: [gon-foundation/gravit-eval-pack](https://github.com/gon-foundation/gravit-eval-pack)
- Network site, docs and SDKs: [gravitopennetwork.org](https://gravitopennetwork.org/) · Foundation: [gon.foundation](https://gon.foundation/)
- Repositories moved from `GravitOpenNetwork` and `gravit-open-network-foundation` to the organisation `gon-foundation`; old links redirect.

---

## Canon v1.1 (12 August 2026), kept unchanged

Gravit Canon — Final v1.1 / GEVP + VEDS
<img width="1920" height="1280" alt="grafik" src="https://github.com/user-attachments/assets/b2da6ae8-488c-4778-8922-8b959c524c3a" />

    Architecture is STABLE. Two-track IETF architecture POSTED. Future work is implementations, interoperability, and operational experience.

Gravit is an open network for verifiable knowledge transformations — from checkbox transparency to auditable trust.
IETF — Two-Track POSTED ✅

Latest — Two-Track:
Track	Document	Revision	Date	Status
Mechanism (HOW)	draft-gravit-gevp	07	2026-08-12	POSTED
Policy (WHAT)	draft-gravit-verifiable-epistemic-decision	00	2026-08-09	POSTED
GEVP-07 — Mechanism | HOW to verify

    TXT: https://www.ietf.org/archive/id/draft-gravit-gevp-07.txt
    HTML: https://www.ietf.org/archive/id/draft-gravit-gevp-07.html
    Datatracker: https://datatracker.ietf.org/doc/draft-gravit-gevp/
    Diff 06→07: https://author-tools.ietf.org/iddiff?url2=draft-gravit-gevp-07

What changed from 06:

    Section 10 VEDS Conformance Mapping — normative mapping between GEVP ESM and VEDS taxonomy
    RAW → not admissible, VALIDATED → ≤ Speculative Claim, VERIFIED → Probabilistic Assessment, COMMITTED (h>0.7/f<0.3) → Verified Fact
    Aggregation Restriction = No Aggregation Laundering (VEDS 4.1.2)

Stable since 05:

    ESM: RAW -> VALIDATED -> VERIFIED -> COMMITTED
    Persistence MAY (Ledger, IPFS, GSS, DB, Archive) — not MUST
    Signatures OPTIONAL, Transport Bindings separate

VEDS-00 — Policy | WHAT to enforce

    TXT: https://www.ietf.org/archive/id/draft-gravit-verifiable-epistemic-decision-00.txt
    HTML: https://www.ietf.org/archive/id/draft-gravit-verifiable-epistemic-decision-00.html
    Datatracker: https://datatracker.ietf.org/doc/draft-gravit-verifiable-epistemic-decision/

Defines:

    Taxonomy: Verified Fact / Probabilistic Assessment / Speculative Claim
    Failure States: REJECTED / DEGRADED / PENDING
    Decision Record format, traceability, auditability, Conformance Statement
    Threat model 4.6.1 → Security 6 + Residual Risks
    Mechanism-agnostic by design (Variant A): GEVP is Informative example only [GEVP] — no downref per RFC 3967/4897
    Verified idnits: Checking references for intended status: Proposed Standard — No issues found here — 0/0/2/0

Two-Track Architecture

EU AI Act Art.50
IETF TWO-TRACK

GEVP-07 — Mechanism | HOW to verify          VEDS-00 — Policy | WHAT to enforce
ESM: RAW → VALIDATED → VERIFIED → COMMITTED  Taxonomy: Verified Fact / Probabilistic / Speculative
θ = 0.73, h>0.7 • f<0.3                      Failure: REJECTED / DEGRADED / PENDING
         <--- Conformance Mapping Section 10 --->

    GEVP = HOW: verifiable provenance (who created, what verified, when, theta-score)
    VEDS = WHAT: reproducible, auditable, fail-closed behavioral guarantees

For EU AI Act Art.50 (mandatory disclosure from Aug 2026): together = auditable trust.
Core Invariants

    Engineering heuristic, NOT theorem: C(manipulation) > C(validation) * 2.0
    Theta: 0.73 RECOMMENDED (pinned 7755f53: 1401/1500, TPR 93.4%, FPR 0.4%), range 0.70-0.80
    Convergence: h > 0.7 honest, f < 0.3 faulty — no 67% Byzantine claim
    GEVP renamed from VCP to avoid collision with VeritasChain VCP (draft-kamimura-scitt-vcp)

Implementation Status

    MVR 0.1.0-mvr: https://github.com/GravitOpenNetwork/gravit-canon/tree/main/mvr
    Calibration SHA: 7755f53, TPR 93.4%, FPR 0.4%, theta 0.73 RECOMMENDED
    Next: interop tests against both specs

Links

    Org: https://github.com/GravitOpenNetwork
    Website: https://gravit.space
    IETF folder: https://github.com/GravitOpenNetwork/gravit-canon/tree/main/ietf
    Issues: https://github.com/GravitOpenNetwork/gravit-canon/issues

Citation

draft-gravit-gevp-07, Alex Konviser, IETF Individual Submission, 2026-08-12
draft-gravit-verifiable-epistemic-decision-00, Alex Konviser, IETF Individual Submission, 2026-08-09

Validation:

    GEVP-07: author-tools.ietf.org — well-formed, 0 dup, 0 missing xrefs, 0 non-ASCII
    VEDS-00: idnits 2.17.1 — 0 errors, 0 flaws, 2 warnings (known -00 boilerplate), 0 comments — "No issues found here" for Proposed Standard

