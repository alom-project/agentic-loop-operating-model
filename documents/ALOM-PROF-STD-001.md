**IMPLEMENTATION STANDARD**

**ALOM Profile Engineering
& Generation**

**Implementation Architecture Standard**

Mission / Rule Resolution / Operating Model Generation / Work Decomposition / Execution Suitability / Human Control / Profile Compilation / Approval

| **Core principle** Use the applying organization's Rulebook and Canonical Knowledge, together with its Business Mission, as inputs to semi-automatically generate executable Operating Profiles for ALOM Managed Work. Generated results are DRAFT and become Effective only after Human Review / Approval. Assign human-only / interactive-agent / agentic / deterministic-system to each Work through a suitability assessment; do not replace responsibilities, interpersonal interactions, or approvals that humans must perform with Agent execution. |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|

| **Management item** | **Value**                                                          |
|--------------|---------------------------------------------------------------------|
| Document ID       | ALOM-PROF-STD-001                                                   |
| Version           | v0.4-review.20261109                                                          |
| Created       | 2026-08-13                                                          |
| Governing standard     | ALOM-ARCH-STD-001 v2.5                                              |
| Primary scope       | ALOM Profile Engineering & Generation / L1 implementation subsystem |
| Owner     | Organization Architecture (Enterprise Architecture) / AI Platform                               |
| Joint responsibility     | Business Owner / Quality / Security and Privacy / Project Management   |
| Classification | Public |

This specification specifies a cross-cutting implementation Subsystem that generates the L1-owned Operating Model & Governance contracts from the applying organization's standards and Mission, without changing the governing ALOM-ARCH-STD-001 v2.5 (ALOM Integrated Architecture Standard) or the L1/L3/L5/L6/L7 implementation standards.

# **Document Control**

## **1. Position and Authority Precedence**

- This document conforms to ALOM-ARCH-STD-001 v2.5. Profile Engineering is an implementation Subsystem of L1 Operating Model & Governance, not an eighth Layer.

- This document does not change L1-L7 Authority. Referencing L6/L7 does not grant the Profile Generator Authority over Knowledge/Operational SSOT.

- Generated Profiles are AI Proposals / Drafts. Automatic promotion to the protected default branch or Effective Profile Registry is prohibited.

- If the governing standards, this document, or applicable laws, contracts, customer NDAs, or Security/Privacy rules conflict, the higher-authority or stricter constraints take precedence.

- \[STD\] indicates inheritance from governing/Layer standards; \[REF\] indicates adoption from existing references; \[PROPOSAL\] indicates implementation details added by this document.

| **Fixed boundary** Management of the applying organization (Corporate Management) determines Strategy / Market / Pricing / Capital Allocation / Revenue-Profit Target and related matters. Profile Engineering converts the resulting Business Mission / Objective / Demand / Constraint into ALOM Managed Work; it does not replace management decision-making itself. |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|

## **2. Sources and Design Classification**

| **ID** | **Source**                                  | **Use in this document**                                                                                             |
|--------|-------------------------------------------|--------------------------------------------------------------------------------------------------------------|
| S1     | ALOM-ARCH-STD-001 v2.5-review.20261110 (ALOM Integrated Architecture Standard) | Non-effective alignment candidate; controlled authority remains v2.5. Current normative baseline: seven Layers, ALE=L2-L4, L5 Shared Execution, Managed Work, Human Control, NFR, and conformance principles. |
| S2     | ALOM-L1-STD-001 v0.7-review.20261110                | PurposeRecord, ManagedWorkDefinition, ResponsibilityAssignment, Execution Mode, Outcome/SLO, Human Control. |
| S3     | ALOM-GRAPH-STD-001 v0.4-review.20261110 | Node types including Human Task, GraphSpec, GraphRun, Human Gate, and Dynamic Rewrite boundaries.                            |
| S4     | ALOM-HR-STD-001 v0.4-review.20261110 | Shared execution for Interactive Agent / Agentic, Harness, Runner, Tool, Isolation, and Trace.                               |
| S5     | ALOM-KNW-STD-001 v0.4-review.20261110 | Rulebook/Standard Context resolution, Authority/Revision, Ontology, Citation, and ContextPack.                        |
| S6     | ALOM-SSOT-STD-001 v0.5 | Canonical Knowledge, Authority Registry, Controlled Write, Revision/Provenance, Verification.               |

## **3. Document Status**

v0.3 standardizes Profile Engineering as an L1 implementation Subsystem and fixes suitability assessment to exactly four Execution Modes (human-only / interactive-agent / agentic / deterministic-system). hybrid is not an Execution Mode. human_required=true together with execution_mode=deterministic-system is an ERROR. This edition records the correspondence of Release lifecycle and Security state with Contract / WF.

# **Contents**

| **Chapter** | **Content**                                               |
|--------|--------------------------------------------------------|
| 1      | 1 Purpose and Scope                                       |
| 2      | 2 Fixed Definitions and Responsibility Boundaries                                   |
| 3      | 3 Profile Engineering Architecture Principles               |
| 4      | 4 Overall ALOM Stack and Position of Profile Engineering          |
| 5      | 5 Input Contracts: Mission / Rulebook / Constraints           |
| 6      | 6 Profile Model / Scope                            |
| 7      | 7 Mission Interpretation                               |
| 8      | 8 Rule / Standard Resolution                           |
| 9      | 9 Applicability Resolution                             |
| 10     | 10 Organization / Role / Responsibility Generation     |
| 11     | 11 Lifecycle / Process Generation                      |
| 12     | 12 Work Decomposition / Managed Work Generation        |
| 13     | 13 Execution Suitability Assessment                    |
| 14     | 14 Human Control / Human Execution Planning            |
| 15     | 15 Graph / Loop / Harness / Context Binding            |
| 16     | 16 Quality Gate / Assurance / Outcome / SLO Generation |
| 17     | 17 Profile Compilation / Validation / Conformance      |
| 18     | 18 Human Review / Approval / Lifecycle                 |
| 19     | 19 Provenance / Trace / Evidence                       |
| 20     | 20 Security / NDA / Isolation                          |
| 21     | 21 API / Event / Contract Architecture                 |
| 22     | 22 Repository / CI/CD / Versioning                     |
| 23     | 23 Physical Deployment Reference Configuration                                |
| 24     | 24 Nonfunctional Requirements / SLO / Observability                        |
| 25     | 25 Acceptance Gates and Conformance Tests                                |
| 26     | 26 Implementation Roadmap and Backlog                        |
| 27     | Appendix A Minimum Data Contracts                                   |
| 28     | Appendix B YAML Contract Examples                                       |
| 29     | Appendix C Execution Suitability Decision Matrix              |
| 30     | Appendix D Governing Requirement and Technical Element Mapping                 |

# **1. Purpose and Scope**

## **1.1 Purpose**

This document defines the standard for implementing ALOM Profile Engineering & Generation as a design and compilation Subsystem owned by the applying organization. It generates executable, auditable ALOM Operating Profiles that can be approved, using the organization's Canonical Rulebook and Business Mission.

Profile Engineering resolves the organization's standards, customer constraints, contracts, quality, Security, Project Management, and development/operations standards applicable to the Mission from L6/L7, and transforms them into the Profile Types and overlays applicable to the target Scope. Humans MUST review every generated result as a Draft. Only approved Profiles are reflected in the L1 Managed Work Catalog and the execution contracts of lower Layers.

| **Design goal** When starting a new business, Project, or operation, reproducibly generate candidate structures from standards, then have humans verify and approve their validity, responsibilities, and exceptions, instead of manually rereading the applying organization's Rulebook and designing the Operating Model from scratch each time. |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|

## **1.2 In Scope**

- Generate Profile Drafts from Business Mission / Objective / Demand / Constraint.

- Resolve the applying organization's Rulebook, Project standards, development standards, quality standards, Security, Review standards, Criteria, and customer/contract rules.

