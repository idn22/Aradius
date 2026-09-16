READMI
GPL-3.0 license
A-RADIUS Platform Architecture, Tenant Provisioning & Operations Blueprint
Status: AUTHORITATIVE WORKING BLUEPRINT / EXECUTION REFERENCE
Architecture: Multi-Tenant ISP Platform — PostgreSQL Schema-per-Tenant
Backend: Go
Purpose: Acuan struktur, provisioning, operasional ISP, role applications, runtime, dan ritme pengerjaan end-to-end.

Daftar Isi
I. Development / Platform Side
1. Canonical Developer Blueprint 15/15
2. Existing Engineering Foundation
3. Engineering Capability Matrix
II. ISP Lifecycle / Control Plane
4. Developer Dashboard
5. ISP Registration
6. Automatic Provisioner
7. Portal Activation
8. Tenant Resolver
III. ISP Tenant / Operation Side
9. First Login Wizard
10. Administrator Application — 16 Modules
11. Reseller Application
12. Sales Application
13. Mitra Application
14. Teknisi Application
IV. Runtime & Continuous Operations
V. End-to-End Workflows
VI. ISP Lifecycle State Model
VII. Standard Work Execution Loop
VIII. Working Rules
IX. End-to-End Architecture Summary
Struktur Lengkap A-RADIUS
A-RADIUS
│
├══════════════════════════════════════════════════════════════
│ I. DEVELOPMENT / PLATFORM SIDE
├══════════════════════════════════════════════════════════════
│
├── 1. CANONICAL DEVELOPER BLUEPRINT 15/15
│
├── 2. EXISTING ENGINEERING FOUNDATION
│
└── 3. ENGINEERING CAPABILITY MATRIX
     │
     ├── Quality & Testing
     ├── Security, Secrets & Access Control
     ├── Tenant Isolation
     ├── Migration Orchestration
     ├── Background Jobs & Scheduler
     ├── Backup / Restore / DR
     ├── Release / Rollback
     └── Observability & Operational Guardrails
│
├══════════════════════════════════════════════════════════════
│ II. ISP LIFECYCLE / CONTROL PLANE
├══════════════════════════════════════════════════════════════
│
├── 4. DEVELOPER DASHBOARD
├── 5. ISP REGISTRATION
├── 6. AUTOMATIC PROVISIONER
├── 7. PORTAL ACTIVATION
└── 8. TENANT RESOLVER
│
├══════════════════════════════════════════════════════════════
│ III. ISP TENANT / OPERATION SIDE
├══════════════════════════════════════════════════════════════
│
├── 9. FIRST LOGIN WIZARD
├── 10. ADMINISTRATOR APPLICATION
│       └── 16 Administrator Modules
├── 11. RESELLER APPLICATION
├── 12. SALES APPLICATION
├── 13. MITRA APPLICATION
└── 14. TEKNISI APPLICATION
│
└══════════════════════════════════════════════════════════════
  IV. RUNTIME & CONTINUOUS OPERATIONS
══════════════════════════════════════════════════════════════
    │
    ├── RADIUS
    ├── Network
    ├── NAS / MikroTik
    ├── OLT / FTTH
    ├── ONU / ONT
    ├── GenieACS
    ├── Billing
    ├── Monitoring
    ├── Audit
    ├── Alerts
    ├── Background Jobs
    ├── Backup / Restore
    └── Security
