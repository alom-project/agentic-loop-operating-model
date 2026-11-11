# ALOM Profile Scope & Operating Domain Contract

**Document ID:** ALOM-PROF-SCOPE-SPEC-001
**Version:** v0.4-review.20261108
**Date:** 2026-10-30
**Owner:** Enterprise Architecture / AI Platform
**Applies to:** L1 Profile Engineering & Generation and L1-L7 scope consumers

> **Core rule**: ALOM Managed Work is anchored to a permanent `OperatingDomainProfile`. `ProjectProfile`, `CustomerProfile`, and `OrganizationProfile` are independent context overlays and MUST NOT be modeled as a mandatory parent-child chain. `project_id` is optional. Runtime isolation MUST use an explicit `isolation_scope_ref` rather than treating `project_id` as the universal isolation key.

> **Terminology:** An applying organization is the entity or unit applying ALOM; examples include businesses, public bodies, educational or research institutions, and nonprofits. The existing Enterprise scope (rank 10) is the baseline of the applying organization as a whole. It is distinct from the optional rank-30 OrganizationProfile responsibility and authority overlay. Existing identifiers and scope kinds retain their names; sample values such as `company` are illustrative and do not restrict the type of organization.

## 1. Purpose

This specification removes the project-centric assumption that entered the first ALOM Profile model through an illustrative delivery case. It defines one common scope contract that can represent both:

- permanent organizational functions such as Finance, HR, Legal, General Affairs, organizational IT, recurring operations, and maintenance; and
- temporary execution contexts such as customer projects, migration projects, PoCs, and internal initiatives.

This specification does **not** add an eighth ALOM layer. Profile Engineering & Generation remains an L1 Operating Model & Governance implementation subsystem.

## 2. Authority of the common scope contract

This companion specification defines the common-scope fields and resolution rules for L1–L7 consumers. For the fields defined here, consumers SHALL use this contract; conflicting legacy project-centric wording is a compatibility constraint, not the active common contract.

## 3. Fixed definitions

| Term | Definition | MUST NOT be treated as |
|---|---|---|
| OperatingDomainProfile | Permanent capability/function/service boundary in which Managed Work exists. Examples: System Integration, Finance, HR, organizational IT. | Project, organization chart node, customer |
| OrganizationProfile | Responsibility, authority, role, assignment, segregation-of-duties, and ownership overlay. Its lifecycle is independent from a project. | Child of ProjectProfile |
| CustomerProfile | Customer-specific contract, NDA, security, data handling, quality, or relationship constraints. Optional. | Mandatory hierarchy node |
| ProjectProfile | Temporary objective, contract/delivery context, deadline, risk, governance, and project-specific constraints. Optional. | Parent of organization/work model |
| CommonScopeContract | L1-L7 common scope identity used to select Profiles, authorize access, correlate Trace, and bind runtime execution. | A single linear inheritance chain |
| isolation_scope_ref | Explicit security/NDA/tenant isolation boundary reference. | Alias for project_id |
| ScopeOverlay | Approved or draft delta selected by scope predicates and merged by field-level semantics. | Last-write-wins patch |
| EffectiveProfile | Human-approved, fully resolved immutable operating contract for a target scope/work. | Draft Profile, runtime mutable state |

`OperatingDomainProfile` corresponds to the Profile Type named `BusinessProfile` in other controlled documents (for example the Profile Contract, Profile Reference Architecture, and L1). That type name is retained in those documents; there, `BusinessProfile` denotes the OperatingDomainProfile defined here. No rename is made in this version.

## 4. Profile model

### 4.1 Permanent operating structure

The structural model is:

```text
Enterprise
  └─ OperatingDomainProfile
      ├─ LifecycleProfile
      ├─ ProcessProfile
      └─ ManagedWorkProfile
          ├─ ExecutionProfile
          ├─ GovernanceProfile
          ├─ ContextProfile
          └─ AssuranceProfile
```

`OperatingDomainProfile` is the permanent anchor. It may represent:

- `business_service`: a customer-facing or revenue-producing service/capability;
- `corporate_function`: a permanent organizational function such as Finance or HR;
- `shared_platform`: a permanent internal platform capability such as organizational IT or AI Platform; or
- another explicitly registered domain kind.

### 4.2 Independent context overlays

