# ALOM-PROFILE-TEMPLATE-003

Repository-native generalized Profile template for `ALOM-PROF-SCOPE-SPEC-001`.

- Version: v0.2
- Date: 2026-10-29
- Status: managed template
- Purpose: represent both permanent operating functions and temporary project work without synthesizing a Project.

## Structure

```text
bundle.yaml
scope.yaml
profiles/operating-domain.yaml
profiles/organization.yaml
profiles/customer.yaml
profiles/project.yaml
profiles/lifecycle.yaml
profiles/process.yaml
profiles/managed-work.yaml
profiles/execution.yaml
profiles/governance.yaml
profiles/context.yaml
profiles/assurance.yaml
```

`profiles/project.yaml` and `profiles/customer.yaml` are optional overlays. `profiles/organization.yaml` is an independent responsibility/authority overlay and is not a child of Project.

Runtime consumers resolve `scope.yaml` to `CommonScopeContract v1`; `isolation_scope_ref` is the canonical isolation boundary. A missing `project_id` is valid.
