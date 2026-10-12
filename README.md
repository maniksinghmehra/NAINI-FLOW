# NAINI-FLOW

**Predictive Traffic Management and Parking Reservation System**

NAINI-FLOW is a traffic-management platform designed to coordinate vehicle arrivals, parking reservations, digital entry validation, and traffic analysis through a unified software system.

The project focuses on predictive demand management rather than relying exclusively on reactive congestion control. By coordinating arrival windows with road and parking capacity, the system aims to support more efficient traffic flow and evidence-based transportation planning.

## Objectives

- Distribute vehicle arrivals across configurable time windows.
- Coordinate parking reservations with available capacity.
- Provide digital entry passes with QR-based validation.
- Support traffic administrators through operational dashboards.
- Monitor traffic demand, parking occupancy, and reported incidents.
- Analyse congestion, travel delays, and environmental impacts.
- Evaluate traffic-management interventions using simulation.
- Establish a shared data architecture for operational interfaces and analytical workflows.

## System Modules

### 1. Visitor Portal

The visitor portal provides the interface for trip planning and access management.

Planned capabilities include:

- Trip planning and arrival-window selection.
- Parking discovery and reservation.
- Digital QR e-Pass generation.
- Transport and shuttle options.
- Booking status and pass information.
- Relevant traffic conditions and incident notifications.

### 2. Traffic Administration Portal

The administration portal is intended to support traffic monitoring, planning, and operational decision-making.

Planned capabilities include:

- Traffic and parking overview dashboards.
- Vehicle-arrival forecasts.
- Configurable arrival quotas.
- Traffic distribution across entry routes.
- Parking capacity and occupancy monitoring.
- Incident reporting and status management.
- Operational statistics and historical trends.

### 3. Scanner Portal

The scanner portal provides an interface for validating entry passes at designated access points.

Planned capabilities include:

- QR e-Pass scanning and validation.
- Single-use pass redemption.
- Booking and entry-record lookup.
- Duplicate-use prevention.
- Scan-status and connectivity monitoring.
- Offline scan queuing where operationally appropriate.

Pass validity and redemption must be enforced by the backend rather than relying solely on client-side checks.

### 4. Traffic Analytics

The analytics module is intended to convert validated traffic observations into useful operational and research outputs.

Planned capabilities include:

- Vehicle-count analysis.
- Traffic-demand estimation.
- Congestion and queue-length analysis.
- Parking occupancy and turnover analysis.
- Travel-delay and time-loss estimation.
- Traffic trend analysis.
- Environmental-impact estimation.
- Comparisons between baseline conditions and proposed interventions.

## Technical Architecture

NAINI-FLOW is designed around separate user interfaces, a shared application backend, and an independent traffic-analysis pipeline.

### Frontend

| Technology | Purpose |
|---|---|
| React | Component-based user interfaces |
| TypeScript | Type safety and maintainability |
| Vite | Development server and production build tooling |
| Tailwind CSS | Interface styling |
| Lucide React | Interface icons |
| React Router | Client-side navigation |

### Backend and Database

The planned backend architecture uses Supabase and PostgreSQL to manage shared application data.

The backend is intended to support:

- Authentication and session management.
- User roles and access control.
- Booking and reservation records.
- Parking inventory and occupancy records.
- Digital pass lifecycle management.
- Entry-validation records.
- Incident and operational data.

Database policies and server-side validation must enforce permissions and protect application data.

### Traffic Simulation

The proposed simulation workflow uses SUMO-compatible data processing and SimTraM for mixed-traffic modelling.

The pipeline consists of:

1. Collecting and validating traffic-demand data.
2. Preparing origin–destination demand datasets.
3. Converting datasets into compatible input formats.
4. Generating vehicle trips and routes.
5. Running traffic scenarios.
6. Comparing simulation outputs across interventions.

Potential scenarios include arrival-window restrictions, heavy-vehicle timing controls, reduced road capacity, and road-closure events.

Simulation results are estimates generated from a model. They must remain distinguishable from observed traffic measurements and live operational data.

## Data Collection and Processing

The project may use multiple sources to estimate and analyse traffic demand.

Potential inputs include:

- Manual vehicle counts.
- Roadside observations.
- Queue-length measurements.
- Parking capacity and occupancy records.
- Booking and entry-validation records.
- Origin–destination demand estimates.
- Authorised traffic-monitoring data.
- Incident and road-condition reports.