The resolver selects each applicable overlay independently against the permanent operating structure:

| Context overlay | Selection and purpose |
|---|---|
| OrganizationProfile | Optional responsibility and authority context. |
| CustomerProfile | Optional customer-specific constraints. |
| ProjectProfile | Optional temporary project context. |
| UseCase / Process / local overlay | Optional work-local specialization. |

There is no mandatory `OrganizationProfile -> ProjectProfile` or `ProjectProfile -> OrganizationProfile` relationship. Organization and Project are naturally many-to-many. Resolution produces a candidate; a Profile becomes Effective and may be used only after validation, the required Human approvals, release authorization, and Registry admission. Resolution alone does not grant Effective status.

### 4.3 Profile ownership

| Profile | Primary semantic ownership |
|---|---|
| OperatingDomainProfile | permanent purpose/capability boundary, lifecycle/process/work catalog |
| OrganizationProfile | responsibility, authority, assignment constraints, SoD |
| CustomerProfile | customer contract/NDA/customer security and quality constraints |
| ProjectProfile | temporary objective, delivery constraints, deadline, project risk/governance |
| ManagedWorkProfile | purpose, execution mode, owner reference, risk, evidence, runtime bindings |
| ExecutionProfile | ALE/L5/Harness/Runner/Tool/budget constraints |
| GovernanceProfile | policy, human control, approval, exception/remedy |
| ContextProfile | L6/L7 knowledge roots, authority, freshness, citation |
| AssuranceProfile | eval, verification, review, oracle, criteria, independence |

## 5. CommonScopeContract

### 5.1 Canonical fields

For a complete CommonScopeContract, the published v1 schema requires `phase`, `classification`, and `isolation_scope_ref` at both design-time and runtime. The runtime and security-sensitive design requirements below remain applicable. If the required values are not yet known, keep the input as an unresolved draft; do not invent values or treat it as a schema-valid complete contract.

| Field | Requirement | Meaning |
|---|---|---|
| `phase` | MUST in schema v1 | `design_time` or `runtime` |
| `scope_ref` | MUST | immutable/canonical reference for the resolved scope identity |
| `enterprise_id` | MUST | applying organization boundary |
| `domain_id` | MUST | permanent operating domain |
| `organization_id` | MAY | organization/responsibility context |
| `customer_id` | MAY | customer context |
| `project_id` | MAY | temporary project context |
| `usecase_id` | MAY | use-case-local context (rank 40) |
| `process_id` | MAY | process-local context (rank 40; independent of and parallel to `usecase_id`) |
| `work_id` | SHOULD for design-time, MUST for executable Managed Work | Managed Work identity |
| `tenant_id` | MAY | compatibility/multi-tenant routing metadata; not the sole isolation key |
| `classification` | MUST in schema v1 at both phases | information classification ceiling/label |
| `isolation_scope_ref` | MUST in schema v1 at both phases; required for runtime and security-sensitive design resolution | explicit isolation boundary |

The absence of `project_id` MUST NOT cause Profile compilation, resolution, L2 admission, L5 execution, L6 retrieval, L7 authority resolution, or Trace correlation to fail unless a selected rule explicitly requires a project for that particular Managed Work.

In this version each of `organization_id`, `customer_id`, `project_id`, `usecase_id`, and `process_id` is single-valued: an identifier or null, never a list. Work that spans departments is represented by splitting it into separate Managed Work items, one per department, each carrying its own `organization_id` / `process_id`, so that each department's rules apply. Multi-valued scope fields are out of scope for this version.

The L2 Control Plane standard and the runtime binding contracts derived from it spell the use-case identifier `use_case_id`. It denotes the same identifier as `usecase_id` in this contract; no rename is made in this version.

### 5.2 Example: permanent Finance work

This example is a runtime contract.

```yaml
kind: CommonScopeContract
schema_version: "1.0"
phase: runtime
scope_ref: scope://company/domain/finance/work/expense-approval
enterprise_id: company
domain_id: finance
organization_id: finance-department
customer_id: null
project_id: null
usecase_id: expense-processing
work_id: expense-approval
classification: confidential
isolation_scope_ref: scope://company/finance
```

### 5.3 Example: SI customer project work

This example is a runtime contract.

