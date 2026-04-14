# User Roles & Persona Workflows: The Human Journey

This document explains who uses the Neowaa system and exactly how they interact with it. We use **User Flow Diagrams** to visualize the steps each person takes from start to finish.

---

## 1. High-Level Use Case (System Interaction)

This diagram shows how different users interact with the core platform services.

```mermaid
graph LR
    Owner((Property Owner))
    Tenant((Tenant))
    Photo((Photographer))
    Admin((System Admin))
    Agent((Broker/Agent))

    subgraph Platform
        Listing[Property Listing]
        Contract[Digital Leasing]
        Payment[Payment Gateway]
        Verify[Verification AI]
        Media[Media Portal]
    end

    Owner --> Listing
    Owner --> Contract
    Tenant --> Listing
    Tenant --> Contract
    Tenant --> Payment
    Photo --> Media
    Media --> Verify
    Admin --> Verify
    Admin --> Payment
    Agent -.-> Listing
```

---

## 2. Property Owners / Landlords
Owners are focused on maximizing rental yield and minimizing management effort.

### Core Workflow:
1. **Onboarding**: Direct registration or UAE Pass.
2. **Listing**: Uploading Title Deed and property specs.
3. **Verification**: AI-driven owner/property check.
4. **Contracting**: Generating a smart lease and digital signing.

### Owner User Flow (Mermaid)
```mermaid
sequenceDiagram
    participant O as Owner
    participant S as Neowaa System
    participant G as Govt (DLD/UAE Pass)

    O->>S: Register via UAE Pass
    G-->>S: Identity Verified
    O->>S: Upload Title Deed + Photos
    S->>S: AI OCR Reads Deed
    S->>G: Verify Ownership
    G-->>S: Match Found (Listed)
    O->>S: Set Installments (1-12)
    O->>S: Generate Lease & Sign
    S->>S: Pushed to Tenant
```

---

## 3. Tenants / Renters
Tenants look for a seamless, transparent, and legally secure search and move-in experience.

### Core Workflow:
1. **Discovery**: AI-powered "vibe" search and VR tours.
2. **Acceptance**: Digital lease review and OTP-based signature.
3. **Financials**: Paying security deposit and setting up auto-rent.
4. **Exit**: Digital move-out request and deposit recovery.

### Tenant User Flow (Mermaid)
```mermaid
sequenceDiagram
    participant T as Tenant
    participant S as Neowaa System
    participant P as Payment Gateway

    T->>S: Search for "Sunlit 2BHK"
    S-->>T: Semantic Results + VR Tour
    T->>S: Accept Lease Terms
    S->>T: Send OTP for Signature
    T->>S: Enter OTP (Signed)
    T->>P: Pay Deposit & Admin Fees
    P-->>S: Success
    T->>S: Set Up DDA/Auto-Debit
    S-->>T: Move-in Ready (Digital NOC)
```

---

## 4. Professional Photographers (Pro-Media Flow)
Photographers act as "Trust Officers" for the platform.

### Pro-Media User Flow (Mermaid)
```mermaid
flowchart TD
    Assign[Receive Job Assignment] --> Visit[Property Visit & Shoot]
    Visit --> Login[Login to Photographer Portal]
    Login --> Upload[Upload HQ Photos/Videos]
    Upload --> AI[AI Quality Check - Gemma3]
    AI -- High Quality --> Badge[Auto-Issue 'Verified Badge']
    AI -- Low Quality --> Recapture[Request Re-shoot]
```

---

## 5. Backend Administrators (Ops Layer)
Admins manage the ecosystem, resolve disputes, and ensure financial integrity.

### Admin Responsibilities:
*   **Manual KYC**: Overriding AI if document scans are unclear.
*   **Dispute Handling**: Coordinating with the **Rental Dispute Center (RDC)**.
*   **Commission Tracking**: Payouts to referral partners.

---

## 6. Brokers & Agents (Phase 2)
Agents are delegated by owners to handle specific properties.

### Agent Delegation Flow (Mermaid)
```mermaid
flowchart LR
    Owner[Owner] -->|Delegate| Prop[Property X]
    Prop --> Agent[Broker/Agent Account]
    Agent -->|Upload| Ejari[Finalized Lease]
    Agent -->|Manage| Leads[Tenant Lead Tracking]
```

---
*Prepared by Antigravity for Lince's Understanding folder.*
