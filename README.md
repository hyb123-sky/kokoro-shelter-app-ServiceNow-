Overview
KOKORO is a comprehensive disaster response application that manages shelters, volunteers, emergency communications, and situational awareness through the ServiceNow platform. The system combines a Service Portal front-end with a robust back-end data model to support both registered users and guest access during emergencies.
The name KOKORO（こころ） means "heart" in Japanese — reflecting the project's mission to connect communities in times of crisis.

Architecture
Platform Stack
LayerTechnologyBack-endServiceNow (Orlando+) — Custom Application ScopeService PortalAngularJS (ServiceNow SP Framework)Front-end (EOC)React 18 + TypeScript, deployed on VercelGISMapbox GL JSState ManagementZustand (EOC), AngularJS Services (SP)Server StateTanStack Query (EOC)
Service Portal — Router Architecture v3
The Service Portal uses a modular three-widget router pattern:
kokoro_router (Master Router)
  ├── kokoro_user (User Dashboard)
  │     ├── Profile Settings Panel
  │     ├── Daily Reminder Toggle
  │     └── Onboarding Tour
  └── kokoro_user_disaster (Disaster Operations)
        ├── Volunteer Registration
        ├── Shelter Status Board
        └── Emergency Messaging
Emergency Operations Center (EOC)
A standalone React/TypeScript application providing real-time tactical awareness:

Incident Map — Mapbox GL with priority-coded markers
Weather Panel — Live weather integration
Incident Detail Modal — Full incident drill-down
Priority Dashboard — Filterable by severity

Custom Tables
TablePurposesilent_wishAnonymous support requestsheartbeatUser activity / wellness check-inuser_profileExtended user profilesemergency_messageBroadcast emergency communicationsguest_token72-hour guest access tokensprocess_eventWorkflow state machine eventsfriend_relationSocial connection graphfriend_notificationFriend activity alerts

Key Features
Volunteer Management (CAD System)

Bloomberg Terminal / Palantir Gotham-inspired tactical UI
Kanban Board — 4-column drag-and-drop workflow: ASSIGNED → IN_PROGRESS → ON_HOLD → COMPLETED
Heartbeat Monitor — Real-time volunteer status tracking
COMMS Module — Broadcast messaging to field teams
SITREP Panel — Situational reports sidebar
Offline Queue — Queued operations for connectivity loss (V9)

Accessibility & Security

WCAG 2.1 AA compliant (V8)
Unified input validation layer (V3)
Rate limiting & security hardening
Role-based access control

Guest Access

72-hour emergency guest tokens
No-registration shelter lookup
Designed for crisis scenarios where login is impractical


Source Control
This repository is connected to a ServiceNow Personal Developer Instance (PDI) via ServiceNow Source Control.
Instance: dev269536.service-now.com
App Scope: x_1821654_kokoro_0_*
Repository Structure
/
├── 80ba4d9538363210f6b1fb96feaa.../   # ServiceNow app metadata
│   └── sn_source_control.properties    # Source control config
└── README.md

Note: ServiceNow application files (Business Rules, Script Includes, UI Policies, Client Scripts, etc.) are managed through the platform's source control integration and will appear as commits from the connected PDI.


Related Repositories
RepositoryDescriptionkokoro-shelter-app-ServiceNow- (this repo)ServiceNow back-end applicationKOKORO EOC (React)Emergency Operations Center front-end

Certifications & Context
This project was developed as part of a 12-week ServiceNow portfolio initiative by a developer holding:

✅ CSA — Certified System Administrator
✅ CAD — Certified Application Developer
✅ CIS-ITSM — Certified Implementation Specialist, IT Service Management
✅ CIS-RC — Certified Implementation Specialist, Risk and Compliance


Setup & Development
Prerequisites

ServiceNow PDI (Personal Developer Instance)
ServiceNow Studio or VS Code with SN Extension

Getting Started

Fork this repository
Connect your PDI to the forked repo via Source Control in ServiceNow Studio
Import the application into your instance
Configure the custom tables and Service Portal pages

For the EOC (React Front-end)
bash# Separate repository — clone and install
npm install
npm run dev
