⏺️ ➡️ 🟦 🔵🔹🔷 🔵 ☑️ ✔️ 🔴 ⭕ • ‣ → ⁕

# ⏺️ Tenant & Microsoft Entra ID

- **Tenant** = your organization's Microsoft Entra ID directory.
- **Microsoft Entra ID** = the identity service that provides and manages that directory.

- The **Tenant** stores the identities, and **Microsoft Entra ID** authenticates those identities

### ➡️ Flow

```text
Tenant Stores identities
   ↓
     -> Stores Users
     -> Stores Groups
     -> Stores Applications
     -> Stores Service Principals
     -> Stores Managed Identities
   ↓
Microsoft Entra ID authenticates them
   ↓
Azure RBAC checks permissions
   ↓
Access to Subscription
   ↓
Resource Group
   ↓
Resource
```

# ⏺️ Identities

- Objects that can be authenticated

### ➡️ Identity Contents = attributes + Credentials

- The information stored inside that identity.
  - **Attributes**: (name, email, Object ID, etc.)
  - **Credentials**: (password, certificate, secret, key, etc.)

### ➡️ Security Principal

- The identity object itself (who/what can authenticate and receive permissions).

```text
Microsoft Entra ID
        │
        ▼
Identities (objects that can be authenticated)
        │
        ├── Security Principals
        │      ├── User
        │      ├── Group
        │      ├── Device
        │      └── Service Principal
        │             ├── Application Service Principal
        │             └── Managed Identity
        │                    ├── System-assigned
        │                    └── User-assigned
        │
        └── Identity Contents
               ├── Attributes
               └── Credentials
```

# ⏺️ Service principal

- A **Service Principal** is a non-human **identity(security principal)** in a **Microsoft Entra ID** tenant that represents an application or service and is used to authenticate the application or service and authorize its access to Azure resources.

```text
Service Principal
│
├── Application Service Principal
│     └── Identity representing an App Registration
│
└── Managed Identity
      │
      ├── System-assigned Managed Identity
      │     └── Tied to one Azure resource
      │
      └── User-assigned Managed Identity
            └── Standalone identity that can be attached to multiple Azure resources
```

### ➡️ Application Service Principal

- Identity for an application you register in Microsoft Entra ID (custom apps, GitHub Actions, Terraform, CI/CD, etc.)

### ➡️ Managed Identity

- Identity automatically managed by Azure for Azure resources (VMs, App Service, Functions, Logic Apps, etc.)

##### 🟦 System-assigned

- Created and deleted with the Azure resource (1:1 relationship).

##### 🟦 User-assigned

- Created independently and can be attached to multiple Azure resources.

# ⏺️ Azure RBAC

- Authorization
