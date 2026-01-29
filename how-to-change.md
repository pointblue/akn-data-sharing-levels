# Policy for Updating the AKN Sharing Level Definitions

## Purpose and Scope
This policy establishes the formal procedure for modifying the canonical definition of the Avian Knowledge Network (AKN) data sharing levels, which currently resides in `main.md`. It applies to all collaborators, committees, and partner teams who author, review, or implement changes that affect the published definition or its downstream consumers.

## Governance Authority
The AKN Steering Committee (the Committee) is the sole body authorized to approve changes to the definition. The Committee chair is responsible for convening meetings, verifying quorum (minimum two-thirds of voting members), and certifying the outcome of each vote. The Repository Maintainer ensures that approved changes are recorded in `main.md` and related artifacts.

## Change Management Procedure
1. **Submission of Change Request**
   - Any member may submit a written change request that includes: background, rationale, specific edits to `main.md`, anticipated effective date, and impact assessment for data providers and consumers.
   - Requests must be circulated to the Committee at least five business days before the next scheduled meeting, ensuring adequate review time.

2. **Presentation and Clarification**
   - The proposer (or their delegate) presents the request during the meeting, highlighting objectives, dependencies, and implementation implications.
   - Committee members may request clarifications or require supporting documentation (e.g., field testing, partner endorsements) before moving forward.

3. **Deliberation and Vote**
   - After discussion, the chair calls for a vote. A simple majority of the full Committee and a standing quorum are required for approval.
   - Approved motions must specify the exact text to be incorporated into `main.md`, the target release window, and any conditional requirements.

4. **Documentation of Approved Changes**
   - The Repository Maintainer drafts the approved edits in `main.md`, referencing the meeting date and motion ID in the pull request or commit description.
   - The Committee reviews the draft for fidelity to the approved motion before granting final editorial sign-off.

5. **Engineering Handoff**
   - Following sign-off, the maintainer provides the engineering team with the merged specification, desired release date, and any migration notes.
   - The engineering team confirms feasibility, proposes alternative timelines if necessary, and acknowledges receipt in writing.

6. **Release Coordination and Publication**
   - Approved changes are merged into the `main` branch once engineering confirms release readiness. The repository tag and release notes must reference the effective date.
   - Publication to avianknowledge.net occurs in lockstep with the engineering release. Any discrepancy between the live site and `main.md` must be resolved within one business day.

## Record Keeping and Transparency
A permanent record of meeting minutes, motions, votes, and effective dates must be stored alongside the repository (e.g., in `historic/`). The Committee chair ensures that stakeholders are notified of upcoming votes, outcomes, and release plans within two business days of each decision.

## Policy Maintenance
This policy is reviewed annually by the Committee. Amendments to the policy itself follow the same process and require explicit notation in the repository history indicating the effective date of the governance change.