I. Development / Platform Side
1. Canonical Developer Blueprint 15/15
A-RADIUS
└── DEVELOPER
    │
    ├── 01. REPOSITORY & BRANCH MANAGEMENT
    │   ├── Repository
    │   ├── Branches
    │   ├── Commits
    │   ├── Pull Requests
    │   ├── Releases
    │   └── Tags
    │
    ├── 02. DATABASE & MIGRATIONS
    │   │
    │   ├── Global / Development Database
    │   │   ├── PostgreSQL
    │   │   ├── master_control Schema
    │   │   ├── Tenants Registration
    │   │   ├── Provisioning Logs
    │   │   ├── Migration Status
    │   │   ├── Schema Management
    │   │   ├── Rollback
    │   │   ├── Backup
    │   │   └── Restore
    │   │
    │   ├── Per-Client RADIUS Databases
    │   │   └── Schema-per-Tenant Isolation
    │   │       ├── customers
    │   │       ├── radacct
    │   │       ├── invoices
    │   │       ├── nas_nodes
    │   │       ├── ip_pools
    │   │       ├── customer_ip_bindings
    │   │       └── ip_conflict_logs
    │   │
    │   └── Database Services
    │       ├── Tenant Schema Provisioning
    │       ├── ClientDatabaseRouter
    │       ├── Tenant Context Switcher
    │       ├── Migration Validation
    │       └── PostgreSQL / Per-Client Integration
    │
    ├── 03. API GATEWAY & ROUTING
    │   ├── Routes
    │   ├── Middleware
    │   ├── Authentication
    │   ├── Authorization / Tenant AuthZ
    │   ├── Rate Limit
    │   ├── API Health
    │   └── API Logs
    │
    ├── 04. RADIUS CORE ENGINE
    │   ├── Authentication
    │   ├── Accounting
    │   ├── CoA
    │   ├── Attributes
    │   ├── Policies
    │   ├── Sessions
    │   └── Runtime Health
    │
    ├── 05. TENANT & SUBSCRIBER MANAGEMENT
    │   │
    │   ├── Client ISP Directory & Provisioning
    │   │   ├── Client Profile & Status
    │   │   │   ├── Active
    │   │   │   ├── Inactive
    │   │   │   └── Suspended
    │   │   ├── License Tier
    │   │   ├── Expiration
    │   │   ├── Enforcement
    │   │   ├── Credential Rotation
    │   │   └── Client Portal Access
    │   │
    │   └── Subscriber & End-User Profiles
    │       ├── Credentials
    │       ├── Service Plan
    │       ├── Bandwidth
    │       ├── IP / MAC Binding
    │       └── RADIUS Attributes
    │
    ├── 06. BILLING & LICENSE
    │   ├── Billing Engine
    │   ├── License Engine
    │   ├── Subscription
    │   └── Payment Integration
    │
    ├── 07. NAS & DISRUPTOR MANAGEMENT
    │   ├── NAS Registry
    │   ├── WireGuard P2P / NAT Traversal
    │   ├── Tunnel Allocation
    │   ├── IP / MAC Binding
    │   ├── Zero-Touch Provisioning
    │   ├── RADIUS Secret
    │   ├── UDP 1812
    │   ├── UDP 1813
    │   ├── UDP 3799
    │   ├── NAS Health
    │   ├── Handshake
    │   ├── Reachability
    │   ├── Suspension Trigger
    │   ├── Grace Period
    │   ├── Warning
    │   ├── CoA / Disconnect
    │   └── Reactivation
    │
    ├── 08. RADIUS SIMULATION & DEBUGGER TOOL
    │   ├── Live RadTest
    │   ├── Authentication Test
    │   ├── Accounting Test
    │   ├── Packet Flow
    │   ├── Attribute Inspector
    │   ├── Tenant Context Switcher
    │   ├── Authentication Log Trace
    │   └── CoA / Disconnect Tester
    │
    ├── 09. DEPLOYMENT & CI/CD
    │   ├── Pipelines
    │   ├── Build
    │   ├── Tests
    │   ├── Security Scan
    │   ├── Docker Build
    │   ├── Deployment
    │   ├── Rollback
    │   └── Deployment History
    │
    ├── 10. STAGING & PREVIEW
    │   ├── Staging Environment
    │   ├── Preview Deployment
    │   ├── Smoke Test
    │   └── Promotion Gate
    │
    ├── 11. AI & SMART AUTOMATION
    │   ├── Automation Rules
    │   ├── Incident Analysis
    │   ├── Log Analysis
    │   ├── Deployment Advisor
    │   └── Smart Remediation
    │
    ├── 12. MONITORING
    │   ├── Runtime Health
    │   ├── Containers
    │   ├── CPU / RAM
    │   ├── Services
    │   ├── PostgreSQL
    │   ├── Redis
    │   └── Network
    │
    ├── 13. LOGS & AUDIT
    │   ├── Application Logs
    │   ├── Deployment Logs
    │   ├── Security Logs
    │   ├── RADIUS Logs
    │   └── Audit Trail
    │
    ├── 14. ALERTS & INCIDENTS
    │   ├── Active Alerts
    │   ├── Incident Queue
    │   ├── Severity
    │   └── Resolution History
    │
    └── 15. DEVELOPER DOCUMENTATION
        ├── API Docs
        ├── Architecture
        ├── Deployment
        ├── Database
        ├── RADIUS
        └── Runbooks
2. Existing Engineering Foundation
Existing foundation dipertahankan dan disejajarkan ke struktur Development di atas.

Existing Engineering Foundation
│
├── Repository Foundation
├── Database Foundation
├── API Foundation
├── RADIUS Foundation
├── Tenant Foundation
├── Authentication / Authorization Foundation
├── Network Foundation
├── NAS Foundation
├── WireGuard Foundation
├── CI/CD Foundation
├── Staging Foundation
├── Monitoring Foundation
├── Backup / Restore Foundation
└── Production Readiness Foundation
3. Engineering Capability Matrix
Engineering Capability Matrix adalah hardening layer lintas module.

