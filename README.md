# Technical Specification Framework
**Institutional Infrastructure:** Kamphaeng Phet Community Municipal Hospital  
**Document Identifier:** KPC-HIS-HEALTH-002  
**Subject:** Health Promotion Integration Service (Webhook & Flex Synthesis Engine)  
**Classification:** Internal Use Only (Confidential)  
**Revision:** 1.0.5 (2026)

---

## 1. Executive Summary

The **Health Promotion Integration Service** constitutes a specialized architectural component engineered for the systematic dissemination of public health intelligence via the LINE Messaging Interface. This system orchestrates the delivery of high-fidelity content, including automated mass-broadcasts and dynamic Flex Messages, ensuring that institutional health campaigns are executed with technical precision, cryptographic security, and administrative efficiency.

### 1.1 Systematic Attributes

| Systematic Attribute | Technical Specification |
|:---|:---|
| **System Identity** | KPC-Health-Promotion-Integration |
| **Functional Classification** | Content Delivery & Integration Middleware |
| **Architecture Paradigm** | Asynchronous Event & Broadcast Management |
| **Authentication Standard** | HMAC-SHA256 Cryptographic Verification |
| **Data Format** | LINE Flex Message JSON Synthesis |

---

## 2. Institutional Interface Specifications

The digital interface layer is governed by structured **Flex Message** and **Rich Menu** protocols. These components are designed to facilitate high-engagement healthcare communication, providing constituents with standardized access to health screening schedules, immunization updates, and maternal care resources.

### 2.1 Visual Interface Protocol (Health Promotion)



<p align="center">
  <img src="richmenu.png" alt="Health Promotion Interface Protocol" width="550" style="border: 2px solid #1a1a1a; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.15);">
  <br>
  <em><strong>Exhibit B:</strong> Architectural Layout of Health Promotion Service Interface</em>
</p>

### 2.2 Event Routing Matrix & Service Mapping

The following table delineates the systematic mapping between user-initiated keywords and their corresponding internal synthesis protocols:

| Functional Domain | Triggering Keyword Aliases | Protocol (Synthesis Handler) |
|:---|:---|:---|
| **Scheduling** | ตารางนัดหมายและการจองคิว | `getPrenatalAppointments` |
| **Education** | ความรู้คุณแม่ตั้งครรภ์, ความรู้หญิงตั้งครรภ์ | `educatePregnantWomen`, `getPregnancySymptoms` |
| **Consultation** | ติดต่อ-สอบถาม, ศูนย์ช่วยเหลือ | `getContactUS`, `getHelpCenter` |
| **Family Planning** | ความรู้เกี่ยวกับการวางแผนครอบครัว | `getContraceptiveInfo` |
| **Public Relations** | ประชาสัมพันธ์ | `communicationAndSupport` |
| **Specialized Care** | งานส่งเสริมสุขภาพแม่และเด็ก | `supportMotherChildWellbeing` |
| **Clinical Guidance** | ควรฝากเมื่อไหร่, ควรฝากครรภ์เมื่อไหร่? | `getWhenToGetCare` |
| **Institutional** | เกี่ยวกับเรา, about us, บุคลากร | `getAboutUs`, `getTeam` |
| **Information** | คำถามที่พบบ่อย | `getFaq` |

---

## 3. Transactional Architecture & Procedural Workflow

The operational lifecycle of each inbound request ensures the integrity of the data transmission during the synthesis and dissemination of structured health content.



```mermaid
graph TD
    %% Node Definitions
    A([LINE Gateway Ingress]) --> B[HTTPS POST Request /webhook]
    B --> C{Security Validation<br/>Gateway}
    
    %% Security & Validation Logic
    C -- Authentication Failure --> D[401 Unauthorized & Security Logging]
    C -- Verified Origin --> E[Event Orchestration & Context Parsing]
    
    %% Content Processing Logic
    E --> F{Event Routing Matrix}
    F -- Actionable Event --> G[Internal Content API Request]
    F -- Administrative Event --> H[Subscriber Profile Synchronization]
    
    %% Content Synthesis
    G --> I[Health Promotion Logic Integration]
    I --> J[Flex Message Synthesis Engine]
    J --> K[JSON Payload Object Construction]
    
    %% Terminal Response Delivery
    K --> L[Outbound API Transmission]
    L --> M([200 OK Status Acknowledgement])
    
    %% Styling for Professionalism
    style C fill:#f4f4f4,stroke:#007c91,stroke-width:2px
    style J fill:#f4f4f4,stroke:#333,stroke-width:2px
    style F fill:#f4f4f4,stroke:#007c91,stroke-width:2px