```yaml
kind: CommonScopeContract
schema_version: "1.0"
phase: runtime
scope_ref: scope://company/domain/system-integration/customer/customer-a/project/core-renewal/work/code-review
enterprise_id: company
domain_id: system-integration
organization_id: delivery-division
customer_id: customer-a
project_id: core-renewal
usecase_id: code-review
work_id: code-review
classification: confidential
isolation_scope_ref: scope://customer-a/core-renewal
```

Both examples use the same contract. Project is present only where it has business meaning.

## 6. Resolution model

### 6.1 Selection phases

The resolver SHALL apply the following phases:

1. Normalize and validate `CommonScopeContract`.
2. Resolve the applying-organization baseline (Enterprise scope).
3. Resolve the mandatory `OperatingDomainProfile`.
4. Select matching independent overlays: Organization, Customer, Project, and other approved context overlays.
5. Select UseCase/Process and Work-specific overlays.
6. Apply Rule Authority and Applicability decisions.
7. Merge each field group using its declared operator.
8. Verify no-relaxation invariants and detect semantic conflicts.
9. Resolve `isolation_scope_ref` and runtime authorization boundary.
10. Bind L1-L7 references, create the EffectiveProfile candidate, calculate canonical digest, validate, and require Human Approval before Effective release.

### 6.2 Specificity is not a parent tree

The baseline specificity classes are:

| Class | Rank | Note |
|---|---:|---|
| Applying organization (Enterprise) | 10 | baseline common to the applying organization |
| Operating Domain | 20 | permanent work capability |
| Organization / Customer / Project | 30 | parallel context overlays; no implicit order among them |
| UseCase / Process | 40 | local business/process specialization; `usecase_id` and `process_id` are independent kinds at the same rank with no implicit order between them |
| Work | 50 | final Managed Work specialization |

Organization, Customer, and Project all have the same structural rank; UseCase and Process likewise share rank 40. If two overlays at the same rank propose incompatible non-monotonic values, the resolver MUST NOT choose one by file order, timestamp, profile type, or last-write-wins. It SHALL either:

- apply a field operator whose semantics are monotonic and deterministic; or
- use an explicit approved Authority/precedence rule; or
- emit `CONFLICT` / `REVIEW_REQUIRED`.

### 6.3 Scope selector

A ScopeOverlay selector matches only the fields it explicitly declares. Example:

```yaml
selector:
  enterprise_id: company
  domain_id: finance
  organization_id: finance-department
  project_id: null
```

A `null` value means the overlay explicitly targets non-project work. An omitted selector field is not a wildcard privilege escalation; it means the field does not participate in selection.

## 7. Field-level merge and no-relaxation

The resolver MUST NOT implement generic last-write-wins.

| Field group | Operator | Rule |
|---|---|---|
| `required_gates`, `evidence`, `approvers` | `UNION` | lower/local overlay cannot remove mandatory items |
| `prohibits`, `deny_tools`, `deny_actions` | `UNION` | prohibitions accumulate unless an explicit valid ExceptionGrant applies |
| `allowed_tools`, `capabilities` | `INTERSECTION` | local overlay can only narrow allowed capability |
| `autonomy_ceiling` | `MOST_RESTRICTIVE` | A0 < A1 < A2 < A3 < A4 |
| `risk_class` | `MOST_SEVERE` | organization-defined severity order |
| `classification` | `MOST_RESTRICTIVE` | stricter classification wins |
| budgets/ceilings | `MIN_CEILING` | smaller permitted upper bound wins |
| `human_required` | `BOOLEAN_OR` | any mandatory human condition is preserved |
| owner/authority/approver/stop authority | `EXPLICIT_OR_CONFLICT` | differing candidates are not silently selected |
| `isolation_scope_ref` | `EXPLICIT_OR_CONFLICT` | security boundary cannot silently move |
| runtime binding refs | `NEAREST_COMPATIBLE` | replacement only when schema/capability/authority compatible |
| source/provenance refs | `UNION_DEDUP` | all selected/denied inputs remain traceable |

### 7.1 Mandatory invariants