Where direct traffic counts are unavailable, queue-length and parking-occupancy methods can provide estimates. Their assumptions, limitations, and validation methods should be documented.

Data-processing workflows should preserve source information, timestamps, vehicle categories, and measurement methods wherever available.

## Development Roadmap

### Phase 1 — Core Platform

- [ ] Establish the application architecture and shared navigation.
- [ ] Develop the visitor, administration, and scanner interfaces.
- [ ] Define core data models and application workflows.
- [ ] Establish reusable interface components and consistent design patterns.

### Phase 2 — Booking and Access Management

- [ ] Implement arrival-window reservations and parking allocation.
- [ ] Develop digital e-Pass generation and validation.
- [ ] Establish booking lifecycle management.
- [ ] Implement backend-enforced access controls and duplicate-use prevention.

### Phase 3 — Traffic Intelligence

- [ ] Develop traffic monitoring and demand forecasting.
- [ ] Integrate vehicle-count and parking-occupancy data.
- [ ] Implement incident reporting and operational dashboards.
- [ ] Establish route-level traffic summaries and historical analysis.

### Phase 4 — Analytics and Simulation

- [ ] Develop traffic-demand and congestion analysis.
- [ ] Establish the SUMO-compatible data-processing pipeline.
- [ ] Evaluate traffic interventions using SimTraM.
- [ ] Analyse travel delays, queue lengths, and estimated emissions.
- [ ] Compare baseline and intervention scenarios.

### Phase 5 — Integration and Validation

- [ ] Integrate the application with the backend and verified data sources.
- [ ] Validate database integrity and authorisation policies.
- [ ] Test booking, pass validation, and incident-management workflows.
- [ ] Evaluate operational reliability and deployment readiness.
- [ ] Document known limitations and remaining requirements.

Progress should reflect actual implementation and testing. Mark a task complete only when its requirements have been met and validated.

## Development Setup

### Prerequisites

- Node.js version supported by the installed Vite release.
- npm.
- Git.
- A code editor such as Visual Studio Code.

### Installation

Clone the repository:

```bash
git clone https://github.com/YOUR_USERNAME/NAINI-FLOW.git
cd NAINI-FLOW
```

Install project dependencies:

```bash
npm install
```

Start the development server:

```bash
npm run dev
```

Open the local URL displayed in the terminal.

### Production Build

Generate a production build:

```bash
npm run build
```

Preview the production build locally:

```bash
npm run preview
```

Run the configured lint checks:

```bash
npm run lint
```

## Project Structure

The following structure describes the intended organisation of the application as development progresses.

```text
NAINI-FLOW/
├── public/
├── src/
│   ├── assets/
│   ├── components/
│   ├── layouts/
│   ├── pages/
│   │   ├── Overview/
│   │   ├── Traffic/
│   │   ├── Parking/
│   │   ├── Bookings/
│   │   ├── Analytics/
│   │   └── Incidents/
│   ├── services/
│   ├── types/
│   ├── App.tsx
│   ├── index.css
│   └── main.tsx
├── .gitignore
├── package.json
├── package-lock.json
├── tsconfig.json
├── vite.config.ts
└── README.md
```

The actual directory structure may evolve as modules are implemented.

## Security and Data Integrity

The application should follow these principles:

- Enforce access permissions at the backend and database layers.
- Keep privileged credentials out of source control.
- Store sensitive configuration in environment variables.
- Validate reservation and pass state on the server.
- Prevent duplicate redemption of single-use passes.
- Restrict operational and surveillance data to authorised users.
- Apply appropriate data-retention and access policies.
- Clearly distinguish observed data, estimated values, and simulation outputs.
- Avoid exposing personal or sensitive information through public interfaces.

## Development Principles

- Maintain modular, readable, and type-safe code.
- Separate interface components from data-access logic.
- Use reusable components and consistent application patterns.
- Document data models, assumptions, and integration contracts.
- Validate external data before using it in analysis.
- Test critical workflows and error conditions.
- Keep demonstration data clearly identified.
- Avoid presenting planned integrations as operational capabilities.
- Preserve a clear separation between operational services and research simulations.

## Project Vision

NAINI-FLOW aims to bring predictive arrival management, parking coordination, digital entry validation, and traffic-impact analysis into one extensible platform.

Its long-term goal is to support more effective traffic operations and evidence-based transportation planning through validated data, reproducible simulation, and measurable evaluation of proposed interventions.