ENGINEERING CAPABILITY MATRIX
│
├── A. QUALITY & TESTING
│   ├── Unit Tests
│   ├── Integration Tests
│   │   ├── PostgreSQL
│   │   └── Redis
│   ├── API Contract Tests
│   ├── RADIUS Conformance
│   │   ├── PAP
│   │   ├── CHAP
│   │   ├── MS-CHAPv2
│   │   ├── Accounting Start
│   │   ├── Accounting Interim
│   │   ├── Accounting Stop
│   │   ├── CoA
│   │   └── Disconnect
│   ├── Tenant Isolation Tests
│   ├── Migration Tests
│   ├── Load Tests
│   ├── Soak Tests
│   ├── Chaos Tests
│   └── Quality Gates
│
├── B. SECURITY, SECRETS & ACCESS CONTROL
│   ├── Secret Inventory
│   ├── Encryption Keys
│   ├── RADIUS Shared Secrets
│   ├── WireGuard Keys
│   ├── DB Credentials
│   ├── Key Rotation
│   ├── Secret Detection
│   ├── CVE Monitoring
│   ├── SAST
│   ├── Container Scan
│   ├── Platform RBAC
│   ├── Tenant RBAC
│   ├── Dangerous Action Guard
│   ├── Break-glass
│   └── Security Audit
│
├── C. TENANT ISOLATION
│   ├── Tenant Identity
│   ├── Tenant Context
│   ├── Tenant Resolver
│   ├── Schema-per-Tenant
│   ├── Query Isolation
│   ├── Connection Pool Isolation
│   ├── Cross-Tenant Guard
│   └── Isolation Assertions
│
├── D. MIGRATION ORCHESTRATION
│   ├── Schema Version Ledger
│   ├── Idempotent Runner
│   ├── Advisory Lock
│   ├── Concurrency Control
│   ├── Per-Tenant Status
│   ├── Partial Failure
│   ├── Resume
│   ├── Drift Detection
│   └── Dry-run
│
├── E. BACKGROUND JOBS & SCHEDULER
│   ├── Scheduler
│   ├── Leader Election
│   ├── Job Queue
│   ├── Worker Pool
│   ├── Retry
│   ├── Backoff
│   ├── Dead-Letter Queue
│   ├── Idempotency Registry
│   └── Job History
│
├── F. BACKUP / RESTORE / DR
│   ├── Global Backup
│   ├── Per-Tenant Backup
│   ├── PITR / WAL
│   ├── Full Restore
│   ├── Single-Tenant Restore
│   ├── Restore Drill
│   ├── RPO
│   ├── RTO
│   ├── Offsite Copy
│   └── DR Runbook
│
├── G. RELEASE / ROLLBACK
│   ├── Development
│   ├── Staging
│   ├── Production
│   ├── Preview
│   ├── Smoke Test
│   ├── Promotion Gate
│   ├── Deployment
│   ├── Rollback
│   ├── Deployment History
│   └── Change Freeze
│
└── H. OBSERVABILITY
    ├── Service Health
    ├── PostgreSQL Health
    ├── Redis Health
    ├── RADIUS Health
    ├── Network Health
    ├── Metrics
    ├── Logs
    ├── Audit
    ├── Alerts
    ├── Incidents
    ├── SLO
    └── Runbooks
II. ISP Lifecycle / Control Plane
4. Developer Dashboard
DEVELOPER DASHBOARD
│
├── Tenant Registry
├── ISP Registration
├── ISP Profile
├── Tenant Status
├── Provisioning Status
├── License / Entitlement
├── Feature Status
└── Provisioning History
Developer Dashboard adalah control plane A-RADIUS. Ia digunakan untuk lifecycle platform dan tenant ISP, bukan untuk operasional pelanggan ISP sehari-hari.

5. ISP Registration
ISP REGISTRATION
│
├── ISP Identity
├── Company / ISP Profile
├── Owner Information
├── Contact Information
├── Package / License
├── Enabled Features
├── Tenant Limits
└── Initial Configuration
ISP Registration
      │
      ▼
Validated Provisioning Request
Hasil tahap ini belum menjadi tenant aktif.

6. Automatic Provisioner
AUTOMATIC PROVISIONER
│
├── 01. TENANT REGISTRATION
│   ├── Generate Tenant ID
│   ├── Generate Tenant UUID
│   ├── Register Tenant
│   └── Initial Status
│
├── 02. SCHEMA CREATION
│   ├── Create Tenant Schema
│   ├── Validate Schema
│   └── Register Schema Version
│
├── 03. MIGRATION
│   ├── Run Migration
│   ├── Validate Migration
│   ├── Record Version
│   └── Record Migration Status
│
├── 04. SEED BASELINE
│   ├── Default Configuration
│   ├── Default Roles
│   ├── Default Permissions
│   ├── System Settings
│   ├── Reference Data
│   └── Initial Module Configuration
│
├── 05. OWNER ACCOUNT
│   ├── ISP Owner
│   ├── Administrator Identity
│   ├── Initial Credential
│   └── Role Binding
│
├── 06. INITIAL RBAC
│   ├── Owner
│   ├── Administrator
│   ├── Operator
│   ├── Permission Matrix
│   └── Capability Assignment
│
├── 07. LICENSE / ENTITLEMENT
│   ├── Package
│   ├── Enabled Modules
│   ├── Feature Flags
│   ├── Service Limits
│   └── Tenant Limits
│
├── 08. PROVISIONING VERIFICATION
│   ├── Tenant Check
│   ├── Database Check
│   ├── Schema Check
│   ├── Migration Check
│   ├── Seed Check
│   ├── Owner Check
│   ├── RBAC Check
│   ├── Entitlement Check
│   ├── Isolation Check
│   └── Portal Readiness
│
└── 09. FAILURE HANDLING
    ├── Retry
    ├── Resume
    ├── Rollback
    ├── Compensation
    └── Failure Audit
