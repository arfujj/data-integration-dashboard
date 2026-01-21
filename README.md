#Data Integration Platform

A production-ready data platform that centralizes operational, financial, and project data into a single source of truth.  
Built using **Laravel, Supabase (PostgreSQL), Prefect, Python**, and external APIs to power dashboards, reporting, and business integrations.

This system is designed for **data accuracy, auditability, and scalability**, supporting executive reporting, KPI tracking, and profitability analysis.

---

## Table of Contents

- Overview  
- Architecture  
- Tech Stack  
- Core Features  
- ETL Pipelines  
- Dashboards  
- Integrations  
- Local Development  

---

## Overview

The ABC Data Platform aggregates data from multiple business systems into a unified, reliable data layer used for:

- Executive dashboards  
- Pipeline and profitability tracking  
- Contract and invoice reporting  
- KPI monitoring  
- User-specific analytics views  

The platform enables teams to make faster, data-driven decisions with clean, validated, and auditable data.

---

## Architecture

External Systems  
(Google Sheets, Fieldwire, QuickBooks, APIs)  
↓  
ETL / Sync Layer (Prefect + Python)  
↓  
Supabase (PostgreSQL)  
↓  
Laravel Application  
↓  
Dashboards & Admin UI  

---

## Tech Stack

### Backend & Data
- Laravel (PHP)  
- Supabase (PostgreSQL)  
- Prefect (ETL orchestration)  
- Python (ETL & integrations)  

### Frontend
- Blade Templates  
- DataTables  
- Chart.js / ApexCharts  
- Select2 / Flatpickr  

### Integrations
- Google Sheets API  
- Fieldwire API  
- Supabase REST API  

---

## Core Features

- Contract master data management  
- Pipeline tracking  
- Profitability analysis  
- KPI dashboard customization (per user)  
- Rate management  
- User & access management  
- Webhook-based task updates  
- Role-based dashboard access  
- Audit-friendly data snapshots  

---

## ETL Pipelines

### Contracts Sync

**Flow Name:** `contracts-sync`  
**Source:** Google Sheets (PLPA Master → Contracts tab)  
**Target:** Supabase table `contract`

**Behavior:**
- Full refresh  
- Preserves manual records (`is_custom = 1`)  
- Batch inserts via Supabase REST API  
- Optional CSV snapshot for auditing  

**Transformations:**
- Header normalization  
- Data validation & cleaning  
- Numeric type coercion  
- UTC timestamp normalization  

ETL scripts are located under `/etl`.

---

## Dashboards

### Available Dashboards

- Pipeline  
- Profitability  
- Rates  
- Users  
- KPI Library  

### KPI Customization

- User-specific KPI selection  
- Layouts stored in `kpi_layouts`  
- Persisted per dashboard tab  
- Drag-and-drop KPI management  

---

## Integrations

### Google Sheets
- OAuth authentication  
- Primary source for contract master data  

### Fieldwire
- Webhook-based task updates  
- Task → Contract linkage  
- Status & completion tracking  

---

## Local Development

### Prerequisites

- PHP 8.x  
- Composer  
- Node.js  
- Python 3.10+  
- Supabase project access  
