# Overview
KOKORO is a comprehensive disaster response application that manages shelters, volunteers, emergency communications, and situational awareness through the ServiceNow platform. The system combines a Service Portal front-end with a robust back-end data model to support both registered users and guest access during emergencies.

The name KOKORO（こころ） means "heart" in Japanese — reflecting the project's mission to connect communities in times of crisis.

## Architecture
### Platform Stack

| Layer | Technology |
| :--- | :--- |
| **Back-end** | ServiceNow (Orlando+) — Custom Application Scope |
| **Service Portal** | AngularJS (ServiceNow SP Framework) |
| **Front-end (EOC)** | React 18 + TypeScript, deployed on Vercel |
| **GIS** | Mapbox GL JS |
| **State Management** | Zustand (EOC), AngularJS Services (SP) |
| **Server State** | TanStack Query (EOC) |

### Service Portal — Router Architecture v3
The Service Portal uses a modular three-widget router pattern:

```text
kokoro_router (Master Router)
├── kokoro_user (User Dashboard)
│     ├── Profile Settings Panel
│     ├── Daily Reminder Toggle
│     └── Onboarding Tour
└── kokoro_user_disaster (Disaster Operations)
      ├── Volunteer Registration
      ├── Shelter Status Board
      └── Emergency Messaging
Emergency Operations Center (EOC)A standalone React/TypeScript application providing real-time tactical awareness:Incident Map — Mapbox GL with priority-coded markersWeather Panel — Live weather integrationIncident Detail Modal — Full incident drill-downPriority Dashboard — Filterable by severityCustom TablesTablePurposesilent_wishAnonymous support requestsheartbeatUser activity / wellness check-inuser_profileExtended user profilesemergency_messageBroadcast emergency communicationsguest_token72-hour guest access tokensprocess_eventWorkflow state machine eventsfriend_relationSocial connection graphfriend_notificationFriend activity alertsKey FeaturesVolunteer Management (CAD System)Bloomberg Terminal / Palantir Gotham-inspired tactical UIKanban Board — 4-column drag-and-drop workflow: ASSIGNED → IN_PROGRESS → ON_HOLD → COMPLETEDHeartbeat Monitor — Real-time volunteer status trackingCOMMS Module — Broadcast messaging to field teamsSITREP Panel — Situational reports sidebarOffline Queue — Queued operations for connectivity loss (V9)Accessibility & SecurityWCAG 2.1 AA compliant (V8)Unified input validation layer (V3)Rate limiting & security hardeningRole-based access controlGuest Access72-hour emergency guest tokensNo-registration shelter lookupDesigned for crisis scenarios where login is impracticalSource ControlThis repository is connected to a ServiceNow Personal Developer Instance (PDI) via ServiceNow Source Control.Instance: https://www.google.com/search?q=dev269536.service-now.comApp Scope: x_1821654_kokoro_0_*Repository StructurePlaintext/
├── 80ba4d9538363210f6b1fb96feaa.../   # ServiceNow app metadata
│   └── sn_source_control.properties    # Source control config
└── README.md
Note: ServiceNow application files (Business Rules, Script Includes, UI Policies, Client Scripts, etc.) are managed through the platform's source control integration and will appear as commits from the connected PDI.Related RepositoriesRepositoryDescriptionkokoro-shelter-app-ServiceNow-(this repo) ServiceNow back-end applicationKOKORO EOC (React)Emergency Operations Center front-endCertifications & ContextThis project was developed as part of a 12-week ServiceNow portfolio initiative by a developer holding:✅ CSA — Certified System Administrator✅ CAD — Certified Application Developer✅ CIS-ITSM — Certified Implementation Specialist, IT Service Management✅ CIS-RC — Certified Implementation Specialist, Risk and ComplianceSetup & DevelopmentPrerequisitesServiceNow PDI (Personal Developer Instance)ServiceNow Studio or VS Code with SN ExtensionGetting StartedFork this repositoryConnect your PDI to the forked repo via Source Control in ServiceNow StudioImport the application into your instanceConfigure the custom tables and Service Portal pagesFor the EOC (React Front-end)Bash# Separate repository — clone and install
npm install
npm run dev