Provisioning State Gate
REGISTERED
     │
     ▼
PROVISIONING
     │
     ├──────────── FAILED
     │                │
     │                ├── Retry
     │                ├── Resume
     │                └── Rollback
     │
     └──────────── all gates PASS
                      │
                      ▼
                    READY
7. Portal Activation
PORTAL ACTIVATION
│
├── Administrator Portal Enablement
├── Tenant Route Activation
├── Access Policy Activation
├── Role Application Availability
├── First Login State
└── Portal Readiness Verification
Provisioning
=
membuat tenant

Portal Activation
=
membuka tenant agar digunakan ISP
8. Tenant Resolver
TENANT RESOLVER
│
├── Resolve Tenant Identity
├── Verify Tenant Status
├── Load Tenant Context
├── Resolve Authoritative Schema
├── Apply Tenant Scope
├── Apply Tenant RBAC
├── Apply Capability
├── Isolation Guard
└── Route to Correct Tenant
Universal Tenant Boundary
Request
   │
   ▼
Authentication
   │
   ▼
Tenant Resolver
   │
   ▼
Authorization
   │
   ▼
Tenant Context
   │
   ▼
Correct Tenant Schema
ISP-A
  ↓
tenant_a

ISP-B
  ↓
tenant_b

ISP-A ─── X ───► tenant_b
III. ISP Tenant / Operation Side
9. First Login Wizard
FIRST LOGIN WIZARD
│
├── Administrator Verification
├── Initial Password Change
├── Security Setup
├── ISP Profile Setup
├── Branding
├── Initial System Configuration
├── Initial Network Configuration
├── Notification Configuration
└── Setup Completion
First Login Wizard tidak melakukan create database, create schema, global platform migration, atau platform deployment. Semua pekerjaan tersebut selesai di sisi provisioning/control plane.

10. Administrator Application — 16 Modules
Struktur berikut adalah dashboard yang digunakan oleh ISP.

A-RADIUS
└── ADMINISTRATOR
    │
    ├── 01. DASHBOARD
    │   ├── Administrator Control Center
    │   ├── System Health
    │   ├── Database Status
    │   ├── Active Users
    │   ├── Active Profiles
    │   ├── Recent Sign-in
    │   └── Network Devices
    │
    ├── 02. PROFIL VOUCHER
    │   ├── Profile List
    │   ├── Create Profile
    │   ├── Edit Profile
    │   ├── Package / Service
    │   └── Profile Status
    │
    ├── 03. VOUCHER CONTROL CENTER
    │   ├── Overview
    │   ├── Stock
    │   ├── Generate Voucher
    │   ├── Active
    │   ├── Sold
    │   ├── Expired
    │   └── Voucher Audit
    │
    ├── 04. PELANGGAN
    │   ├── Customer List
    │   ├── Customer Detail
    │   ├── Service
    │   ├── Subscription
    │   ├── Session
    │   └── Status
    │
    ├── 05. RADIUS
    │   ├── Server
    │   ├── Authentication
    │   ├── Accounting
    │   ├── Sessions
    │   ├── Profiles
    │   └── RADIUS Logs
    │
    ├── 06. NETWORK
    │   │
    │   ├── Router / MikroTik
    │   │   ├── Router Inventory
    │   │   ├── Router Detail
    │   │   ├── API Connection
    │   │   ├── RouterOS
    │   │   ├── Interfaces
    │   │   ├── Routing
    │   │   └── Health
    │   │
    │   ├── VPN & Tunneling
    │   │   ├── ZeroTier
    │   │   ├── WireGuard
    │   │   ├── Jeroti
    │   │   ├── Routier
    │   │   ├── L2TP/IPsec
    │   │   └── IPsec
    │   │
    │   ├── Private Network
    │   └── Network Diagnostics
    │
    ├── 07. MONITORING
    │   ├── System
    │   ├── RADIUS
    │   ├── Router
    │   ├── NAS
    │   ├── OLT
    │   ├── Traffic
    │   ├── Sessions
    │   └── Alerts
    │
    ├── 08. AUDIT LOGS
    │   ├── System Logs
    │   ├── Login Events
    │   ├── Administrator Activity
    │   ├── Network Activity
    │   ├── Provisioning Activity
    │   └── Security Events
    │
    ├── 09. SYSTEM
    │   ├── General Settings
    │   ├── Database
    │   ├── Redis
    │   ├── RADIUS
    │   ├── Network
    │   ├── Notifications
    │   ├── Backup
    │   └── Diagnostics
    │
    ├── 10. NAS
    │   ├── NAS Inventory
    │   ├── Add NAS
    │   ├── NAS Detail
    │   ├── RADIUS Client
    │   └── NAS Health
    │
    ├── 11. OLT / FTTH
    │   ├── OLT
    │   ├── PON
    │   ├── ONU / ONT
    │   ├── ODP
    │   ├── Fiber Topology
    │   └── Optical Monitoring
    │
    ├── 12. GENIEACS
    │   ├── Devices
    │   ├── Device Detail
    │   ├── Online / Offline
    │   ├── Provisioning
    │   ├── Configuration
    │   └── Tasks
    │
    ├── 13. BILLING
    │   ├── Billing Dashboard
    │   ├── Packages
    │   ├── Invoices
    │   ├── Payments
    │   ├── Outstanding
    │   └── Payment History
    │
    ├── 14. MITRA / RESELLER
    │   ├── Mitra Dashboard
    │   ├── Reseller
    │   ├── Balance
    │   ├── Top Up
    │   ├── Voucher
    │   ├── Sales
    │   └── Transactions
    │
    ├── 15. USERS & ACCESS
    │   ├── Users
    │   ├── Administrator
    │   ├── Roles
    │   ├── Permissions
    │   ├── Sessions
    │   └── Capability
    │
    └── 16. PROFILE
        ├── Administrator Profile
        ├── Security
        ├── Password
        ├── Active Sessions
        └── Activity
