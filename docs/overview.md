# Construction Project Management System

A modern enterprise workspace for a multinational construction company to manage project delivery, task execution, document metadata, and approval decisions in one place.

## Users

- Admins oversee system data and governance.
- Project Managers track project status, progress, tasks, and document submissions.
- Employees complete assigned construction tasks and submit design/document work.
- Approvers review submitted documents and record approval decisions.

## Design direction

The app uses a professional Microsoft/Fluent-inspired design with a white and light gray workspace, dark navy header/navigation, royal blue accents, subtle shadows, rounded cards, compact data tables, and responsive desktop-first layouts.

## Data approach

The app uses Dataverse-backed tables for CTS Project, CTS Task, CTS Document, CTS Document Approval, and System User access records. KPI cards, grids, and forms are aligned to the generated Dataverse table columns, with people assignment fields using the System User table and Dataverse User lookup values.