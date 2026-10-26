# Complexity Drivers

Known sources of solution complexity to look for in RFP and tender documentation.

Each driver describes an aspect of the solution and explains what makes it troublesome.
A driver is found only when the documentation requires its troublesome side.
The same aspect in a simple form is not a driver: a standalone application on managed cloud services, or baseline security practices such as the OWASP Top 10, add no unusual complexity.
How common a requirement is does not decide it: one found in most RFPs is still a driver when it demands the troublesome side.

## Drivers

### 1. Solution Type

Identify whether the requested solution is a platform that others build on or extend, or a product intended for multiple customers, rather than a standalone application. Also identify requirements to serve several organizations from one deployment, such as multi-tenancy or per-organization configuration. Platforms and products may require extensibility, backward compatibility, and minimal impact of changes on existing consumers, while serving several organizations requires isolating their data and configuration. When future consumers, extensions, or customer-specific needs are not known at bid time, the architecture is harder to define and the effort harder to estimate. This increases architectural complexity, design effort, and the risks of costly rework.

### 2. Operational Infrastructure

Identify on-premises, hybrid, or IaaS hosting, and constraints on infrastructure and permitted deployment technologies. Also identify the operational infrastructure the solution needs beyond production hosting, such as non-production environments, deployment pipelines, the software supply chain, or monitoring. Managed cloud services reduce infrastructure and operational effort, while every part that must be built from scratch or under restrictive constraints adds to it. This increases implementation effort, operational effort, and delivery risks.

### 3. Service Levels

Identify explicit service-level commitments for production, such as measurable targets for availability, performance, scalability, or recovery, and obligations to operate and support the solution, such as 24/7 operations or incident resolution times. Meeting them may demand specific architectural patterns, infrastructure redundancy, resilience mechanisms, testing practices, continuous monitoring, and operational processes and staff. Strict targets are especially hard to meet when the solution is new and has no operational history. This increases solution complexity, operational effort, and the risks of failing to meet service commitments.

### 4. External Integrations

Identify third-party services, enterprise systems, and legacy systems that the solution must integrate with, including the availability and maturity of their interfaces. Also identify interface standards the integrations must conform to, such as Peppol, ISO 20022, or HL7. Integrations introduce additional implementation, testing, mocking, and operational dependencies. Undocumented, legacy, or business-critical integrations may require specialized approaches, and interface standards add conformance testing and often certification. This increases implementation complexity, testing effort, and delivery risks.

### 5. User Interfaces

Identify mobile client applications and the number of client platforms the solution must support, such as web, iOS, Android, or desktop. Also identify explicit accessibility, usability, and localization requirements for its user interfaces, such as WCAG conformance or support for several languages and writing systems. Multiple client platforms may require different technology stacks, API design considerations, distribution mechanisms, compatibility strategies, and platform-specific user experiences. Accessibility, usability, and localization requirements add specialized design, testing, and often conformance audits on every platform. This increases development complexity, testing effort, and maintenance risks.

### 6. Developer Interfaces

Identify whether the solution must expose public interfaces or provide tools for external developers and consumers, such as API contracts, SDKs, CLIs, or MCP servers. Also identify interface standards they must conform to, such as FHIR, Open Banking, or open data standards. Public interfaces may require governance from the beginning, including security, versioning, documentation, backward compatibility, and lifecycle management, while interface standards add conformance testing and often certification. This increases architectural complexity and long-term maintenance risks.

### 7. Security Controls

Identify mandatory security and data protection frameworks, standards, and regulations applicable to the solution, such as NIST, ISO 27001, or government and industry standards. Also identify specific security controls the solution must implement or integrate with, such as access control, cryptography, audit trails, or security monitoring. Obligations that prescribe controls in detail, require integration with the customer's security infrastructure, or must be evidenced through audits or certification demand specialized expertise, prescribed development methodologies, documentation, and verification practices. This increases architectural complexity, implementation effort, and compliance risks.

### 8. Data Migration

Identify dependencies on existing data sources and requirements to migrate, consolidate, transform, correlate, deduplicate, or enrich legacy data. Migration may require detailed data analysis, mapping, cleansing, validation, reconciliation, and transition strategies to preserve data integrity and business continuity. This increases implementation complexity and delivery risks, especially with uncertain data quality and legacy dependencies.

## Risk Levels

Only the troublesome side of an aspect is a driver, so every driver found is a source of complexity and the lowest level is **High**. There are no Low or Medium levels.

- **High** — The driver adds effort and uncertainty, but does not jeopardize delivery. State any aggravating factors in the findings: broad or open-ended scope, several instances at once (such as many integrations or many client platforms), strict measurable targets, or a need for specialized expertise.
- **Critical** — The driver may jeopardize delivery or the bid itself: requirements that are mandatory and contractually enforced (such as penalties or certification before go-live), dependencies that are undocumented, unavailable, or outside the bidder's control, or requirements that cannot all be met under the constraints in the documentation.

When in doubt between High and Critical, choose Critical and state the uncertainty in the driver's summary.

## Overall Risk

The overall risk is a verdict on how the drivers found combine, not the highest level among them: several drivers together may be harder than each one alone.
The verdict is based on the documentation as it stands, not on the bidder's capacity or on what a clarification could change.

- **Predictable** — No drivers, or only High drivers that are bounded and largely independent. A regular bid process can absorb them.
- **Challenging** — High drivers that are open-ended or aggravate each other (such as on-premises hosting with strict availability targets and many legacy integrations), or Critical drivers whose extent the documents define in full, such as penalties or certification before go-live. The bid needs attention to them.
- **Uncertain** — Critical drivers whose extent the documents leave open, such as dependencies that are undocumented, unavailable, or outside the bidder's control, or gaps and contradictions in what is required. Due diligence is needed before committing to bid.
- **Unrealistic** — Critical drivers with requirements that cannot all be met, or so many Critical drivers that delivery as specified looks infeasible.

When in doubt between two verdicts, choose the more severe one and state the uncertainty in the Executive Summary.
