# SAP MM - Purchase Order Output Configuration (NEU)

This repository demonstrates how to configure automatic message outputs for Purchase Orders in SAP S/4HANA. In this scenario, we set up the traditional `NEU` output type, ensuring that purchase orders are automatically printed immediately upon saving.

## 1. SOP: Bypassing S/4HANA Output Management for Classic PO Message Generation

**Step 1: Navigate to the Output Control Settings**
* Execute transaction `SPRO` and open the SAP Reference IMG.
* Follow the menu path: *Cross-Application Components → Output Control → Manage Application Object Type Activation*.

**Step 2: Deactivate the Modern Output Engine**
* Locate the Application Object Type `PURCHASE_ORDER` in the generated list.
* Change its Activation Status from **Active** to **Inactive**.

> **System Architecture Note:** This action successfully disables the BRF+/Adobe Document Services framework. The system will automatically revert to the classic NAST (SAPscript/SmartForms) message determination procedure, bypassing the need for complex server-side customizing or missing Java stacks.

![Application Object Type Configuration](screenshots/Zrzut%20ekranu%202026-08-03%20151439.png)

**Step 3: Configure the Classic Output Parameters in the PO**
To complete this step, proceed to the dispatch and communication settings outlined below.

---

## 2. Dispatch Time Settings

To ensure the output is generated instantly when the document is created, the dispatch time must be properly configured. Within the output condition records or document output details, set the **Dispatch time** to `4 Send immediately (when saving the application)`.

![Dispatch Time Configuration](screenshots/dispatch%20time.png)

---

## 3. Communication Method and Print Parameters

Finally, the printing parameters must be defined to route the output to the correct destination. Set the **Logical destination** (e.g., `LOCL` for local printing), check the **Print immediately** box, and ensure the **Storage Mode** is set to `1 Print only` to trigger the physical or PDF printout instantly.

![Communication Method Settings](screenshots/communication%20method%201.png)