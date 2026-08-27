# SAP SD Customer Return & Credit Memo Procedure

---

## 1. Business Purpose

This repository documents the end-to-end customer return and credit memo procedure in SAP Sales and Distribution (SD). It outlines the configuration and transactional steps required to process customer returns using return document type `RK`, create a corresponding credit memo request (`RERK`), execute outbound delivery without picking, perform Post Goods Issue (PGI), and generate the final billing document.

---

## 2. Create Return Order (VA01)

### 2.1 Initial Setup & Document Type `RK`
- **Transaction:** `VA01`
- **Order Type:** `RK` (Return)

![VA01 Initial Screen](screenshots/1%20va01.png) 
![VA01 Order Header](screenshots/2%20va01.png)

### 2.2 Item Adjustments & Control Data
- **Quantity Correction:** Adjust item quantities to reflect only what is physically returned and accepted on the invoice (e.g., if the primary delivery was `102` and the return is `2`, maintain `100` as the active quantity).
- **Plant Routing:** Change the receiving plant if goods need to be routed to an alternative storage location.

![Items to Correct](screenshots/3%20Items%20to%20correct.png)

### 2.3 Blocks and Rejection Reasons
- Maintain the **Billing Block** and **Reason for Rejection** alongside necessary internal notes to control the processing flow.

> **Note:** Proper maintenance of the billing block prevents premature credit memo generation before quality inspection or logistical confirmation of the returned goods.

![Billing Block Reason](screenshots/4%20billing%20block%20reason%20.png)

---

## 3. Create Credit Memo Request with Reference to `RK` (RERK)

- **Transaction:** `VA01` (Create with Reference)
- **Reference Document:** Return Order (`RK`) created in the previous step.
- **Document Type:** `RERK` (Credit Memo Request referencing return)

> **System Logic:** Referencing the original return order ensures pricing, quantities, and customer details are automatically copied over, maintaining auditability and document flow.

![RERK with Reference to RK](screenshots/5%20RERK%20WITH%20REF%20TO%20RK.png)

---

## 4. Outbound Delivery from `RERK`

- **Transaction:** `VL01N`
- **Action:** Generate the outbound delivery document originating from the credit memo request (`RERK`).

![Deliver from RERK without Picking](screenshots/6%20DELIVER%20FROM%20RERK%20WITHOUT%20ANY%20PICKING.png)

---

## 5. Post Goods Issue (PGI) Without Picking

- **Transaction:** `VL02N`
- **Action:** Execute Post Goods Issue (PGI) directly for the delivery without requiring any picking steps, reflecting the return receipt into inventory stock.

---

## 6. Billing with Reference to `RK` (VF01 / VF03)

### 6.1 Create Billing Document (VF01)
- **Transaction:** `VF01`
- **Action:** Generate the final billing document (credit memo) referencing the return order (`RK`).

![VF01 with Reference to RK](screenshots/7%20VF01%20WITH%20REF%20TO%20RK.png)

### 6.2 Review and Output (VF03)
- **Transaction:** `VF03`
- **Action:** Display the completed billing document and verify the generated output PDF.

![VF03 Display Document](screenshots/8%20VF03.png) 
![Billing Output PDF](screenshots/9%20PDF.png)