- Human-required work MUST NOT become agentic through overlay specificity.
- Human-required work MUST NOT become deterministic-system through overlay specificity. `human_required=true` together with `execution_mode=deterministic-system` is ERROR / fail-closed.
- Execution Mode is exactly `human-only / interactive-agent / agentic / deterministic-system`. `hybrid` is not an Execution Mode. Work Type `deterministic`/`hybrid` remains orthogonal.
- Mandatory Quality/Assurance gates MUST NOT be removed.
- Authority conflicts MUST NOT be auto-resolved.
- Project-specific rules MUST NOT apply to non-project work merely because a project field is missing.
- Organization authority MUST remain valid independently of Project lifetime.
- Customer/Project NDA may tighten an isolation boundary but MUST NOT weaken a stricter domain/organization boundary.
- `project_id` MUST NOT be synthesized only to satisfy an implementation schema.

## 8. Isolation contract

### 8.1 Explicit boundary

All runtime consumers that require isolation SHALL use `isolation_scope_ref` as the canonical security partition reference.

Examples:

```yaml
# permanent corporate function
isolation_scope_ref: scope://company/hr

---
# customer/project NDA boundary
isolation_scope_ref: scope://customer-a/core-renewal
```

The value is an opaque approved scope reference. Consumers MUST NOT infer that every `scope://...` value is a project.

### 8.2 Required behavior

- `project_id` MAY contribute to isolation-scope resolution but MUST NOT be the only allowed isolation input.
- A project-less Finance/HR/Legal workload can have a stronger isolation boundary than a normal internal project.
- Queue namespace, state partition, worker pool, repository/workspace, credential, artifact, cache, Context retrieval, Trace, and L7 access policies SHALL derive from `isolation_scope_ref` plus authorization policy.
- If the isolation boundary cannot be resolved, runtime admission fails closed.

## 9. L1-L7 consumer contract

| Consumer | Required change from project-centric baseline |
|---|---|
| L1 Operating Model & Governance | ManagedWorkDefinition and Profile Resolution use `CommonScopeContract`; OperatingDomain is permanent; Project is optional overlay. |
| L2 Control Plane | TaskContract/TaskRun/RuntimeManifest carry `scope_ref`, `domain_id`, optional `project_id`, and mandatory runtime `isolation_scope_ref`. Queue/state partition MUST NOT require project. |
| L3 Graph Engineering | GraphRun inherits the Common Scope from L2; graph semantics do not introduce a project requirement. |
| L4 Agentic Loop | LoopRun inherits the Common Scope; convergence semantics are scope-neutral. |
| L5 Shared Execution Plane | ExecutionRequest carries Common Scope and `isolation_scope_ref`; sandbox/worker/tool/credential isolation uses the explicit boundary, not mandatory project. |
| L6 Context & Knowledge | ContextRequest/ContextPack carry Common Scope; authorization, cache, retrieval, and citations are partitioned by explicit isolation scope. |
| L7 SSOT | Authority/read/action/federation selectors accept Common Scope; canonical identifiers and access policy do not require project. |
| Trace/Evidence | events include `scope_ref`, `domain_id`, `isolation_scope_ref`, and only the overlay IDs actually present. |

## 10. Compiler / Validator contract

### 10.1 Compiler requirements

The Profile Resolver/Compiler SHALL:

- accept a scope with `project_id = null` or absent;
- require a resolvable `domain_id`;
- select Organization/Customer/Project as independent overlays;
- make overlay selection deterministic and independent of source file order;
- preserve the field-level operators in section 7;
- include every selected/rejected overlay and resolution reason in provenance;
- emit the same semantic EffectiveProfile and digest for the same normalized inputs, source revisions, and resolution-policy version.

### 10.2 Validator requirements

The Validator SHALL fail or require review for:

- missing Enterprise or Operating Domain (a scope without a resolvable `domain_id` is rejected);
- missing runtime isolation boundary;
- a consumer schema that marks `project_id` globally mandatory;
- implicit synthesis of a fake Project for permanent work;
- authority or responsibility conflict;
- human-required regression;
- weakened mandatory assurance/control;
- cross-isolation access using a different `isolation_scope_ref`;
- unknown field merge behavior;
- incompatible non-monotonic values proposed by two overlays at the same rank without a monotonic deterministic field operator or an approved Authority/precedence rule (CONFLICT / REVIEW_REQUIRED per section 6.2; never file order, timestamp, profile type, or last-write-wins);
- a scope-kind field (`organization_id`, `customer_id`, `project_id`, `usecase_id`, `process_id`) carrying more than one value.

