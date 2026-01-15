# Technical Specification Framework
**Institutional Infrastructure: Kamphaeng Phet Community Municipal Hospital**
*Document Identifier: KPC-HIS-HEALTH-002*
*Subject: Health Promotion Integration Service (Webhook & Flex Synthesis Engine)*

---

## 1. Executive Summary

The **Health Promotion Integration Service** constitutes a specialized architectural component engineered for the systematic dissemination of public health intelligence via the LINE Messaging Interface. This system orchestrates the delivery of high-fidelity content, including automated mass-broadcasts and dynamic Flex Messages, ensuring that institutional health campaigns are executed with technical precision, cryptographic security, and administrative efficiency.

| Systematic Attribute | Technical Specification |
|:---|:---|
| **System Identity** | KPC-Health-Promotion-Integration |
| **Functional Classification** | Content Delivery & Integration Middleware |
| **Architecture Paradigm** | Asynchronous Event & Broadcast Management |
| **Authentication Standard** | HMAC-SHA256 Cryptographic Verification |

---

## 2. Institutional Interface Specifications

The digital interface layer is governed by structured **Flex Message** and **Rich Menu** protocols. These components are designed to facilitate high-engagement healthcare communication, providing constituents with standardized access to health screening schedules, immunization updates, and wellness resources.

<p align="center">
  <img src="richmenu.png" alt="Health Promotion Interface Protocol" width="100%" style="border: 1.5px solid #1a1a1a; box-shadow: 0 4px 12px rgba(0,0,0,0.15);">
</p>
<p align="center"><strong>Exhibit B:</strong> <em>Architectural Layout of Health Promotion Service Interface</em></p>

---

## 3. Transactional Architecture & Procedural Workflow

The operational lifecycle of each inbound request is delineated in the following flowchart. The architecture enforces a mandatory validation phase at the security perimeter to ensure the integrity of the data transmission during the synthesis and dissemination of structured health content.

```mermaid
graph TD
    %% Node Definitions
    A([LINE Gateway Ingress]) --> B[HTTPS POST Request /webhook]
    B --> C{Security Validation<br/>Gateway}
    
    %% Security & Validation Logic
    C -- Authentication Failure --> D[401 Unauthorized & Security Logging]
    C -- Verified Origin --> E[Event Orchestration & Context Parsing]
    
    %% Content Processing Logic
    E --> F{Event Routing<br/>Matrix}
    F -- Actionable Event --> G[Internal Broadcast API Request]
    F -- Administrative Event --> H[Subscriber Profile Synchronization]
    
    %% Content Synthesis
    G --> I[Health Promotion API Integration]
    I --> J[Flex Message Synthesis Engine]
    J --> K[JSON Payload Object Construction]
    
    %% Terminal Response Delivery
    K --> L[Outbound API Transmission]
    L --> M([200 OK Status Acknowledgement])
    
    %% Styling for Professionalism
    style C fill:#f9f9f9,stroke:#333,stroke-width:2px
    style J fill:#f9f9f9,stroke:#333,stroke-width:2px
    style F fill:#f9f9f9,stroke:#333,stroke-width:2px
