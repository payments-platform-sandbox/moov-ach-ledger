# Moov ACH + Ledger (`moov-ach-ledger`)

> ACH processing and **ledger service** built with Moov and Postgres, including reconciliation and webhook handling.  

## 1) Overview
This service integrates with **Moov ACH** to simulate payment rails.  
It also maintains a **ledger** in Postgres to ensure all transactions are consistent and auditable.  

**Responsibilities**
- Initiate ACH debit/credit requests via Moov SDK  
- Store immutable ledger entries for every transaction  
- Handle Moov webhooks (payment settled, failed, returned)  
- Reconcile ledger against Moov state  


## 2) Functional Requirements
- **FR1 (Workflow Execution):** Executes ACH step of payment workflows  
- **FR2 (Webhook Handling):** Consumes Moov callbacks  
- **FR3 (Reconciliation):** Scheduled jobs to compare ledger vs Moov  
- **FR4 (Refunds & Cancellations):** ACH reversal and ledger updates  


## 3) Data Model
- **Ledger entries**: immutable, append-only  
- **Events**: `PaymentCreated`, `LedgerUpdated`, `RefundProcessed`  


## 4) Tech Stack
- Java 17 + Spring Boot  
- Moov ACH SDK  
- Postgres for ledger storage  
- Kafka (optional) for publishing payment events  


## 5) License
MIT