The Validator SHALL NOT fail or require review solely because `project_id`, `organization_id`, `customer_id`, `usecase_id`, or `process_id` is absent.

### 10.3 Golden cases

At minimum the test suite MUST include:

1. permanent Finance work with no project;
2. SI delivery work with Customer + Project overlays;
3. Organization and Project overlays resolving independently;
4. authority conflict that fails closed;
5. no-relaxation test for Human-required / mandatory gate / allowed capability;
6. cross-isolation negative test where two scopes have different `isolation_scope_ref` values;
7. same-rank conflict: two overlays at the same rank propose incompatible non-monotonic values with no approved operator or precedence rule, producing CONFLICT / REVIEW_REQUIRED;
8. missing `domain_id` rejected;
9. a single `process_id` accepted alongside or without `usecase_id`, and a list-valued `process_id` rejected.

Case 1 is the `project_id`-absent acceptance case.

## 11. Template contract

The generalized template SHALL contain at least:

```text
bundle.yaml
scope.yaml
profiles/operating-domain.yaml
profiles/organization.yaml        # optional selection
profiles/customer.yaml            # optional
profiles/project.yaml             # optional
profiles/lifecycle.yaml
profiles/process.yaml
profiles/managed-work.yaml
profiles/execution.yaml
profiles/governance.yaml
profiles/context.yaml
profiles/assurance.yaml
```

A valid bundle MUST NOT require `profiles/project.yaml` to exist. If it exists, it is selected as a temporary overlay by scope predicate.

## 12. Relationship to the public specifications

The following specifications are current public cross-checks for this contract; the list does not assert that they are identical to the historical source documents.

| Public specification | Common-scope cross-check |
|---|---|
| `ALOM-PROFILE-RA-001` | Profile scope specificity, domain anchor, and optional overlays. |
| `ALOM-PROF-CONTRACT-SPEC-001` | Scope resolution, no-relaxation, and Profile binding. |
| `ALOM-PROF-CV-SPEC-001` | Project-less compilation and explicit isolation validation. |
| `ALOM-PROF-REG-STD-001` | Registry and Resolver scope selection. |
| `ALOM-RUNTIME-BIND-SPEC-001` | Runtime scope, optional Project, and required isolation boundary. |

### 12.1 Compatibility rule

For the fields defined here, consumers SHALL accept the CommonScopeContract and MUST NOT require a synthetic Project. A supplied `project_id` MAY be accepted; new implementations and tests SHALL target the generalized contract.

### 12.2 Figure source

A controlled document's figure source follows its reviewed migration state. While a document is a text mirror, the received DOCX remains the authority for its layout and figures; annotate a source figure that still shows the previous project-centric order in its caption rather than replacing that controlled figure. Once the document is managed, version-controlled repository figure sources and renders become the working source and may be redrawn by a reviewed change; the caption annotation may then be removed.

A separate public-facing derivative does not by itself replace the controlled figure source or change the document's migration state. Inclusion or omission of a figure in this edition does not itself change approval, Freeze, or Effective status.

## 13. Acceptance mapping

| Acceptance criterion | Contract evidence |
|---|---|
| Back-office work without synthetic Project | sections 4, 5.2 |
| SI/customer project remains representable | section 5.3 |
| Organization and Project not forced parent-child | sections 4.2, 6.2 |
| Permanent operating-domain concept | sections 3, 4.1 |
| ProjectProfile explicitly optional | sections 4.2, 5.1, 11 |
| Organization authority independent of Project lifetime | sections 4.3, 7.1 |
| Common Scope Contract for L1-L7 | sections 5, 9 |
| Security isolation not dependent on project_id | section 8 |
| Deterministic/no-relaxation resolver | sections 6, 7, 10 |
| SI and permanent back-office examples | sections 5.2, 5.3 |
| Cross-document mandatory-project review | sections 9, 12 |

## Revision history

| Version | Date | Change |
|---|---|---|
| Draft v0.2 | 2026-08-14 | Baseline of this companion contract. |
| Draft v0.3 | 2026-10-27 | Normative revision: single-valued scope fields, optional `process_id` at rank 40, and related validation and alignment. |
| Draft v0.4 | 2026-10-30 | Figure-source handling changed; the CommonScopeContract in sections 3–11 did not change. |