11. Reseller Application
RESELLER APPLICATION
│
├── Dashboard Reseller
├── Penjualan Voucher
├── Manajemen Pelanggan
├── Saldo
├── Top Up
├── Komisi
├── Laporan
├── Downline
└── Riwayat Transaksi
Scope Reseller dibatasi ke pelanggan, transaksi, voucher, saldo, komisi dan downline sesuai permission/capability yang diberikan ISP.

12. Sales Application
SALES APPLICATION
│
├── Dashboard Sales
├── Prospek
├── Registrasi Pelanggan
├── Penjualan Langsung
├── Package / Service
├── Target
├── Pencapaian
├── Komisi
├── Laporan Penjualan
└── Tracking Aktivitas
13. Mitra Application
MITRA APPLICATION
│
├── Dashboard Mitra
├── Pelanggan Mitra
├── Project / Area
├── Skema Kerja Sama
├── Contract
├── Revenue Sharing
├── Laporan
├── Monitoring Aktivitas
├── Dokumen
└── Komunikasi dengan ISP
14. Teknisi Application
TEKNISI APPLICATION
│
├── Dashboard Teknisi
├── Tiket
├── Penugasan
├── Customer Detail
├── Lokasi Pelanggan
├── Device Information
├── Instalasi
├── Aktivasi
├── Maintenance
├── Troubleshooting
├── Network Diagnostics
├── Monitoring Perangkat
├── Laporan Lapangan
├── Tracking Lokasi
├── Dokumentasi Foto
└── Completion Evidence
Struktur Role di Dalam Satu ISP
Administrator, Reseller, Sales, Mitra dan Teknisi berada di tenant ISP yang sama. Mereka dibedakan oleh role, permission, capability dan UX aplikasi.

                       TENANT ISP
                           │
                           ▼
                    TENANT DATA
                           │
                           ▼
                       TENANT RBAC
                           │
      ┌────────────┬───────┼───────┬────────────┐
      │            │       │       │            │
      ▼            ▼       ▼       ▼            ▼
Administrator   Reseller  Sales   Mitra      Teknisi
Application    Application App     App          App
Shared tenant data meliputi customer, subscription, billing, network, device, ticket, transaction dan audit data sesuai domain dan permission masing-masing.

Universal Request Flow
Setiap request dari semua role application wajib melewati boundary server-side berikut.

USER
 │
 ▼
APPLICATION
 │
 ├── Administrator
 ├── Reseller
 ├── Sales
 ├── Mitra
 └── Teknisi
 │
 ▼
AUTHENTICATION
 │
 ▼
TENANT RESOLVER
 │
 ▼
TENANT STATUS CHECK
 │
 ▼
TENANT CONTEXT
 │
 ▼
ROLE
 │
 ▼
PERMISSION
 │
 ▼
CAPABILITY
 │
 ▼
DOMAIN SERVICE
 │
 ▼
DATABASE / INFRASTRUCTURE
 │
 ▼
AUDIT
 │
 ├── Log
 ├── Metric
 └── Security Event
 │
 ▼
RESPONSE
Frontend menu visibility tidak boleh digunakan sebagai authorization boundary. Authorization wajib ditegakkan server-side.

IV. Runtime & Continuous Operations
Runtime Service Flow
Subscriber / Pelanggan
        │
        ▼
NAS / MikroTik
        │
        ▼
RADIUS Server
        │
        ▼
Network
        │
        ├── Router
        ├── VPN / Tunnel
        └── NAS
        │
        ▼
OLT / FTTH
        │
        ▼
ONU / ONT
        │
        ▼
GenieACS
        │
        ▼
Billing
        │
        ▼
Monitoring / Audit / Alerts
        │
        ▼
Internet / Service Delivery
Continuous operations mencakup monitoring, audit logs, background jobs, backup/restore/DR, security, alerting, incident handling, release, migration dan rollback.

