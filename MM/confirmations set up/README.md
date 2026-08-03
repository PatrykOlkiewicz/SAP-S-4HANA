SOP: Bypassing S/4HANA Output Management for Classic PO Message Generation
Step 1: Navigate to the Output Control Settings

Execute transaction SPRO and open the SAP Reference IMG.

Follow the menu path: Cross-Application Components → Output Control → Manage Application Object Type Activation.

Step 2: Deactivate the Modern Output Engine

Locate the Application Object Type PURCHASE_ORDER in the generated list.

Change its Activation Status from Active to Inactive.

System Architecture Note: This action successfully disables the BRF+/Adobe Document Services framework. The system will automatically revert to the classic NAST (SAPscript/SmartForms) message determination procedure, bypassing the need for complex server-side customizing or missing Java stacks.

Step 3: Configure the Classic Output Parameters in the PO

Open transaction ME21N to create a new Purchase Order (or ME22N to edit an existing one).

Navigate to the Messages screen at the header level and enter your classic output type (e.g., NEU).

Select the message line and click the Communication method button. To prevent the system from searching for a non-existent optical archive (which triggers the ME142 error), set the Storage Mode field strictly to 1 (Print only) and ensure your logical destination (e.g., LP01 or LOCL) is filled.

Go back, click the Further data button, and change the Dispatch time to 4 (Send immediately).

Save the Purchase Order. The message will now process automatically and generate a successful green status.