- Generate applicable Profile Types and Scope overlays. Organization / Customer / Project are optional peer overlays; a Project is not required for every Work.

- Generate organizational Unit, Role, Responsibility, Authority, and Human/Agent Assignment conditions.

- Generate the Processes and Gates required by the applicable Work and Rules. Project Phase is an example when applicable; Entry/Exit Criteria, Quality Gate, Technical Review, and Test/Acceptance/Migration also follow their applicability conditions.

- Assign human-only / interactive-agent / agentic / deterministic-system Execution Mode, Risk, Autonomy, and Human Control to each Managed Work.

- Generate bindings to L3 Graph, L4 Loop, L5 Harness, L6 Context, and L7 Authority as required by Execution Mode and Graph use.

- Profile Validation, Conformance, Human Review/Approval, Versioning, Trace, Provenance, and Drift detection.

## **1.3 Out of Scope**

- Final decisions by management of the applying organization (Corporate Management), including business strategy, investment, pricing, and contract execution.

- Personnel systems themselves, final authorization of organizational restructuring, and final decisions on assigning or evaluating actual people.

- LLM internal reasoning, chain-of-thought, and model weights.

- AI implicitly creating new Rules absent from governing standards, laws, or contracts.

- Automatic transition from a generated Profile to a Production Action without Human Approval.

## **1.4 Conformance Units**

| **Conformance unit**               | **Required artifacts**                                                                            |
|----------------------------|-------------------------------------------------------------------------------------------|
| Profile Generation Service | MissionInput / RuleResolutionSet / DraftProfileBundle / ValidationReport / ApprovalRecord |
| Business/Project Profile   | Purpose, applicable standards, organization, Lifecycle, Outcome, Risk, Authority                                 |
| Managed Work Profile       | Purpose, Owner, Responsibility, Execution Mode, Risk, Autonomy, Evidence, Binding         |
| Effective Profile Release  | Approved ProfileBundle + source revisions + compiler version + approval evidence          |

# **2. Fixed Definitions and Responsibility Boundaries**

| **Term**              | **Fixed definition**                                                                                                         | **Not equivalent to**                   |
|-----------------------|----------------------------------------------------------------------------------------------------------------------|----------------------------------------|
| Profile Engineering   | An L1 implementation subsystem that generates and validates ALOM Operating Profiles from Mission and Canonical Rule/Knowledge and prepares them for approval. | An eighth Layer / ALE / simple Prompt generation      |
| Profile Generator     | A Component that generates structured candidate Profiles. It has no Authority and generates Drafts only.                                           | Policy Decision Point / Human Approver |
| Profile Compiler      | A Component that deterministically assembles multiple Profiles into a consistent ProfileBundle from Resolved Rules and Mission.                        | Free-form text generation by an LLM alone                    |
| Business Mission      | An input contract specifying the objectives, customers/markets/Outcomes, and constraints given by management of the applying organization (Corporate Management).                                      | The applying organization's strategy itself                       |
| Rulebook              | The set of Canonical Knowledge approved by the applying organization, including Policy/Standard/Process/Criteria/Role/Quality/Security.                    | Search Index / AI summary                     |
| Resolved Rule         | An executable Rule with resolved applicability, conditions, requirements/prohibitions/options, Authority, Evidence, and source Revision.                        | Rules expressed only in natural language                   |
| Application Profile   | Concrete Operating conditions, SLO, Risk, Authority, and Binding applicable to a specific Business/PJ/Use Case.                             | Governing standard                               |
| ProfileBundle | A release-candidate unit combining the Profile Types and overlays applicable to the target Scope with a Manifest. Organization / Customer / Project are optional peer overlays, not a mandatory parent chain. | A single enormous YAML file |
| Execution Suitability | A contract assessing Agent executability, delegability, Risk, interpersonal requirements, responsibility, and independence for each Work.                                | Model capability assessment alone                     |
| Human-required Work   | Work that requires Human execution because of responsibility, interpersonal interaction, law/contract, Authority, or other factors, even if an Agent has the capability to execute it.               | Only Work that Agents perform poorly                |
| Effective Profile     | An execution Profile that has completed Human Review/Approval and has a fixed effective window, target Scope, and source revision.                       | A Draft immediately after Generator output               |

| **Responsibility boundary** Profile Engineering generates proposals for an executable Operating Model. L1 owns the final Managed Work / Authority / Policy / Outcome contracts; L2-L7 each own their respective Runtime responsibilities. |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|

# **3. Profile Engineering Architecture Principles**

| **ID**   | **Principle**                            | **Normative requirement**                                                                                                              |
|----------|-------------------------------------|-----------------------------------------------------------------------------------------------------------------------|
| PROF-P01 | Canonical-first                     | Obtain Rules/Standards/Roles/Criteria other than Mission from Canonical sources that resolve to L7 Authority.                      |
| PROF-P02 | Draft-only generation               | AI/Generator generates Drafts/Proposals only. Becoming Effective requires Human Approval.                                     |
| PROF-P03 | No invented rule                    | If a Rule cannot be resolved, is ambiguous, or conflicts, do not guess; return it to a Human as UNRESOLVED / CONFLICT.                                  |
| PROF-P04 | Mission-to-work traceability        | Make every Managed Work traceable back to its Mission/Purpose and applicable Rules.                                                     |
| PROF-P05 | Human suitability before automation | Evaluate Human-required conditions before Agent capability, and do not let automation rates erode responsibility, interpersonal requirements, or Authority.                    |
| PROF-P06 | Execution mode explicit             | Determine human-only / interactive-agent / agentic / deterministic-system through a structured decision for each Work. Implicit fallback is prohibited.                            |
| PROF-P07 | Organization as contract            | Generate separate Unit/Role/Responsibility/Authority/Assignment conditions, rather than organizational names alone.                                   |
| PROF-P08 | Rule precedence explicit            | Record precedence and conflict outcomes for law/contract/NDA/organization-wide rules / Domain/PJ/UseCase in the Manifest.                                       |
| PROF-P09 | Deterministic core + AI assistance  | Process Schema validation, applicability, precedence, mandatory gates, and related checks deterministically. Limit AI to semantic extraction and candidate generation. |
| PROF-P10 | Evidence-first approval             | The Approver can inspect the generation rationale, source revision, unresolved items, differences, Risk, and rationale for Human/Agent assignment.                        |
| PROF-P11 | Living profile                      | Detect Profile Drift as Rulebook/Mission/Resource changes, then regenerate→Review→Release.                                |
| PROF-P12 | Portability                         | Preserve Profile Schema and Conformance semantics when changing the LLM/Agent/Workflow/Profile Engine.                        |
| PROF-P13 | Scoped generation                   | Inherit Tenant/Customer/PJ/NDA/Classification/Purpose Scope before Retrieval. Cross-scope references are prohibited.              |
| PROF-P14 | Independent conformance             | Do not pass a Profile solely on the Generator's self-evaluation. Independently deploy Validator/Rule Engine/Policy/Human Review.           |

# **4. Overall ALOM Stack and Position of Profile Engineering**

Management of the applying organization (Corporate Management)
Business Mission / Objective / Demand / Constraint
\|
v
L1 Operating Model & Governance
+------------------------------------------------------+
\| Profile Engineering & Generation Subsystem \|
\| Mission -\> Rule Resolve -\> Generate -\> Validate \|
\| -\> Human Review -\> Approved ProfileBundle \|
+------------------------------------------------------+
\|
+--------------+------------------------------+
\| \| \| \|
v v v v
L2-L4 ALE L5 Shared L6 Context L7 SSOT
Agentic Work Execution & Knowledge Authority
\| \| ^ ^
+--------------+--------------+---------------+
\|
Human / Interactive / Agentic Work

## **4.1 Internal Subsystem Capabilities**