V. End-to-End Workflows
PHASE 1 — Platform Development
Owner Requirement
        │
        ▼
Canonical Blueprint 15/15
        │
        ▼
Map ke Module
        │
        ▼
Existing Engineering Foundation
        │
        ▼
Engineering Capability Gate
        │
        ├── Quality
        ├── Security
        ├── Isolation
        ├── Migration
        ├── Recovery
        └── Observability
        │
        ▼
Implementation
        │
        ▼
Testing
        │
        ▼
CI Verification
        │
        ▼
Development
PHASE 2 — ISP Registration
Developer Dashboard
       │
       ▼
Create ISP
       │
       ├── ISP Identity
       ├── Owner
       ├── Contact
       ├── Package
       ├── License
       ├── Features
       └── Limits
       │
       ▼
Validation
       │
       ├── FAIL
       │    └── Correct Data
       │
       └── PASS
            │
            ▼
     Provisioning Request
PHASE 3 — Automatic Tenant Provisioning
Provisioning Request
        │
        ▼
Generate Tenant ID / UUID
        │
        ▼
Register Tenant
        │
        ▼
Create Schema
        │
        ▼
Run Migration
        │
        ▼
Seed Baseline
        │
        ▼
Create Owner
        │
        ▼
Create Initial RBAC
        │
        ▼
Apply License / Entitlement
        │
        ▼
Provisioning Verification
        │
        ├── DB
        ├── Schema
        ├── Migration
        ├── Seed
        ├── Owner
        ├── RBAC
        ├── Isolation
        └── Portal
        │
        ▼
        PASS?
       ┌──┴──┐
       │     │
      NO    YES
       │     │
       ▼     ▼
    FAILED  READY
       │
       ├── Retry
       ├── Resume
       └── Rollback
PHASE 4 — Portal Activation
Tenant READY
      │
      ▼
Portal Activation
      │
      ├── Enable Admin Portal
      ├── Activate Tenant Route
      ├── Apply Access Policy
      ├── Enable Allowed Applications
      └── First Login State
      │
      ▼
Portal ACTIVE
PHASE 5 — First Login
ISP Owner
    │
    ▼
Login
    │
    ▼
Authentication
    │
    ▼
Tenant Resolver
    │
    ▼
first_login = true
    │
    ▼
First Login Wizard
    │
    ├── Verify Owner
    ├── Password
    ├── Security
    ├── ISP Profile
    ├── Branding
    ├── System Setup
    └── Network Setup
    │
    ▼
setup_complete = true
    │
    ▼
ISP Administrator Dashboard
    │
    ▼
16 Administrator Modules
PHASE 6 — Administrator Creates Operational Users
Administrator
      │
      ▼
15. Users & Access
      │
      ├── Create Administrator
      ├── Create Reseller
      ├── Create Sales
      ├── Create Mitra
      └── Create Teknisi
      │
      ▼
Role Assignment
      │
      ▼
Permission Assignment
      │
      ▼
Capability Assignment
      │
      ▼
Application Access
PHASE 7 — Customer Acquisition via Sales
Sales
  │
  ▼
Sales Application
  │
  ▼
Create Prospect
  │
  ▼
Registrasi Pelanggan
  │
  ▼
Customer Created
  │
  ▼
Package / Subscription
  │
  ▼
Need Installation?
  │
  ├── NO ──► Service Activation
  │
  └── YES
       │
       ▼
Create Installation Ticket
       │
       ▼
Assign Technician
PHASE 8 — Teknisi Installation Flow
Installation Ticket
       │
       ▼
Teknisi Application
       │
       ▼
Accept Assignment
       │
       ▼
Customer Location
       │
       ▼
Installation
       │
       ├── Router
       ├── ONU / ONT
       ├── Cable
       ├── ODP
       └── Device Setup
       │
       ▼
Network Provisioning
       │
       ├── NAS
       ├── OLT
       ├── GenieACS
       └── Subscriber Binding
       │
       ▼
RADIUS Test
       │
     ┌─┴─┐
     │   │
   FAIL PASS
     │   │
     ▼   ▼
 Diagnose Activation
     │   │
   Retry ▼
       Documentation
           │
           ├── Photo
           ├── Location
           ├── Device
           └── Report
           │
           ▼
      Ticket COMPLETE
PHASE 9 — RADIUS Runtime
Subscriber
    │
    ▼
Router / NAS
    │
    ▼
RADIUS Access-Request
    │
    ▼
Resolve NAS / Tenant
    │
    ▼
Tenant Context
    │
    ▼
Credential Lookup
    │
    ▼
Policy
    │
    ├── Profile
    ├── Bandwidth
    ├── IP
    ├── Quota
    └── Status
    │
    ▼
Access-Accept / Reject
    │
    ▼
User Session
    │
    ▼
Accounting
    │
    ├── Start
    ├── Interim
    └── Stop
PHASE 10 — Billing Runtime
Customer
   │
   ▼
Subscription
   │
   ▼
Billing Cycle
   │
   ▼
Invoice
   │
   ▼
