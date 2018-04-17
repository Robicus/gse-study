# Security Policy and Business Issues

## Exam Outcome

Demonstrate an understanding of the security policy and business issues including continuity planning.

Reference: 401.2, Module 8

## Security Policy

### Policy Framework

- Why an Organization Needs a Security Policy

Security policies protect organizations, their people, and information. The policy establishes what must be done to protect information stored on computers.

- Mission Statement

The mission statement should focus on the reason the organization exists. It can serve as a refocusing tool during crisis. It's the idea behind the brand.

- Policies vs. Procedures

Policies: Address the who, what, and why; a directive that indicates a conscious decision to follow a path toward a specified objective.
Procedures: Address the how, where, and when; detailed steps to be followed by users, system operations personnel, and others to accomplish a specific task.

Standard: organizational and specifics uniform use of specific technologies; usually refers to specific hardware and software.
Baseline: a more specific implementation of a standard. Gets into more specific technical details of how a system should be configured.

#### Policy Tables of Contents

- Purpose
- Related documents or references
- Cancellation or expiration
- Background
- Scope
- Policy statement
- Responsibility
- Action

## Contingency Planning

### Business Continuity Planning

The business continuity plan (BCP) is a strategic plan of focusing on the avilability of critical business processes.  It includes disaster recovery and business resumption planning.

Business Impact Analysis (BIA) helps determine the maximum tolerable downtime (MTD) for any given system, i.e., how long can your system be compromised? BIA is useful for developing DRP.

### BCP-DRP Planning Process Lifcycle:

1. Project Intiation
2. Risk Analysis
3. Business Impact Analysis
4. Build the Plan
5. Test and Validate the Plan
6. Modify and Update the Plan
7. Approve and Implement the Plan

#### Business Continuity and Disaster Recovery Planning Model
|-------------------------------------------|-------------------------------|
| 1. Business Continuity                    |                               |
| 1. Policies and Strategies                |   Business Continuity Plan    |
| 1. Risk Management                        |                               |
| 2. Busness Continuity Planning            |                               |
|-------------------------------------------|-------------------------------|
| 2. Valication and Testing                 |                               |
| 2. Information Technology Recovery Process|                               |
| 3. Alternative Site                       |       Disaster Recovery       |
| 3. Data Backup and Offsite Replication    |                               |
| 3. Servers Storage Network                |                               |
|-------------------------------------------|-------------------------------|

1. Infrastructure Layer
2. Management Layer
3. Policy Layer

### Course of Action Matrix
/--------------|------------------|------------------|----------------|----------------|--------------|-------------------\
|    PHASE     |      DETECT      |       DENY       |    DISRUPT     |    DEGRADE     |   DECEIVE    |      DESTROY      |
|--------------|------------------|------------------|----------------|----------------|--------------|-------------------|
|              |                  |                  |                |                |              |                   |
|              | IDS/IPS          | IPS              | IPS            | IPS            | HoneyPots    |                   |
| RECON        | Firewall L7      | Firewalls        | Proxy          | Proxy          | Proxy        | N/A               |
|              | Proxy            | ACLs             | Firewall L7    | Firewall L7    | Redirections |                   |
|              | System Logs      |                  |                |                |              |                   |
|--------------|------------------|------------------|----------------|----------------|--------------|-------------------|
|              | IPS/IDS          | IPS              |                |                |              |                   |
|              | Firewall L7      | Firewalls        | IPS            | IPS            | HoneyPots    | IPS               |
| DELIVERY     | Proxy            | Email Protection | Firewall L7    | Firewall L7    | Proxy        | Email Protections |
|              | Perceptive User  | AV               | Endpoint Suite | Endpoint Suite | Redirections | Endpoint Suite    |
|              | Endpoint Suite   | ACLs             |                |                |              |                   |
|--------------|------------------|------------------|----------------|----------------|--------------|-------------------|
|              | IDS/IPS          | IPS              |                |                |              |                   |
|              | Firewalls        | Firewalls        | IPS            | IPS            | HoneyPots    | IPS               |
| EXPLOITATION | Email Protection | Email Protection | Firewalls L7   | Firewalls L7   | Proxy        | Email Protection  |
|              | Endpoint Suite   | Endpoint Suite   | Endpoint Suite | Endpoint Suite | Redirections | System Logs       |
|              | AV               | AV               |                |                |              | Endpoint Suite    |
|--------------|------------------|------------------|----------------|----------------|--------------|-------------------|
|              |                  |                  |                |                |              |                   |
|              | IDS/IPS          | IPS              | IPS            | IPS            |              | IPS               |
| INSTALLATION | System Logs      | DEP              | DEP            | DEP            | HoneyPots    | Proxy             |
|              | Endpoint Suite   | Endpoint Suite   | Endpoint Suite | Endpoint Suite |              | Endpoint Suite    |
|              | AV               | AV               |                |                |              |                   |
|--------------|------------------|------------------|----------------|----------------|--------------|-------------------|
|              | IDS/IPS          | IDS/IPS          |                |                |              |                   |
|              | Proxy            | Proxy            | IDS/IPS        | IDS/IPS        | HoneyPots    | IPS               |
| C2           | Firewalls        | Firewalls L7     | Proxy          | Proxy          | Proxy        | Proxy             |
|              | System Logs      | Endpoint Suite   | Firewalls L7   | Firewalls L7   | Redirections | Endpoint Suite    |
|              | Endpoint Suite   | ACLs             | Endpoint Suite | Endpoint Suite |              |                   |
|--------------|------------------|------------------|----------------|----------------|--------------|-------------------|
|              |                  | IPS              |                |                |              |                   |
|              | IDS/IPS          | Firewall L7      | IPS            | IPS            |              |                   |
| ACTIONS      | Proxy            | DEP              | Firewall L7    | Firewall L7    | HoneyPots    | IPS               |
| OBJECTIVES   | Firewalls        | Endpoint Suite   | DEP            | DEP            | Proxy        | Proxy             |
|              | System Logs      | AV               | Endpoint Suite | Endpoint Suite | Redirections | Endpoint Suite    |
|              | Endpoint Suite   | ACLs             | AV             | AV             |              |                   |
\--------------|------------------|------------------|----------------|----------------|--------------|-------------------/