| **No.** | **Capability**         | **Primary responsibilities**                             | **Primary artifacts**             |
|---------|------------------------|------------------------------------------|----------------------------|
| P1      | Mission Intake         | Normalize Mission/constraints and establish scope      | MissionSpec                |
| P2      | Rule Resolution        | Discover Rulebooks and resolve authority/revision     | RuleResolutionSet          |
| P3      | Applicability          | Determine applicability/exclusions/conditions/precedence            | ApplicabilityDecision      |
| P4      | Organization Modeling  | Generate Unit/Role/Responsibility/Authority   | OrganizationProfile        |
| P5      | Lifecycle Modeling     | Generate Phase/Process/Gate/Criteria          | LifecycleProfile           |
| P6      | Work Decomposition     | Decompose Work Units and assign Purpose/Owner/Outcome | ManagedWorkProfile\[\]     |
| P7      | Suitability Assessment | Determine human-only / interactive-agent / agentic / deterministic-system suitability            | ExecutionSuitabilityResult |
| P8 | Binding | Resolve applicable Graph / Loop / Harness / Context / Authority refs according to Mode and Graph use | ExecutionBinding |
| P9 | Compiler | Compose and pin applicable Profile Types and Scope overlays | DraftProfileBundle |
| P10     | Validator              | Check Schema/Rule/Conformance/Conflict     | ValidationReport           |
| P11     | Approval Workflow      | Human Review/Decision/Exception          | ApprovalRecord      |
| P12     | Lifecycle & Drift      | Release/Revision/Drift/Recompile         | ProfileReleaseManifest     |

## **4.2 Layer Integration Boundaries**

| **Layer** | **What Profile Engineering requests**             | **What the Layer owns**                  |
|-----------|---------------------------------------------------|------------------------------------------|
| L1        | Candidate Purpose/Work/Role/Policy/Outcome/Profile registrations  | Final Management/Governance Authority      |
| L2        | Candidate Task/entry conditions for agentic Work                  | Durable orchestration / Task state       |
| L3        | Candidate GraphSpec/Node/Human Task configurations                 | Topology/Routing/Join/Graph completion   |
| L4        | Candidate LoopSpec/success/eval/termination conditions             | Loop convergence semantics               |
| L5        | Harness/Runner capability conditions for interactive/agentic execution | Execution enforcement / Tool / Isolation |
| L6        | Rulebook/Knowledge/Context retrieval requests                | Meaning/Retrieval/Context                |
| L7        | Canonical source/revision/authority references           | Truth/Authority/Record                   |

# **5. Input Contracts: Mission / Rulebook / Constraints**

## **5.1 MissionSpec**

Do not accept Mission solely as free text. Structure at least the purpose, target customers/services, expected Outcome, Scope, deadline, constraints, and Authority Owner. Retain free text as supplementary explanation.

| **Field**  | **Required** | **Meaning**                             |
|-----------------|----------|--------------------------------------|
| mission_id      | MUST     | Unique identifier                           |
| objective       | MUST     | Objective to achieve                             |
| business_owner  | MUST     | Mission owner                        |
| scope           | MUST     | tenant / enterprise / domain (Operating Domain `domain_id`; formerly business) / organization? / customer? / project? / usecase? / process? |
| target_outcomes | MUST     | Expected Operational/External outcome     |
| constraints     | MUST     | time/cost/security/contract/resource |
| rulebook_roots  | MUST     | Reference starting point                           |
| assumptions     | MAY      | Explicit assumptions                             |
| validity        | MUST     | Effective window                             |

## **5.2 Rulebook Source**

As a rule, Rulebooks are Approved Knowledge in L7 Knowledge SSOT. L6 resolves source/revision/authority and returns Context with Citations to Profile Engineering. Derived Indexes and AI summaries may support discovery but do not constitute Authority.

## **5.3 Constraint Classes**

| **Class**           | **Example**                           | **Priority**                      |
|---------------------|----------------------------------|---------------------------------|
| Legal / Regulatory  | Laws, regulations, and supervisory requirements             | Highest                          |
| Contract / Customer | Contracts, NDAs, and customer-specific standards          | Take precedence when stricter than the applying organization's standards |
| Policy of the applying organization (Corporate Policy)    | Organization-wide Security, quality, AI use, and approval | Common baseline                |
| Domain / Business   | Business/operation-specific rules                | Within the target Domain                    |
| Project Standard    | PJ methodology, phases, artifacts, and Gates       | Within the target PJ                        |
| UseCase Profile     | Work-specific SLO/Autonomy/Harness     | Lower-level specialization                      |

| **MUST** Profile generation MUST NOT be considered complete for a Mission whose applicable Rulebook roots cannot be resolved. At minimum, send it for Human Review as DRAFT_WITH_UNRESOLVED. |
|-------------------------------------------------------------------------------------------------------------------------------------------------------|

# **6. Profile Model / Scope**

## **6.1 Profile types and scope**

A Profile Type classifies contract responsibilities; scope identifies applicability and specificity. Neither establishes a mandatory parent-child chain. Under ALOM-PROF-SCOPE-SPEC-001 §3 and §6.2, BusinessProfile is the Profile Type for the required permanent Operating Domain anchor. Organization / Customer / Project are independent optional overlays at rank 30; UseCase / Process are parallel optional overlays at rank 40. Permanent work without a Project remains representable. Lifecycle / ManagedWork / Execution / Governance / Context / Assurance and other Profile Types are composed according to their responsibilities and applicability; their names or display order do not themselves establish inheritance precedence.

A lower-level specialization MUST NOT relax applicable higher-level prohibitions, Authority ceilings, or minimum Quality Gates. Inheritance and merge follow field-level operators, Authority, and same-rank conflict rules; Human Approval and source provenance remain required.

## **6.2 Profile type**

| **Profile**         | **Main content**                                             | **Update unit** |
|---------------------|----------------------------------------------------------|--------------|
| BusinessProfile     | Mission, service boundary, Outcome, Business Owner       | Business/Service |
| ProjectProfile      | PJ objectives, contract, delivery model, risk, resource, governance | PJ           |
| OrganizationProfile | Unit, Role, Responsibility, Authority, assignment rule   | PJ/organization      |
| LifecycleProfile    | Phase, entry/exit, gate, mandatory artifact              | PJ/methodology    |
| ProcessProfile      | Procedures, input/output, and review for a specific phase                     | Process      |
| ManagedWorkProfile  | Purpose/owner/execution/risk/evidence/binding            | Work/UseCase |
| ExecutionProfile    | ALE/L5/Harness/Runner/Tool/budget                        | Work/Node    |
| GovernanceProfile   | Policy, Human control, approval, exception and remedy | Policy/Work |
| ContextProfile      | Knowledge roots, Authority, freshness and citation | Context/Work |
| AssuranceProfile    | Eval/Review/Oracle/Criteria/independence                 | Work/Gate    |

## **6.3 Profile Resolution**

Compose the Effective Profile according to the specificity ranks in ALOM-PROF-SCOPE-SPEC-001 §6.2: organization-wide (Enterprise)→Operating Domain (required)→Organization / Customer / Project (rank 30, parallel optional overlays)→UseCase / Process (rank 40, parallel and optional)→Work. Record Source/Version/Precedence in the Manifest at each stage. If a conflict cannot be resolved automatically, mark it CONFLICT and require a Human Decision.

Organization / Customer / Project (rank 30) and UseCase / Process (rank 40) are parallel overlays within their respective specificity ranks, with no implicit ordering among them. When overlays of the same rank propose incompatible non-monotonic values, do not select by file order / timestamp / profile type / last-write-wins. Use a monotonic, deterministic field operator, an approved Authority / precedence rule, or CONFLICT / REVIEW_REQUIRED (ALOM-PROF-SCOPE-SPEC-001 §6.2). `project_id` (and `organization_id` / `customer_id` / `usecase_id` / `process_id`) is optional. Absence alone MUST NOT cause rejection unless a selected rule explicitly requires it for that Managed Work. Do not synthesize a Project to satisfy an implementation schema. Reject a missing `domain_id` (ALOM-PROF-SCOPE-SPEC-001 §5.1 / §10.2). Each scope kind field is single-valued (an ID or null), never a list. Split work spanning departments into a Managed Work per department (ALOM-PROF-SCOPE-SPEC-001 §5.1).

