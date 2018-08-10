---
path: "/about/what-is-the-platform/data-store"
date: "2018-05-03"
title: "Data Store"
---

## Data Store
The HCA Data Store is a multi-site replicated storage system containing all raw data and metadata, and certain forms of derived data, materialized and stored as flat files. Its goals are ensuring simple and direct data access for downstream consumers, notifying users of repository changes, and synchronizing data across multiple sites. 

### Design principles
- Data deposited in the Data Store will flow from the HCA ingestion service, which is solely responsible for data and metadata schemas, naming, accessioning, and validation.
- All access between the ingestion service and the Data Store is via well-defined APIs, ensuring modularity and separation of concerns.
- The Data Store will manage data replication across official HCA object stores. There will be at least 2 public cloud stores, and additional public or on-premise stores may be added over time.
- At the lowest level, all data and metadata will be stored as a set of identical objects, invariant across cloud stores, and synchronization across cloud providers will thus depend on synchronization of this set of objects.
- A common object layer across clouds will provide homogeneity and aid portability of analysis and access between different clouds, and allow cloud-independent data indexes to be built that link to each of the data copies on each cloud. 
- The public reference atlas will not require authenticated access, but access control and authentication may be required for some subsets of data.
- It will be possible for any third party to add their own external pipeline or portal (as a consumer), or add a data replica, and receive timely updates about changes to the Data Store.
- Data change notification and replication will be rapid (e.g. significantly less than a day).
- Tracking of data access via analytics will help determine data usage patterns to minimize costs (e.g. which data needs to be highly available or placed cold storage).
- All data and metadata will be explicitly versioned; the Data Store is effectively append-only except in emergency circumstances. Updates to data will generally require new submissions, and updates to metadata will manifest as a series of files or explicit file versions.

### Functional components
- The Producer API is primarily responsible for receiving data directly from the authenticated ingestion service. 
- The Consumer API provides read-only access to data, via cloud-native APIs. Access is subject to authentication and access control for subsets of data where required. The Consumer API also provides webhook change notification (e.g. GitHub-style), allowing downstream computation to be triggered, and ensuring that all secondary and tertiary analysis tools can be reliably and rapidly updated as changes occur.
- The Object synchronization system and the Pub/Sub bus and replication logs systems are private subsystems providing synchronization and change notification infrastructure across distributed object stores, and they communicate with both consumer and producer APIs.
- The Object store(s) are the multiple S3-like object stores on public and/or private clouds.
