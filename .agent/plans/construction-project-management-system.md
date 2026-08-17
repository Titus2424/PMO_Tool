# Construction Project Management System

## Goal
Build a modern enterprise construction project management system for a multinational construction company, using a professional Microsoft/Fluent-inspired visual language.

## Design direction
- White and light gray workspace with a dark navy header/navigation shell.
- Royal blue primary accent for primary actions, active navigation, and progress indicators.
- Subtle shadows, rounded enterprise cards, compact tables, and professional system typography.
- Responsive desktop-first layout with no gaming, futuristic, or decorative styling.

## App structure
- Single unified React app with eight screens and shared navigation.
- Header and navigation remain consistent across all screens.
- Top navigation is used for the requested eight destinations in a compact enterprise shell.

## Screens
- Dashboard: KPI cards for Total Projects 28, Active Tasks 125, Pending Approval 12, active project progress, and pending approval documents.
- Projects: searchable project list with Add Project action, project manager, status, and progress.
- Project Workspace: project overview with manager, status, progress, task/document/approval/team statistics, and tabs for Tasks, Documents, Approvals, and Team.
- Tasks: project selector, Create Task action, and Kanban board with To Do, In Progress, Submitted, and Approved columns.
- My Tasks: employee-focused assigned task list with due date, status, Upload Design, and Submit actions.
- Documents: searchable document table with Upload Document action and document metadata.
- Upload Document: upload form for project, task, file, version, and comments.
- Approval Center: pending documents table with approval comments, Approve, and Reject actions.

## Reusable components
- Header
- Navigation
- KPI cards
- Project cards
- Status badges
- Progress bars
- Tables
- Modal dialogs
- Buttons
- Forms

## Data entities
- cts_projects: master project information with project code, location, schedule, status, and progress; Project Manager uses a Dataverse System User lookup.
- cts_tasks: project task records with assignment, priority, status, and due date; Assigned To uses a Dataverse System User lookup.
- cts_documents: document metadata only; actual files are stored in SharePoint and referenced by URL/File ID; Uploaded By uses a Dataverse System User lookup.
- cts_documentapprovals: approval history for submitted documents; Approver uses a Dataverse System User lookup.

## Relationships
- Projects have many Tasks.
- Projects have many Documents.
- Tasks have many Documents.
- Documents have many Document Approvals.
- User-related fields reference the Dataverse System User table instead of custom user records.

## Roles
- Admin
- Project Manager
- Employee
- Approver

## Data source decision
- Use only four app-owned Dataverse-style tables: cts_projects, cts_tasks, cts_documents, and cts_documentapprovals.
- Do not create Users or Roles tables; use Dataverse System User lookups for all people/user columns and Entra ID Groups or Dataverse Security Roles for role assignment.
- Optimize the model to use Dataverse system tables wherever appropriate, especially for owner, created by, modified by, user assignment, approver, uploader, and project manager references.
- Store document metadata in Dataverse-style data and keep actual files in SharePoint via Document URL and SharePoint File ID.

## Key behavior
- Add Project, Create Task, Upload Document, Submit, Approve, and Reject controls should have working in-app handlers and feedback.
- Search and filters should update the visible data on relevant screens.
- Forms should use enterprise-friendly validation and controlled inputs.
- Current-user personalization can be used where helpful for My Tasks and submitted-by context.