# **7. Mission Interpretation**

## **7.1 Processing Flow**

1.  Validate MissionSpec against its Schema.

2.  Extract candidate domain/customer/project class/risk attributes from the Mission.

3.  Generate candidate questions for missing information and identify unresolved attributes explicitly.

4.  Decompose the Mission into candidate Purposes, Outcomes, and Work scopes.

5.  Have the Mission Owner confirm the interpretation of the input.

## **7.2 AI Usage Boundary**

The Mission Interpreter MAY use an LLM to extract structured candidates from natural language. However, AI MUST NOT newly determine the Mission's business objectives, contractual commitments, authority, or risk acceptance.

## **7.3 Mission Interpretation Result**

| **Item**              | **Status**                          |
|-----------------------|-----------------------------------|
| interpreted_objective | CONFIRMED / PROPOSED / UNRESOLVED |
| scope                 | CONFIRMED / PROPOSED / CONFLICT   |
| target_outcomes       | CONFIRMED / PROPOSED              |
| project_type          | PROPOSED                          |
| risk_hints            | PROPOSED                          |
| questions             | Unresolved items requiring Human confirmation       |
| source_ref            | Mission input Revision               |

# **8. Rule / Standard Resolution**

## **8.1 Rule Resolution Flow**

Mission / Scope
\|
v
L6 ContextRequest
\|-- Metadata / Full-text / Semantic / Ontology
\|-- Authority / Revision / Classification filter
v
Candidate Rules
\|
v
Applicability + Precedence + Citation
\|
v
ResolvedRuleSet
\|-- APPLICABLE
\|-- NOT_APPLICABLE
\|-- CONDITIONAL
\|-- UNRESOLVED
+-- CONFLICT

## **8.2 Rule structure**

| **Attribute**              | **Description**                                                 |
|-----------------------|----------------------------------------------------------|
| rule_id               | Rule identifier                                                 |
| rule_type             | policy/process/criteria/role/quality/security/review/etc |
| source_ref / revision | Canonical provenance                                     |
| applies_when          | Applicability conditions                                                 |
| requires              | Required actions/artifacts/roles/gates                                |
| prohibits             | Prohibitions                                                 |
| authority             | Who decides/approves                                      |
| evidence              | Required evidence                                                 |
| precedence            | Conflict precedence                                             |
| interpretation_status | STRUCTURED / AI_EXTRACTED / HUMAN_CONFIRMED              |

## **8.3 Structuring Natural-Language Rules**

When using natural-language rules directly as Runtime conditions, explicitly mark extracted Rules as AI_EXTRACTED and require Human Confirmed status for important Rules. The Profile Compiler handles trust levels according to interpretation_status and MUST NOT automatically adopt unconfirmed high-Risk Rules into Production Profiles.

# **9. Applicability Resolution**

## **9.1 Decision Logic**

For each Rule, the Applicability Resolver evaluates Mission/PJ attributes against applies_when and returns APPLICABLE / NOT_APPLICABLE / CONDITIONAL / UNRESOLVED / CONFLICT. Use a deterministic Rule Engine wherever possible.

## **9.2 Representative Conditions**

| **Condition axis**          | **Example**                                              |
|---------------------|-----------------------------------------------------|
| Project class       | new development / renewal / maintenance / migration |
| Scale               | small / medium / large / critical                   |
| Customer            | internal / external / regulated                     |
| System criticality  | low / medium / high / mission critical              |
| Data classification | internal / confidential / restricted                |
| Delivery model      | waterfall / iterative / agile / hybrid              |
| Contract            | fixed-price / T&M / SLA / acceptance                |
| Technology          | cloud / on-prem / package / custom                  |
| Risk                | security / safety / financial / reputational        |

## **9.3 Rule Conflict**

Automatically resolve a Conflict only when the stricter constraint can be selected mechanically. For semantic Conflicts involving Authority, responsibility, contract interpretation, or similar matters, generate a Human Decision Packet and store the resolution record in Profile provenance.

# **10. Organization / Role / Responsibility Generation**

## **10.1 Model Principles**

Separate organizational Unit, Role, Responsibility, and Assignment. A Role is a type of continuing responsibility; a Responsibility is a duty toward a target Work; an Assignment binds it to an actual Principal. As a rule, the Profile Generator generates only Roles/Responsibilities; Human Authority makes the final decision on individual Assignments.

## **10.2 SI Project Example**

| **Category**          | **Candidates**                                                                                      |
|-------------------|-----------------------------------------------------------------------------------------------|
| Organization Unit | Business / Project Management / Application Team / Infrastructure Team / Quality Assurance        |
| Role              | Business Owner / PM / PMO / PL / Team Leader / Member / Quality Manager                       |
| Responsibility    | Design, Test planning, implementation and UT, IT, ST, UAT support, migration planning, migration execution, Technical Review, Quality Gate |
| Authority         | requirement approval / design approval / phase exit / go-no-go / exception / stop-resume      |

## **10.3 Independence Rule**

When the Rulebook requires independence for Quality Assurance or Approval, prohibit the same Principal/Role from combining definition/execution/approval, or subject that combination to Human Review. The Generator may leave missing Roles as "required but unassigned".

| **Practical operation** Profile generation need not stop when personnel have not yet been selected. Define Role/Responsibility/Authority first and bind Principals at Project startup. This separates organizational design from staffing. |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|

# **11. Lifecycle / Process Generation**

## **11.1 Lifecycle Generation**

Extract Phase, Entry Criteria, Mandatory Work, Deliverable, Review, Exit Criteria, and Authority from the Project Standard and convert them into a LifecycleProfile.

| **Example Phase** | **Example mandatory Processes**                                          | **Example Exit Authority** |
|-------------|------------------------------------------------------------|----------------------|
| Planning/concept   | Mission confirmation, proposal, estimation, Risk assessment                          | Business Owner       |
| Requirements definition    | Customer interviews, requirements analysis, requirements review, requirements approval           | Customer / PM        |
| High-level design    | Architecture/Interface/Data/Security design, Technical Review | PL / Quality         |
| Detailed design    | Component design, Review, Test design                            | PL                   |
| Implementation and UT    | Implementation, Code Review, Unit Test                     | Team Leader          |
| Integration Test    | IT Plan/Execution/Defect closure                           | Test Lead / Quality  |
| System Test | ST Plan/Execution/Quality evaluation                       | Quality Manager      |
| UAT         | Acceptance support, Issue closure                          | Customer Authority   |
| Migration        | Migration Plan/Trial/Go-No-Go/Production migration         | PM / Customer / Ops  |

## **11.2 Gate Generation**

A Gate is a structured Contract with Entry/Exit Criteria, required evidence, decision authority, exception route, and failure action, rather than a Milestone alone.

# **12. Work Decomposition / Managed Work Generation**

## **12.1 Decomposition Principles**

- Decompose Work into units to which a single responsible party, clear Input/Output, Outcome, Evidence, and Execution Mode can be assigned.

- Do not treat a Phase name such as "high-level design" as one Work. Split it into design, review, Quality decisions, customer explanation, and other activities.

- Separate Decisions requiring Human Authority from Analysis/Preparation that AI can support into different Work Units.

- Express dependencies between Works as candidate L3 Graphs, rather than leaving them as document order alone.

## **12.2 Minimum ManagedWorkProfile Elements**

| **Element**               | **Content**                                 |
|------------------------|------------------------------------------|
| purpose_ref            | Traceability to Mission/Purpose                  |
| owner / responsibility | Role/Authority                           |
| inputs / outputs       | Artifact/SSOT reference                  |
| execution_mode         | human-only / interactive-agent / agentic / deterministic-system |
| risk / autonomy        | Risk class / A0-A4 ceiling               |
| criteria               | completion / quality / acceptance        |
| human_control          | approval/stop/escalation                 |
| assurance              | eval/review/oracle/evidence              |
| binding                | Graph/Loop/Harness/Context/SSOT          |
| trace                  | required evidence / retention            |

