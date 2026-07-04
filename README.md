# SAP RAP Managed Billing Application

This project demonstrates how to build a complete **SAP RAP (RESTful ABAP Programming Model) Managed Application** for Billing Management using **OData V2**.

The application covers the complete RAP development flow, from database tables to a Fiori-ready UI service.
# SAP RAP Managed Billing Application with Fiori Elements Application

## Project Architecture

The application is developed using the Managed RAP approach and consists of the following layers:

- Database Tables
- Interface (Basic) CDS Views
- Value Help CDS Views
- Root CDS Views
- Projection CDS Views
- Metadata Extensions
- Behavior Definitions & Behavior Implementations
- Virtual Elements
- Abstract Entity for Custom Actions
- Service Definition
- Service Binding (OData V2)

---

## 1. Database Tables

Two custom database tables are created as the application's data source.

| Table | Description |
|--------|-------------|
| `ZRAP_BILL_HEADER` | Stores Billing Header information |
| `ZRAP_BILLITEM` | Stores Billing Item details |

---

## 2. Interface (Basic) CDS Views

Interface views expose the database tables and serve as the foundation for the RAP Business Object.

| CDS View | Description |
|----------|-------------|
| `ZRAP_I_BILLHDR` | Billing Header Interface View |
| `ZRAP_I_BILLITM` | Billing Item Interface View |

---

## 3. Value Help CDS Views

Separate CDS Views are created to provide search helps (Value Helps) for input fields.

| CDS View | Used For |
|----------|----------|
| `ZRAP_VH_BILLING_ID` | Billing Number |
| `ZRAP_VH_BILLTYPE` | Billing Type |
| `ZRAP_VH_SALES_ORG` | Sales Organization |
| `ZRAP_VH_REL_STS` | Release Status |

---

## 4. Root CDS Views

Root Views represent the RAP Business Objects.

| CDS View | Description |
|----------|-------------|
| `ZRAP_R_BILLHDR` | Billing Header Root View |
| `ZRAP_R_BILLITM` | Billing Item Root View |

---

## 5. Projection CDS Views

Projection Views expose only the required fields to the UI.

| CDS View | Description |
|----------|-------------|
| `ZRAP_C_BILLHDR` | Billing Header Projection View |
| `ZRAP_C_BILLITM` | Billing Item Projection View |

---

## 6. Metadata Extensions

Metadata Extensions define the Fiori Elements UI, including:

- Header Information
- Facets
- Line Items
- Identification Fields
- Selection Fields
- Field Groups
- Value Helps

| Metadata Extension |
|--------------------|
| `ZRAP_ME_C_BILLHDR` |
| `ZRAP_ME_C_BILLITM` |

---

## 7. Virtual Element

A Virtual Element is implemented to calculate the **Total Amount** dynamically.

### Implementation Class

```
ZRAPCL_SO_VIRTUAL_EXIT
```

**Logic**

```
Total Amount = Sum of all Billing Item Amounts
```

The value is calculated at runtime and is not stored in the database.

---

## 8. Abstract Entity

An Abstract Entity is created for implementing a custom RAP Action.

| Entity |
|---------|
| `ZRAP_AB_CRT_NEW_DOC` |

This entity is used by the custom action **Create Billing Document**.

---

## 9. Behavior Definitions (BDEF)

Behavior Definitions define the business operations supported by the application.

### Root Behavior Definition

```
ZRAP_R_BILLHDR
```

(File: `ZRAP_R_BILLHDR_BO`)

### Projection Behavior Definition

```
ZRAP_C_BILLHDR
```

(File: `ZRAP_C_BILLHDR_BO`)

Supported operations include:

- Create
- Update
- Delete
- Read
- Determinations
- Validations
- Actions
- Feature Control
- Authorizations

---

## 10. Behavior Implementation Classes

Business logic is implemented in the following classes.

| Class |
|--------|
| `ZBP_RAP_R_BILLHDR` |
| `ZBP_RAP_C_BILLHDR` |

These classes contain the implementation for:

- Validations
- Determinations
- Custom Actions
- Feature Control
- Authorization Checks
- Business Logic

---

## 11. Service Definition

The RAP Business Object is exposed using the Service Definition.

```
ZRAP_SD_BILLING
```

---

## 12. Service Binding

A Service Binding is created using:

- **OData V2 UI**

The service is then:

- Published
- Activated
- Tested using SAP Fiori Elements Preview

---

## Application Features

- Managed RAP Business Object
- Header and Item Composition
- CRUD Operations
- Value Help (F4 Help)
- Fiori Elements UI
- Metadata Extensions
- Virtual Elements
- Custom RAP Actions
- Behavior Definitions
- Behavior Implementation
- OData V2 Service
- Dynamic Total Amount Calculation

---

## Technologies Used

- SAP S/4HANA
- ABAP RESTful Application Programming Model (RAP)
- CDS Views
- Managed Business Object
- OData V2
- SAP Fiori Elements
- ABAP Objects

---

## Project Flow

```
Database Tables
        │
        ▼
Interface CDS Views
        │
        ▼
Root CDS Views
        │
        ▼
Behavior Definition
        │
        ▼
Behavior Implementation
        │
        ▼
Projection CDS Views
        │
        ▼
Metadata Extension
        │
        ▼
Service Definition
        │
        ▼
Service Binding (OData V2)
        │
        ▼
SAP Fiori Application
```

---

## Learning Objectives

This project demonstrates how to:

- Build a Managed RAP application from scratch.
- Design Header-Item Business Objects.
- Create Interface, Root, and Projection CDS Views.
- Implement Value Helps.
- Configure Metadata Extensions.
- Implement Virtual Elements.
- Create Custom RAP Actions.
- Write Behavior Definitions and Implementations.
- Expose RAP Business Objects as OData V2 services.
- Build a Fiori Elements application with minimal UI coding.