Payment Status
   │
   ├── PAID
   │     │
   │     ▼
   │   ACTIVE
   │
   └── UNPAID
         │
         ▼
      Grace Period
         │
         ▼
       Warning
         │
         ▼
      Suspension
         │
         ▼
      CoA / Disconnect
Reactivation flow:

Payment
   │
   ▼
Verify
   │
   ▼
Reactivation
   │
   ▼
CoA / Reconnect
   │
   ▼
ACTIVE
PHASE 11 — Reseller Workflow
Administrator
      │
      ▼
Create Reseller
      │
      ▼
Assign Limit / Permission
      │
      ▼
Reseller Application
      │
      ├── Top Up
      ├── Voucher Stock
      ├── Sales
      ├── Customer
      ├── Downline
      └── Transactions
      │
      ▼
Commission / Revenue
      │
      ▼
Billing / Audit
PHASE 12 — Mitra Workflow
Administrator
      │
      ▼
Create Mitra
      │
      ▼
Define Partnership
      │
      ├── Area
      ├── Contract
      ├── Customer Scope
      ├── Revenue Share
      └── Capability
      │
      ▼
Mitra Application
      │
      ├── Customer
      ├── Project
      ├── Activity
      └── Report
      │
      ▼
Revenue Sharing
      │
      ▼
Settlement / Audit
PHASE 13 — Monitoring & Incident Flow
Runtime
  │
  ├── API
  ├── RADIUS
  ├── PostgreSQL
  ├── Redis
  ├── NAS
  ├── Router
  ├── OLT
  └── GenieACS
  │
  ▼
Metrics + Logs
  │
  ▼
Monitoring
  │
  ▼
Anomaly / Failure?
  │
  ├── NO
  │    └── Continue
  │
  └── YES
       │
       ▼
     Alert
       │
       ▼
    Incident
       │
       ├── Diagnose
       ├── Correlate Logs
       ├── Determine Severity
       ├── Remediation
       └── Audit
       │
       ▼
    Resolution
PHASE 14 — Background Jobs
Scheduler
   │
   ├── Accounting Cleanup
   ├── Session Reaper
   ├── Billing Run
   ├── Invoice Generation
   ├── Suspension Sweep
   ├── License Expiry
   ├── Backup
   ├── Migration Fan-out
   └── Notification Jobs
   │
   ▼
Worker Pool
   │
   ▼
Execution
   │
   ├── SUCCESS
   │
   └── FAILED
         │
         ▼
       Retry
         │
         ▼
      Backoff
         │
         ▼
Dead-Letter Queue
PHASE 15 — Backup / Restore / DR
Backup flow:

Production Data
      │
      ▼
Backup
      │
      ├── Global
      └── Per Tenant
      │
      ▼
Integrity Verification
      │
      ▼
Encrypted Offsite Storage
Recovery flow:

Failure
   │
   ▼
Determine Scope
   │
   ├── Single Tenant
   │      │
   │      ▼
   │   Tenant Restore
   │
   └── Platform
          │
          ▼
       Full Restore
          │
          ▼
        Verify
          │
          ▼
        Resume
PHASE 16 — Platform Release / Upgrade
Tenant provisioning dan platform upgrade adalah dua lifecycle berbeda.

Developer Change
      │
      ▼
Canonical Module Scope
      │
      ▼
Implementation
      │
      ▼
Unit / Integration Tests
      │
      ▼
Security Gate
      │
      ▼
Development
      │
      ▼
Staging / Preview
      │
      ▼
Smoke Test
      │
      ▼
Promotion Gate
      │
      ▼
Production Readiness
      │
      ▼
Production
      │
      ▼
Migration Orchestrator
      │
      ├── Tenant A
      ├── Tenant B
      ├── Tenant C
      └── Tenant N
      │
      ▼
Post-Deploy Verification
Provisioning = membuat tenant baru
Migration    = memperbarui tenant yang sudah ada
VI. ISP Lifecycle State Model
NEW
 │
 ▼
REGISTERED
 │
 ▼
PROVISIONING
 │
 ├──────── FAILED
 │            │
 │            ├── Retry
 │            ├── Resume
 │            └── Rollback
 │
 ▼
READY
 │
 ▼
ACTIVATED
 │
 ▼
FIRST LOGIN
 │
 ▼
CONFIGURED
 │
 ▼
ACTIVE
 │
 ├──────────────► MAINTENANCE
 │                     │
 │                     ▼
 │                   ACTIVE
 │
 ├──────────────► SUSPENDED
 │                     │
 │                     ▼
 │                   ACTIVE
 │
 └──────────────► OFFBOARDING
                       │
                       ▼
                    ARCHIVED
VII. Standard Work Execution Loop
Alur berikut menjadi acuan kerja setiap pekerjaan baru.

OWNER INSTRUCTION / REQUIREMENT
             │
             ▼
MAP KE CANONICAL MODULE 01–15
             │
             ▼
CHECK CURRENT REPOSITORY STATE
             │
             ▼
CHECK EXISTING IMPLEMENTATION
             │
             ▼
