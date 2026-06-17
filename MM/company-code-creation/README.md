# Enterprise Structure: Company Code Baseline Setup

---

## 1. Business Purpose

This repository documents the foundational configuration of a new Company Code (Financial Entity) in SAP S/4HANA. Establishing a robust Financial Accounting (FI) baseline is a mandatory prerequisite for any future enterprise operations. Without a fully configured and structurally sound Company Code, no business transactions can be processed or posted to the General Ledger.

---

## 2. System Decision Logic & Best Practices

Rather than building a Company Code from scratch (which risks missing critical underlying tax and financial logic), the SAP Best Practice approach is applied. 

1. **Template Copying (EC01):** The new organizational unit is copied from a standard SAP country template. This ensures the inheritance of hundreds of background customizing tables, including tax procedures and baseline condition structures.
2. **Global Parameters Mapping (OBY6):** The unit is customized with specific structural rules (Fiscal Year, Posting Periods, Field Status) to dictate how data is processed within the financial ledgers.
3. **Architecture Validation:** The structural integrity is validated by extending core master data and simulating a financial posting to prove the entity is active and operational.

---

## 3. Organizational Structure Configuration

### 3.1 Object Creation via Reference (EC01)

The new Company Code is generated using the organizational object copier to maintain data integrity.

- **Copying Process:** Inheriting structural data from the reference template.
  ![Copy Company Code](01_ec01_copy_company_code.png)
- **Execution Log:** Confirming the successful transfer of dependent tables.
  ![Copy Log](02_ec01_copy_log.png)

### 3.2 Entity Localization (OX02)

Adjusting specific entity details, local currency (EUR), and Time Zone (CET) to ensure accurate timestamping for future business documents and transactions.

![Company Code Data](03_ox02.png)
![Address Details](04_ox02_address_details.png)

---

## 4. Global Settings & Control Parameters

### 4.1 Global Parameters (OBY6)

The central control hub for the Company Code. This ensures the unit knows how to process incoming business transactions.
![Global Parameters](05_oby6_global_parameters.png)

### 4.2 Fiscal Year Variant (OB29 & OB37)

Defining the accounting calendar and assigning it to the Company Code to establish the financial framework.
![Fiscal Year Definition](06_ob29_fiscal_year_variant.png)
![Fiscal Year Assignment](07_ob37_assign_fy_variant.png)

### 4.3 Posting Period Variant (OBBO & OB52)

Controlling the data flow gateway. The variant is created, assigned, and the specific time intervals are opened to allow the system to post data into the active periods.
![Posting Period Variant](08_obbo_posting_period_variant.png)
![Open Posting Periods](09_ob52_open_posting_periods.png)

### 4.4 Chart of Accounts Assignment (OB62)

Linking the operational Chart of Accounts to the new entity to enable standard financial reporting and account determination.
![Assign Chart of Accounts](10_ob62_assign_chart_of_accounts.png)

---

## 5. Master Data Readiness & Architecture Verification

Before the unit can be considered fully functional, the foundational Master Data must be established and the architecture rigorously tested. The following validation protocol is executed to ensure system readiness:

### 5.1 Master Data Extension (FS00)
Operational G/L accounts are extended centrally to the new Company Code to populate table `SKB1`. Attempting to post any document without extending the accounts yields an `SKB1` database error, halting all downstream processes.

### 5.2 The Acid Test (FB50)
To validate the structural integrity of the newly configured Company Code, a direct financial simulation is executed. A double-entry simulation forces the system's validation engine to evaluate the Posting Periods, Field Status Variants, and Account Assignments simultaneously. A successful simulation confirms the unit is fully operational, structurally sound, and ready for future module integrations.