## **12.3 Example: Requirements Definition**

| **Work**                       | **Execution Mode**             | **Responsible party**          |
|--------------------------------|--------------------------------|-----------------------|
| Customer interviews                 | human-only / interactive-agent | Business Analyst / PL |
| Organize requirements and analyze duplicates/conflicts        | agentic                        | Agent + Human owner   |
| Draft requirements                  | interactive-agent              | Requirement Engineer  |
| Technical feasibility analysis | agentic / interactive-agent    | Architect             |
| Requirements review                   | human-only / interactive-agent | PL / Reviewer         |
| Customer approval of requirements                   | human-only                     | Customer Authority    |

# **13. Execution Suitability Assessment**

## **13.1 Assessment Axes**

| **Axis**             | **Question**                                     | **Typical result**                  |
|----------------------|----------------------------------------------|-------------------------------|
| Capability           | Can an Agent meet the quality/SLO requirements?                  | Human/Interactive if not     |
| Delegability         | May authority be delegated to an Agent?                  | Human Authority if not       |
| Human Relationship   | Are trust building, negotiation, empathy, or social interaction essential? | Human execution               |
| Accountability       | Should a human retain accountability/legal responsibility?          | Human decision/approval       |
| Risk / Reversibility | Impact of errors and reversibility                       | A0-A4 / Human Gate            |
| Independence         | Is independent Review/Quality assessment required?               | Separate Human/Assurance role |
| Evidenceability      | Can successful Agent execution be verified externally?            | Affects Agentic eligibility             |
| Data / Security      | Confidentiality/NDA/external transmission constraints                        | Runner/Model restrictions or Human   |
| Determinism          | Can the work be standardized/automatically verified?                        | Suitable for Deterministic/Agentic execution     |

## **13.2 Decision Order**

6.  Evaluate Human-required conditions (Authority/interpersonal requirements/law/contract/independence).

7.  Evaluate Agent capability and verifiability.

8.  Determine the Risk/Autonomy ceiling.

9.  Select an Execution Mode from human-only / interactive-agent / agentic / deterministic-system.

10. Assign the required Human Gate / Stop / Escalation.

11. Store the rationale and Rule/Evidence.

| **Important** Do not equate "an Agent can execute this" with "an Agent should execute this". Customer negotiations, requirements approval, final Quality decisions, Go/No-Go, and similar activities may be classified Human-required even when Agents can assist. |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|

# **14. Human Control / Human Execution Planning**

## **14.1 Incorporating Human Work**

The Profile Compiler incorporates human-only Work and Human Tasks into Graphs/Processes as first-class Work Units. During Human execution, L6 Context, L7 SSOT, L5 Interactive Agent, and deterministic Tools can still be used.

Agentic analysis -\> Human customer negotiation -\> Agentic structuring
-\> Human requirement approval -\> Agentic design -\> Human review
-\> Agentic test -\> Human quality gate -\> Human go/no-go

## **14.2 Human Task Packet**

| **Element**      | **Required content**                            |
|---------------|-----------------------------------------|
| reason        | Why a Human is required                       |
| required_role | Required Role/Authority                      |
| context       | L6 ContextPack / source revision        |
| evidence      | Artifacts/assessments required for the decision                 |
| options       | Options/impact                             |
| reversibility | Cancellation/rollback feasibility                     |
| deadline      | Deadline/timeout action                     |
| output        | Decision / artifact / evidence contract |

## **14.3 Human-assisted Execution**

In interactive-agent mode, the Human is the outer controller and uses the L5 Shared Execution Plane. Activities such as organizing discussion points before customer negotiations, retrieving past requirements, drafting minutes, and analyzing differences can be delegated to an Agent while the Human retains interpersonal actions and final Authority.

# **15. Graph / Loop / Harness / Context Binding**

## **15.1 Binding Generation**

| **Target** | **Generated references**                                         | **Condition**                         |
|----------|----------------------------------------------------------|----------------------------------|
| L3 Graph | graph_ref / node type / edge / join / human node         | Dependencies/parallel execution/decisions across multiple Works         |
| L4 Loop  | loop_ref / success / eval / repair / termination         | Iterative Work with execution_mode=agentic |
| L5       | shared_execution_profile / harness / runner capability   | interactive-agent or agentic   |
| L6       | context_profile / knowledge roots / freshness / citation | Shared by Human/Interactive/Agentic    |
| L7       | authority refs / read/write boundary / verification      | Work requiring Canonical read/write |

## **15.2 Binding missing**

Fail Profile Validation if execution_mode=agentic has no resolvable ALE entrypoint, interactive-agent has no L5 execution profile, or an SSOT write is requested but Action Gateway/Authority is unknown.

## **15.3 Human-only and L5 and Below**

human-only Work does not require L5 but may use L6/L7 as needed. If interactive assistance becomes necessary, create a separate interactive-agent Work Unit or make an explicit Execution Mode change. Do not implicitly promote the Work to Agentic execution.

# **16. Quality Gate / Assurance / Outcome / SLO Generation**

## **16.1 Quality Gate**

Generate candidate Quality Gates from Quality Standards, Review Standards, and Criteria. Fix the required artifact, criterion, independent reviewer, decision authority, and exception route for each Gate.

## **16.2 Assurance Placement**

| **Assurance mechanism**          | **Example application**                                       |
|-----------------------|--------------------------------------------------|
| Deterministic Eval    | schema, lint, test, coverage, trace completeness |
| Private Eval          | Design quality rubrics, requirements quality, document quality               |
| External Oracle       | CI, monitor, Operational SSOT, actual environment results        |
| Human Review          | Technical Review, Quality decisions, customer approval          |
| Independent Assurance | Quality management function, Security Review, third-party verification        |

## **16.3 Outcome / SLO**

The Profile Generator may generate SLO candidates from the Rulebook, but MUST NOT invent arbitrary values when numerical targets are unspecified. Mark undefined targets UNRESOLVED and request them from the Business/PJ Owner. Separate Quality / Flow / Human Effort / Cost / Risk.

# **17. Profile Compilation / Validation / Conformance**

## **17.1 Compilation Pipeline**

MissionSpec
+ RuleResolutionSet
+ ApplicabilityDecision\[\]
+ Organization/Lifecycle/Work models
+ SuitabilityResult\[\]
\|
v
Profile Compiler
\|
v
Draft ProfileBundle
\|
+-------+--------+
v v
Schema Validator Conformance Engine
\| \|
+-------+--------+
v
ValidationReport
\|
v
Human Review

## **17.2 Validation categories**

| **Category**   | **Representative checks**                                     |
|----------------|--------------------------------------------------|
| Schema         | required field / enum / reference                |
| Source         | Every Rule/Standard resolves to Authority+Revision    |
| Precedence     | Resolution records for conflicting Rules                               |
| Responsibility | Missing Owner/Approver/Stop authority              |
| Execution      | Consistency between Mode and ALE/L5 bindings                         |
| Human          | Human-required Work is not incorrectly assigned to Agentic execution |
| Assurance      | No missing mandatory Gates/Reviews/Evidence           |
| Security       | No Scope/NDA/classification violations                 |
| Traceability   | Mission→Rule→Profile→Work→Binding is traceable        |

## **17.3 Conformance severity**

| **Severity**    | **Meaning**                                 | **Eligibility to become Effective** |
|-----------------|------------------------------------------|-----------------|
| ERROR           | Normative violation/missing Authority/Security conflict | Not permitted            |
| REVIEW_REQUIRED | Ambiguous Rule/important AI interpretation/responsibility decision           | Permitted after Human resolution   |
| WARNING         | Recommendations/noncritical omissions                    | Approver's decision      |
| INFO            | Explanations/optimization candidates                          | Permitted              |