COORDINATE OWNERSHIP / FILE SCOPE
             │
             ▼
DEFINE ACCEPTANCE CRITERIA
             │
             ▼
DEFINE ENGINEERING CAPABILITY GATES
             │
             ├── Security
             ├── Testing
             ├── Tenant Isolation
             ├── Migration
             ├── Recovery
             └── Observability
             │
             ▼
CREATE ISOLATED BRANCH / PR
             │
             ▼
IMPLEMENT SMALLEST SAFE SLICE
             │
             ▼
UNIT TEST
             │
             ▼
INTEGRATION TEST
             │
             ▼
SECURITY TEST
             │
             ▼
MIGRATION / ROLLBACK TEST
             │
             ▼
EXACT-HEAD CI
             │
             ▼
CROSS-WORKSTREAM REVIEW
             │
             ▼
ALL GATES PASS?
        ┌────┴────┐
        │         │
       NO        YES
        │         │
        ▼         ▼
      FIX      MERGE TO
      /RETEST   DEVELOPMENT
                  │
                  ▼
           STAGING / PREVIEW
                  │
                  ▼
              SMOKE TEST
                  │
                  ▼
           PROMOTION READY?
             ┌────┴────┐
             │         │
            NO        YES
             │         │
             ▼         ▼
           HOLD      OWNER
                   AUTHORIZATION
                        │
                        ▼
                    PRODUCTION
                        │
                        ▼
               POST-DEPLOY VERIFY
                        │
                  ┌─────┴─────┐
                  │           │
                PASS         FAIL
                  │           │
                  ▼           ▼
               CLOSE       ROLLBACK
                  │           │
                  └─────┬─────┘
                        ▼
                 UPDATE EVIDENCE
VIII. Working Rules
Developer Blueprint 15/15 tetap menjadi domain development yang digunakan dalam arsitektur ini.
Setiap pekerjaan baru wajib memiliki mapping Module 01–15 sebelum implementasi.
Existing Engineering Foundation dipertahankan dan disejajarkan; tidak dibuang tanpa alasan teknis.
Engineering Capability Matrix adalah hardening gate lintas module.
Development/platform dan Administrator ISP adalah boundary berbeda.
Administrator ISP hanya menguasai tenant ISP-nya.
Administrator, Reseller, Sales, Mitra dan Teknisi berada dalam tenant ISP yang sama.
Tenant Resolver dan server-side RBAC wajib untuk seluruh role application.
Provisioning harus idempotent, observable, retryable, resumable dan rollback-capable.
First Login Wizard adalah konfigurasi tenant, bukan installer platform.
Perubahan database wajib mempertimbangkan migration, rollback, backup/restore dan tenant fan-out.
Dangerous action wajib memiliki guard dan audit.
Ownership dan file scope harus ditentukan sebelum implementasi.
Pekerjaan paralel tidak boleh memiliki overlap file/scope yang tidak terkoordinasi.
Koordinasi GPT/DevOps ↔ CLOUD/CLAUDE dilakukan melalui Issue #37 untuk pekerjaan lintas workstream.
Development menjadi integration target; staging/preview menjadi verification target.
Production promotion hanya dilakukan setelah gate lulus dan authorization owner diberikan.
Definition of Done berbasis evidence: test, exact-head CI, security, migration/integration evidence dan dokumentasi sesuai risiko scope.
IX. End-to-End Architecture Summary
A-RADIUS DEVELOPMENT
Developer Blueprint 15/15
        │
        ▼
Existing Engineering Foundation
        │
        ▼
Engineering Capability Matrix
        │
        ▼
Developer Dashboard
        │
        ▼
ISP Registration
        │
        ▼
Automatic Provisioner
        │
        ├── Tenant
        ├── Schema
        ├── Migration
        ├── Seed
        ├── Owner
        ├── RBAC
        ├── Entitlement
        └── Verification
        │
        ▼
Portal Activation
        │
        ▼
Tenant Resolver
        │
        ▼
ISP Administrator
        │
        ▼
First Login Wizard
        │
        ▼
16 Administrator Modules
        │
        ├───────────────────────────────────────┐
        │              │             │          │
        ▼              ▼             ▼          ▼
 Administrator      Reseller        Sales      Mitra
 Application        Application     App         App
        │              │             │          │
        └──────────────┴──────┬──────┴──────────┘
                              │
                              ▼
                        Teknisi App
                              │
                              ▼
                         SAME TENANT
                              │
                              ▼
                RADIUS / NETWORK / BILLING
                              │
                              ▼
                 MONITORING / AUDIT / ALERT
                              │
                              ▼
                     ISP OPERASIONAL
Blueprint Usage
README ini adalah acuan kerja end-to-end untuk struktur A-RADIUS, lifecycle tenant/ISP, role applications, runtime flow, dan ritme pengerjaan. Setiap pekerjaan selanjutnya harus membaca struktur ini dari atas ke bawah, menentukan domain/module, boundary tenant, capability gate, file ownership, acceptance criteria, evidence, dan target promotion sebelum implementasi dimula
