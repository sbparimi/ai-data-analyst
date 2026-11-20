# Initial Domain/Data Model

This is a conceptual model, not a migration specification. Codex must refine it with an ERD and ADR before implementation.

## Entities

- User
- Workspace
- WorkspaceMembership (role)
- Project
- SourceArtifact (immutable uploaded object metadata)
- Dataset (logical dataset)
- DatasetVersion (parsed snapshot/schema/version)
- IngestionJob
- ProfileRun
- ColumnProfile
- DataQualityFinding
- MetricDefinition
- AnalysisRun
- AnalysisOperation
- EvidenceRecord
- Insight
- Investigation
- Conversation
- ConversationTurn
- Dashboard
- DashboardWidget
- Report
- ExportJob
- AuditEvent
- UsageRecord

## Required common fields

Where applicable:
- id (non-guessable public identifier)
- workspace_id
- created_at / updated_at
- created_by
- status
- version
- deleted_at or retention state, if soft deletion is approved

## Provenance relationships

- DatasetVersion -> SourceArtifact
- ProfileRun -> DatasetVersion
- AnalysisRun -> DatasetVersion and ProfileRun
- AnalysisOperation -> AnalysisRun
- EvidenceRecord -> AnalysisOperation and source references
- Insight -> EvidenceRecord(s)
- Investigation -> Insight and AnalysisRun
- DashboardWidget -> validated result/evidence reference
- Report -> AnalysisRun, DatasetVersion and rendered assets

## Invariants

- A source artifact is immutable.
- Derived versions are explicit and traceable.
- A result cannot reference an unowned dataset version.
- Evidence is versioned and immutable after run completion.
- Tenant ownership is checked across every relationship.
- Deletion and retention semantics must be designed before production.