# **18. Human Review / Approval / Lifecycle**

## **18.1 Approval Gate**

Making a ProfileBundle Effective requires approval by at least the Business/PJ Owner and, where necessary, Quality, Security/Privacy, Architecture, and Customer Authority. Resolve the Approver set from the Rulebook.

## **18.2 Information the Review UI Must Display**

- Mission and Scope, and the applied Rulebook release/revision.

- Generated organization/Role/Responsibility/Lifecycle/Managed Work list.

- human-only / interactive-agent / agentic / deterministic-system assignments and Suitability rationale.

- Mandatory Quality Gates, Approvals, and Exception routes.

- UNRESOLVED / CONFLICT / WARNING.

- Differences from the previous Profile and the Rule changes that caused them.

- Generator/Compiler/Model versions and Validation results.

## **18.3 Lifecycle**

| **State**  | **Meaning**                       |
|------------|--------------------------------|
| DRAFT      | Immediately after generation. Not executable.           |
| IN_REVIEW  | Under Human Review.               |
| APPROVED   | Approved but not yet Released.        |
| EFFECTIVE  | Executable within the designated Scope/window.     |
| SUSPENDED  | New use is stopped by an operational hold. |
| SUPERSEDED | Replaced by a new Profile.              |
| RETIRED    | No longer applicable.                     |

`SUSPENDED` indicates an operational stop due to an Incident, Rule change, or similar cause. While an effective HOLD exists in the Registry's append-only OperationalHoldRecord, the Resolver rejects new use of the affected release/source/scope, taking precedence over pointer / pin / LKG. Lifting the hold requires an explicit CLEAR by an authorized actor and revalidation; it is not automatic. Release lifecycle and Security state `REVOKED` remain unchanged. `RETIRED` corresponds to `RETIRED` in the Contract Release lifecycle. `VALIDATED`, which is absent from this table, corresponds to the Contract / WF validator-gate (between `DRAFT` and `IN_REVIEW`).

# **19. Provenance / Trace / Evidence**

## **19.1 Profile Provenance**

An Effective Profile MUST make it possible to reproduce its sources, Compiler Version, Rule interpretations, and approvers.

| **Provenance**    | **Example**                                    |
|-------------------|-------------------------------------------|
| Mission revision  | mission://customer-a/core@3               |
| Knowledge release | okf-release://company-rules/2026.08       |
| Rule source       | quality-standard@commitSHA                |
| Generator         | profile-generator 0.1.0 / model ref       |
| Compiler          | profile-compiler 0.1.0                    |
| Validation        | validation-report digest                  |
| Approval          | approval_id / actors / roles / timestamps |
| Bundle digest     | immutable ProfileBundle digest            |

## **19.2 Trace Events**

| **event_type**                | **Content**                           |
|-------------------------------|------------------------------------|
| profile.generation.started    | Mission/Scope/actor                |
| rule.resolved                 | rule/source/revision/applicability |
| profile.work.generated        | work/reason/source                 |
| execution.suitability.decided | mode/reason/rules                  |
| profile.validation.failed     | error/ref                          |
| profile.review.requested      | approvers/unresolved               |
| profile.approved              | decision/evidence                  |
| profile.released              | version/digest/effective window    |
| profile.drift.detected        | changed source/impact              |

# **20. Security / NDA / Isolation**

## **20.1 Security baseline**

- Before Rule retrieval, resolve tenant / `isolation_scope_ref` (including any customer / project overlays present) / NDA / classification / purpose.

- Do not provide unnecessary customer or personal information to the Profile Generator.

- Limit cross-isolation Rule/Knowledge references (different `isolation_scope_ref`, including cross-project / cross-customer) to common standards explicitly authorized by the Authority Registry and Policy.

- Do not store Secrets/credentials/tokens in a Profile Bundle. Resolve short-lived Credentials at runtime in L5/L7.

- Determine whether external LLM use is allowed from data classification and agent_usage policy.

- When processing personal information for Human Assignment candidates, use only the minimum necessary attributes and permissions.

## **20.2 Fail-Closed Conditions**

| **Condition**                       | **Behavior**                             |
|--------------------------------|--------------------------------------|
| Unknown Authority                  | Profile cannot become Effective              |
| NDA scope conflict             | Stop Retrieval/Generation             |
| Required approval unavailable  | Auto-approval prohibited                     |
| Rulebook revision unavailable  | last-known-good or Review Required |
| Security rule conflict         | Stricter Rule or Human decision   |
| Profile tamper/digest mismatch | Reject execution                             |

# **21. API / Event / Contract Architecture**

## **21.1 API Surface**

| **API**                   | **Purpose**                                |
|---------------------------|-----------------------------------------|
| mission.submit / validate | Mission input/validation                        |
| rules.resolve             | Rulebook resolution through L6                    |
| profile.generate          | Generate a Draft ProfileBundle                 |
| profile.validate          | Schema/Conformance validation                  |
| profile.diff              | Differences between previous version and candidate                           |
| profile.review.request    | Start Human Review                        |
| profile.review.decide     | Approve/Reject/Revise                   |
| profile.release           | Approved→Effective Release              |
| profile.resolve           | Resolve an Effective Profile for a Scope/Work |
| profile.drift.check       | Source revision changes and impact assessment           |

## **21.2 ProfileGenerationRequest**

Requests contain mission_ref, scope, target_profile_type, rulebook_roots, requested_by, generation_policy, max_risk, and effective_target. An LLM Prompt alone MUST NOT serve as the API contract.

## **21.3 Canonical Event**

Include event_id / timestamp / actor / mission_ref / profile_ref / source_refs / compiler_version / trace_id / reason / result in events and correlate them from generation through Release.

# **22. Repository / CI/CD / Versioning**

## **22.1 Recommended Repository Structure**

alom-profile-engineering/
schemas/
mission/ profile/ rule/ suitability/
compiler/
resolvers/
validators/
policies/
templates/
evals/
tests/
examples/
migrations/

alom-profiles/
business/
projects/
organizations/
lifecycles/
managed-work/
releases/

## **22.2 Change Gate**

- Schema/Compiler/Rule Template changes follow Issue→branch→change request→CI→CODEOWNERS→Human Approval.

- Manage Compiler version and Profile schema version independently.

- Pin source revision and compiler version in the Manifest for each Profile release.

- Backward-incompatible changes require migration tests and tests that reproduce older Profiles.

## **22.3 Required CI Tests**

| **Test**                  | **Minimum condition**                                  |
|---------------------------|-----------------------------------------------|
| Schema validation         | All examples/profiles pass                        |
| Golden generation         | The same Mission+Rule release yields the same semantic result |
| Conflict tests            | No automatic allow for ambiguity/conflict                 |
| Human-required regression | Customer approval, Quality decisions, and similar activities do not change to agentic or deterministic-system   |
| Scope isolation           | 100% deny for cross-isolation negative tests (different `isolation_scope_ref`, including cross-project / cross-customer) |
| Traceability              | Every Work traces back to Mission+Rule                    |
| Portability               | Profile schema remains compatible with a second LLM/Generator        |

# **23. Physical Deployment Reference Configuration**

## **23.1 Phase 1 Minimum Configuration**

\[User / Architect / PM\]
\|
v
\[Profile Review UI/API\]
\|
+--\> \[Profile Generation Service\]
\| \|-- Mission Interpreter
\| \|-- Rule Resolver
\| \|-- Compiler / Validator
\| +-- Suitability Evaluator
\|
+--\> \[L6 Knowledge API / MCP\]
\| +--\> \[OKF / Rulebook on L7 Git hosting (e.g., GitHub)\]
\|
+--\> \[L1 Governance API\]
\|
+--\> \[Git hosting change request / Approved Profile Registry\]
\|
v
ALOM Runtime

## **23.2 Candidates for Separation at Scale**

