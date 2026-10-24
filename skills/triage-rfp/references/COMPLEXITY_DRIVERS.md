# Complexity Drivers

Known sources of solution complexity to look for in RFP and tender documentation.

Each driver describes an aspect of the solution and explains what makes it troublesome.
A driver is found only when the documentation requires its troublesome side.
The same aspect in a simple form is not a driver: a standalone application on managed cloud services, or baseline security practices such as the OWASP Top 10, add no unusual complexity.

## Drivers

### 1. System Class

Determine whether the requested solution is an extensible platform or a product rather than a standalone application. Platforms and products introduce higher architectural complexity because they must support future extensions, maintain backward compatibility, and minimize the impact of changes on existing applications and consumers. These expectations increase solution complexity and associated risks.

### 2. Target Environment

Identify on-premises, hybrid, or IaaS hosting, and constraints on infrastructure and permitted deployment technologies. Cloud-native solutions using managed PaaS or SaaS services reduce infrastructure complexity and operational effort, while on-premises, hybrid, or restrictive environments require additional architecture, deployment, and maintenance practices. These constraints increase implementation effort and delivery risks.

### 3. Client Applications

Identify mobile client applications and the number of client platforms the solution must support, such as web, iOS, Android, or desktop. Multiple client platforms may require different technology stacks, API design considerations, distribution mechanisms, compatibility strategies, and platform-specific user experiences. This increases development complexity and maintenance risks.

### 4. Public APIs

Identify whether the solution must expose public interfaces or provide tools for external developers and consumers, such as API contracts, SDKs, CLIs, or MCP servers. Public interfaces require governance from the beginning, including security, versioning, documentation, backward compatibility, and lifecycle management. These obligations increase architectural complexity and long-term maintenance risks.

### 5. External Integrations

Identify third-party services, enterprise systems, and legacy systems that the solution must integrate with, including the availability and maturity of their interfaces. Integrations introduce additional implementation, testing, mocking, and operational dependencies, while undocumented, legacy, or business-critical integrations may require specialized approaches. These dependencies increase complexity and delivery risks.

### 6. Service Level (NFRs)

Identify explicit service-level commitments and measurable targets for availability, performance, scalability, or reliability, such as 99.9% availability, response-time limits, throughput, or recovery objectives. Meeting these requirements may demand specific architectural patterns, infrastructure redundancy, resilience mechanisms, testing practices, and continuous monitoring. These obligations increase solution complexity and the risks of failing to meet service commitments.

### 7. Security Frameworks

Identify mandatory security frameworks, regulatory standards, and compliance requirements applicable to the solution, such as NIST, ISO 27001, or government and industry standards. Adherence to these frameworks may require specialized expertise, prescribed security controls, development methodologies, documentation, and verification practices. These obligations introduce additional architectural constraints, implementation effort, and compliance risks.

### 8. Data Migration

Identify dependencies on existing data sources and requirements to migrate, consolidate, transform, correlate, deduplicate, or enrich legacy data. Migration may require detailed data analysis, mapping, cleansing, validation, reconciliation, and transition strategies to preserve data integrity and business continuity. Uncertain data quality and legacy dependencies increase implementation complexity and delivery risks.

## Risk Levels

Only the troublesome side of an aspect is a driver, so every driver found is a source of complexity and the lowest level is **High**. There are no Low or Medium levels.

- **High** — The driver adds effort and uncertainty, but does not jeopardize delivery. State any aggravating factors in the findings: broad or open-ended scope, several instances at once (e.g. many integrations, many client platforms), strict measurable targets, or a need for specialized expertise.
- **Critical** — The driver may jeopardize delivery or the bid itself: requirements that are mandatory and contractually enforced (penalties, certification before go-live), dependencies that are undocumented, unavailable, or outside the bidder's control, or requirements that conflict with each other or with other constraints in the documentation.

When in doubt between High and Critical, state the uncertainty in the finding.

## Overall Risk

The overall risk is a verdict on how the drivers found combine, not the highest level among them: several drivers together may be harder than each one alone.
The verdict is based on the documentation only, not on the bidder's capacity.

- **Predictable** — No drivers, or only High drivers that are bounded and largely independent. A regular bid process can absorb them.
- **Challenging** — Several High drivers that aggravate each other (e.g. on-premises hosting with strict availability targets and many legacy integrations), or a single Critical driver that a clarification question may resolve. The bid needs attention to them.
- **Uncertain** — Critical drivers that clarification is unlikely to resolve, such as dependencies outside the bidder's control, or undocumented systems. Due diligence is needed before committing to bid.
- **Unrealistic** — Critical drivers that conflict with each other or with other constraints in the documentation, or so many of them that delivery as specified looks infeasible.

When in doubt between two verdicts, choose the more severe one and state the uncertainty in the Executive Summary.
