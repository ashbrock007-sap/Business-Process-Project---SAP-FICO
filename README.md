# SAP FICO End-to-End Business Process Implementation

## 📌 Project Overview
This repository contains comprehensive, step-by-step functional documentation and real-time SAP system execution screenshots for core **SAP Financial Accounting (FI)** business processes. 

Configured and tested for **Hammer Industries (Company Code: `B501` | Currency: `INR`)**, this project covers General Ledger (G/L) Accounting and Accounts Payable (AP) workflows from master data setup to transaction posting, account controls, reversals, and financial reporting.

📄 **Full Documentation:** Click on the uploaded PDF file in this repository to view all step-by-step configuration prerequisites, process flows, and SAP GUI screenshots.

---

## 🛠️ Key Configurations & Enterprise Setup
Before executing end-user transactions, the following foundational SAP FICO configurations were established:
* **General Ledger Setup:** Chart of Accounts, Account Groups (Assets, Liabilities, Expenses, Income), Retained Earnings Account, Field Status Variants (`B001`, `B004`), and G/L Tolerance Groups.
* **Posting Controls:** Posting Period Variants, Document Types (`SA` for G/L, `KR` for Vendor Invoices), Number Ranges, Posting Keys (`40`, `50`, `31`), Employee Tolerance Groups, and Reversal Reason Codes (`01`).
* **Accounts Payable Setup:** Vendor Account Groups, Number Ranges, Payment Terms, Vendor Tolerance Groups, and Reconciliation Accounts.

---

## 🔄 Business Processes Covered

### 1. General Ledger (G/L) Accounting
* **G/L Master Data Creation (`FS00`):** Created Balance Sheet and P&L accounts across all core account groups:
  * *Assets:* Cash A/c (`1000`), SBI Current A/c (`1001`), Plant & Machinery (`1002`), Furniture & Fixtures (`1003`)
  * *Liabilities:* Loan A/c (`2000`), Bank Overdraft (`2001`), Bills Payable (`2002`), Sundry Creditors (`2003`)
  * *Expenses:* Rent (`3000`), Telephone Charges (`3001`), Electricity Charges (`3002`), Discount Allowed (`3003`)
  * *Income:* Discount Received (`4000`), Income on Investment (`4001`), Miscellaneous Income (`4002`), Dividend Income (`4003`)
* **Direct G/L Posting (`FB50`):** Executed and simulated expense postings (Rent Paid, Telephone Charges) and verified Data Entry Views.
* **G/L Account Controls (`FS00`):** Tested blocking and unblocking of G/L accounts at both the **Chart of Accounts level** and **Company Code level** to enforce posting restrictions and audit compliance.
* **Document Reversal (`FB08` / `FB03`):** Executed individual document reversals to correct erroneous postings and verified the offsetting accounting entries.

### 2. Accounts Payable (AP) & Sub-Ledger Integration
* **Reconciliation G/L Accounts (`FS00`):** Configured Sundry Creditors (`2003`) and Sundry Debtors (`1004`) reconciliation accounts to integrate sub-ledgers with the General Ledger automatically.
* **Vendor Master Data (`XK01`):** Created domestic supplier records (*B E Solution Pvt Ltd*, *Sun IT Solutions*) linked to Reconciliation Account `2003`.
* **Vendor Invoice Posting (`F-43`):** Recorded supplier invoices (`KR` document type) and verified open-item liabilities.

---

## 💻 SAP Transaction Codes (T-Codes) Used

| Category | T-Code | Description |
| :--- | :--- | :--- |
| **Master Data** | `FS00` | Create / Change / Block G/L Account Centrally |
| **Master Data** | `XK01` | Create Vendor Master Data |
| **Transactions** | `FB50` | Enter G/L Account Document (Direct Posting) |
| **Transactions** | `F-43` | Enter Vendor Invoice |
| **Controls & Audit** | `FB08` | Reverse Individual Document |
| **Controls & Audit** | `FB03` | Display Accounting Document |
| **Reporting** | `FBL3N` | G/L Account Line-Item Display |
| **Reporting** | `FS10N` | G/L Account Balance Display |
| **Reporting** | `FBL1N` | Vendor Line-Item Display |

---

## 📊 Key Outcomes
* Validated end-to-end financial postings from sub-ledger vendor invoices to automated General Ledger reconciliation updates.
* Verified system error handling when attempting to post to blocked G/L accounts (`Account 2000 B501 is blocked for posting`).
* Generated accurate audit trails using standard SAP line-item and balance reports (`FBL3N`, `FS10N`, `FBL1N`).