| **Component**           | **Reason for separation**                     |
|-------------------------|----------------------------------|
| Rule Resolution Service | Retrieval load and Access policy separation |
| Compiler Service        | Deterministic build/reproducibility    |
| Suitability Evaluator   | Separate model/eval update frequency           |
| Review/Approval Service | Human workflow/SoD/audit          |
| Profile Registry        | Fast Effective release resolution        |
| Drift Monitor           | Monitor Rulebook/PJ changes              |

## **23.3 Availability**

Profile Generation is a Control Plane function used when starting a business/PJ and can operate with lower availability than Runtime Task execution. Effective Profile Registry/Resolver, however, is a Production execution dependency; design HA/Cache/last-known-good according to L1 SLOs.

# **24. Nonfunctional Requirements / SLO / Observability**

| **ID**      | **Metric**                    | **Minimum standard**                                                  |
|-------------|-----------------------------|---------------------------------------------------------------|
| PROF-NFR-01 | Source traceability         | 100% revision resolution for Effective Profile Rule/Standard references         |
| PROF-NFR-02 | Human approval safety       | 0 automatic Draft→Effective approvals                                    |
| PROF-NFR-03 | Unresolved safety           | 0 Profiles becoming Effective with ERRORs or UNRESOLVED mandatory conditions           |
| PROF-NFR-04 | Deterministic compilation   | Reproduce the semantic result for the same inputs+source release+compiler |
| PROF-NFR-05 | Execution routing           | Exactly one execution_mode for every Managed Work                            |
| PROF-NFR-06 | Human-required preservation | 0 Agent substitutions for mandatory human authority                         |
| PROF-NFR-07 | Scope isolation             | 0 cross-tenant / cross-isolation violations (different `isolation_scope_ref`, including cross-project / cross-customer) |
| PROF-NFR-08 | Profile drift detection     | Changes to tracked source revisions can be detected                         |
| PROF-NFR-09 | Release reproducibility     | Any Effective Profile can be reconstructed from its Manifest                 |
| PROF-NFR-10 | Review evidence             | 100% correlation of Approve/Reject/Revise reasons with Evidence                   |

## **24.1 Observability**

Observe Generation lead time, unresolved count, rule conflicts, human-required ratio, agentic candidate ratio, approval turnaround, profile drift, rule coverage, manual overrides, and post-release incidents on the Dashboard. Do not use the Agent automation rate as the sole success KPI.

# **25. Acceptance Gates and Conformance Tests**

| **Gate**             | **Test**                        | **Pass condition**                      |
|----------------------|---------------------------------|-----------------------------------|
| GP-01 Mission        | Missing/ambiguous MissionSpec            | Generation is not considered complete when mandatory information is missing    |
| GP-02 Rule Authority | Derived/unapproved sources introduced        | 0 Effective Profile Authority violations |
| GP-03 Applicability  | Conditions/precedence/exceptions       | 0 silent selections with unresolved conflicts    |
| GP-04 Organization   | Role/Responsibility/Authority   | 0 missing mandatory responsibilities                     |
| GP-05 Lifecycle      | Phase/Gate/Criteria             | 0 omitted Gates required by standards               |
| GP-06 Work           | Mission→Work trace              | Every Work is traceable                    |
| GP-07 Suitability    | Human-required/Agentic decision      | 0 conversions of mandatory Human work to Agentic execution       |
| GP-08 Binding        | Consistency between Mode and ALE/L5/L6/L7          | Treat missing/mismatched items as ERROR           |
| GP-09 Assurance      | Quality/Review/Evidence         | 0 missing mandatory assurance          |
| GP-10 Human Approval | Draft→Effective                 | 0 Profiles becoming Effective without approval                |
| GP-11 Provenance     | source/compiler/approval/digest | 100% pinned                          |
| GP-12 Drift          | Rulebook version change         | Affected Profiles can be identified               |
| GP-13 Isolation      | Cross-isolation negative tests (different `isolation_scope_ref`, including cross-project / cross-customer) | 0 boundary violations                         |
| GP-14 Portability    | Different model/engine                  | Preserve the schema/semantics baseline     |

## **25.1 Reference Acceptance Scenario**

An external-customer system development Project is recommended as the initial reference. Use the applying organization's Project/Development/Quality/Review/Security standards as the Rulebook to generate requirements definition→design→implementation→Test→UAT→migration. Retain customer negotiations, requirements approval, Quality Gates, and Go/No-Go as Human-required, while assigning analysis, drafting, testing, and Evidence generation to Agentic/Interactive execution.

# **26. Implementation Roadmap and Backlog**

## **26.1 Recommended Roadmap**

| **Phase**          | **Objective**                         | **Artifacts**                                              |
|--------------------|----------------------------------|---------------------------------------------------------|
| P0 Schema          | Fix the Profile contract                | MissionSpec / Rule / ProfileBundle / Suitability schema |
| P1 Rulebook        | Canonicalize/structure the applying organization's existing standards | Rule Resolution + Citation + Applicability              |
| P2 Generator       | Generate SI Project Drafts            | Business/Project/Org/Lifecycle/Work Profiles            |
| P3 Suitability     | Determine human-only / interactive-agent / agentic / deterministic-system suitability    | Decision matrix + Human-required controls               |
| P4 Approval        | Human Review/Release             | Review UI / Git hosting change request / Effective Registry              |
| P5 Runtime Binding | L2-L7 integration                       | Graph/Loop/Harness/Context bindings                     |
| P6 Learning        | Drift/Outcome feedback           | Profile drift + improvement proposal                    |

## **26.2 Implementation Epics**

| **Epic** | **Name**             | **Primary artifacts**                                         |
|----------|----------------------|--------------------------------------------------------|
| PE1      | Mission & Scope      | MissionSpec / Intake API                               |
| PE2      | Rule Resolution      | L6 connector / Rule schema / precedence                |
| PE3      | Profile Model        | Business/Project/Organization/Lifecycle schemas        |
| PE4      | Work Generation      | ManagedWork decomposition / criteria                   |
| PE5      | Suitability          | Human-required / autonomy / mode evaluator             |
| PE6      | Binding              | Graph/Loop/Harness/Context/SSOT binding                |
| PE7      | Validation           | schema/conformance/conflict engine                     |
| PE8      | Human Review         | review packet / approval / diff                        |
| PE9      | Registry & Release   | ProfileBundle / manifest / effective resolver          |
| PE10     | Trace & Drift        | provenance / events / drift monitor                    |
| PE11     | Application example for a contract development Profile | company rulebook→system development project end-to-end |

# **Appendix A. Minimum Data Contracts**

| **Contract**               | **Minimum responsibilities**                                                                                                                 |
|----------------------------|------------------------------------------------------------------------------------------------------------------------------|
| MissionSpec                | mission_id / objective / owner / scope / outcomes / constraints / rulebook_roots / validity                                  |
| ResolvedRule               | rule_id / source_ref / revision / applies_when / requires / prohibits / authority / evidence / precedence / status           |
| ApplicabilityDecision      | rule_ref / target_ref / result / reason / evaluated_facts / conflict_ref                                                     |
| OrganizationProfile        | unit / role / responsibility / authority / assignment_constraint / independence                                              |
| LifecycleProfile           | phase / entry / work / artifact / gate / exit / authority                                                                    |
| ManagedWorkProfile         | work_id / purpose / owner / inputs / outputs / execution_mode / risk / autonomy / criteria / assurance / binding             |
| ExecutionSuitabilityResult | work_ref / human_required / capability / delegability / risk / reversibility / relationship / accountability / mode / reason |
| ProfileBundle              | profiles / manifest / source refs / unresolved / validation / approval status                                                |
| ProfileReleaseManifest     | bundle_digest / source releases / compiler / model refs / validation / approvals / effective window                          |
| ApprovalRecord      | review_id / reviewer / role / decision / reason / unresolved disposition / evidence / timestamp                              |

# **Appendix B. YAML Contract Examples**

These are illustrative excerpts, not complete, schema-validated Profile or suitability payloads. For actual use, resolve the applicable versioned contract, complete the required Scope and authorization context, and validate the Managed Work criteria, assurance, and binding and the suitability facts required by Appendix A. Example identifiers, decisions, and status values are not evidence of a real approval or release.

## **B.1 Draft Project Profile**

```yaml
apiVersion: alom/v1  
kind: ProjectProfile  
metadata:  
  id: project.customer-a.core-renewal  
  version: 0.1.0-draft  
  status: DRAFT  
mission_ref: mission://customer-a/core-renewal@3  
source_rule_releases:  
  - okf://company/project-standard@2026.08  
  - okf://company/development-standard@2026.08  
  - okf://company/quality-standard@2026.08  
organization_ref: org://customer-a/core-renewal@draft  
lifecycle_ref: lifecycle://system-development@draft  
governance:  
  risk_class: high  
  required_approvers: [business_owner, project_manager, quality_manager]  
profiles:  
  managed_work_root: workset://customer-a/core-renewal@draft  
validation:  
  unresolved: 2  
  errors: 0  
  review_required: true  
```

## **B.2 Execution Suitability**

```yaml
kind: ExecutionSuitabilityResult  
work_ref: work://requirements/customer-negotiation  
human_required: true  
reasons:  
  - human_relationship_essential  
  - commercial_accountability  
agent_support:  
  allowed: true  
  mode: interactive-agent  
  capabilities: [history_summary, issue_extraction, minutes_draft]  
final_authority:  
  role: project_leader  
source_rules:  
  - rule://customer-communication/12@a91f3c  
  - rule://requirement-approval/04@7f21b0  
```

## **B.3 Managed Work**

```yaml
kind: ManagedWorkProfile  
metadata: {id: work.requirements.customer-approval, version: 1.0.0-draft}  
purpose_ref: purpose://requirements-confirmation  
owner: role://project-leader  
responsibility: requirement-approval  
execution_mode: human-only  
risk_class: high  
autonomy_ceiling: A0  
inputs: [requirements-spec, review-record, issue-list]  
outputs: [approval-decision, approved-requirements-revision]  
context_profile: context://project/customer-a  
authority_ref: authority://customer-requirement-approval  
evidence_required: [meeting-record, decision-record, revision-ref]  
trace_required: true  
```

# **Appendix C. Execution Suitability Decision Matrix**

| **Work category**             | **Human-required** | **Agent assistance** | **Recommended Mode**                   | **Notes**              |
|--------------------------|--------------------|---------------|--------------------------------|-----------------------|
| Customer discussions and negotiations           | Yes, as a rule            | Yes           | human-only / interactive-agent | Trust, responsibility, and commercial decisions  |
| Customer demand/requirements approval        | Yes                | Yes           | human-only                     | External Authority         |
| Design Draft                | No                 | Yes           | interactive-agent / agentic    | Review required            |
| Technical Review assistance     | No                 | Yes           | agentic                        | Checks before Human Review  |
| Final Technical Review decision | Yes, conditionally        | Yes           | human-only / interactive-agent | Independence/responsibility           |
| Code generation                 | No                 | Yes           | agentic                        | A1/A2 + CI            |
| Unit Test                | No                 | Yes           | agentic                        | Deterministic verify  |
| Quality data analysis           | No                 | Yes           | agentic                        | Evidence generation          |
| Final quality decision             | Yes                | Yes           | human-only                     | Quality Authority     |
| Migration procedure preparation             | No                 | Yes           | interactive-agent / agentic    | Rehearsal required         |
| Production Go/No-Go      | Yes                | Yes           | human-only                     | High impact Authority |

## **C.1 Decision Pseudorules**

if legal_or_contract_requires_human: HUMAN_REQUIRED
elif external_authority_or_customer_approval: HUMAN_REQUIRED
elif relationship_or_negotiation_is_core: HUMAN_REQUIRED
elif independent_assurance_required: HUMAN_REQUIRED_OR_SEPARATE_REVIEW
else:
evaluate(agent_capability, evidenceability, risk, reversibility, data_policy)
choose(human-only \| interactive-agent \| agentic \| deterministic-system)

\# Any UNRESOLVED mandatory condition -\> REVIEW_REQUIRED, never auto-agentic

# **Appendix D. Governing Requirement and Technical Element Mapping**

## **D.1 Governing Standard Mapping**

| **Requirement in this document** | **Source**                               | **Implementation detail**                                  |
|--------------|------------------------------------------|---------------------------------------------|
| PROF-P01/P13 | S1 P-06/P-08, S5/S6                      | Authority/Scope before retrieval            |
| PROF-P02/P10 | S1/L1 Human Control, S6 Controlled Write | Draft-only + Human Approval                 |
| PROF-P05/P06 | S2 Execution Mode / Human Control        | human-only / interactive-agent / agentic / deterministic-system suitability |
| PROF-P07     | S2 ResponsibilityAssignment              | Organization/Role/Responsibility generation |
| PROF-P08     | S1 authority precedence                               | Rule precedence/conflict                    |
| PROF-P09/P14 | S2/L4 independent assurance principle          | Deterministic core + independent validation |
| PROF-P11     | S2 living operating artifact             | Drift/recompile/review/release              |
| PROF-P12     | S1 portability                           | Model/Engine non-lock-in                    |

## **D.2 Technical Element Mapping**

| **Capability**           | **Implementation candidates**                           | **Authority**              |
|--------------------------|----------------------------------------|----------------------------|
| Canonical Rulebook       | Git hosting + OKF                           | L7 Knowledge SSOT          |
| Retrieval/Context        | Knowledge API / MCP / Ontology         | L6 Derived Runtime         |
| Profile Schema           | JSON Schema / YAML / Pydantic and similar tools        | Profile repository         |
| Applicability/Precedence | Rule Engine / policy-as-code           | Rules owned by the applying organization     |
| Generation               | LLM + structured output                | Draft only                 |
| Compilation              | Deterministic compiler                 | Code owned by the applying organization      |
| Validation               | Schema + conformance + golden tests    | Independent Validator      |
| Approval                 | Git hosting change requests / Workflow / Approval Ledger | Human Authority            |
| Registry                 | Git tag/release + Profile Registry     | Approved Profile authority |
| Runtime binding          | L1 resolver + L2-L7 APIs               | Each Layer's Authority          |
| Trace                    | Trace Ledger / Evidence Store          | Organization-wide (Enterprise) trace authority |

## **D.3 Completion of This Standard**

| **v0.1 completion criteria** Validate this standard's acceptance Gates through an E2E PoC for a contract system development Project. Generate Project/Lifecycle/Organization/Managed Work/Profiles from a real organization's Rulebook, retain customer negotiations, requirements approval, quality decisions, and Go/No-Go as Human-required, and bind Agentic/Interactive Work to L2-L7. |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|

# Version Control / History

| Date | Category | Content | Document version |
| --- | --- | --- | --- |
| 2026-09-19 | normative lifecycle/security-state alignment | Retain the Profile State table and do not equate SUSPENDED with Security REVOKED. RETIRED maps to the Contract lifecycle; the absent VALIDATED state maps to the validator-gate. | Draft v0.3 |
| 2026-10-22 | meaning-preserving editorial errata | Remaining three-mode text: add deterministic-system to the §22.3 Human-required regression conditions to align with ALOM-PROF-CV-SPEC-001 §11.2 / CV-HUM-002. | Draft v0.3 |
| 2026-10-27 | normative scope-model alignment | Apply the ALOM-PROF-SCOPE-SPEC-001 Draft v0.3 scope model to §5.1 MissionSpec scope / §6.3 / §20.1 / §22.3 / §24 PROF-NFR-07 / §25 GP-13. Operating Domain (`domain_id`) is required. Organization / Customer / Project (rank 30) and UseCase / Process (rank 40) are parallel optional overlays. Each scope kind is single-valued; `project_id` is optional; `isolation_scope_ref` is required at runtime. | Draft v0.4 |

