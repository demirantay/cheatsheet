# Programming Syllabus

Classes:
- [Backend](#backend)
- [DBA](#dba)
- [Software Design](#software-design)
- [DevOps](#devops)
- [CompSci](#compsci)

## `Backend`

- [ ] ALT - Python
- [ ] Testing
- [ ] Backend Framework
- [ ] Relational Databases
- [ ] NoSQL Databases
- [ ] API
  - [ ] JSON, REST, authentication OAuth, Basic, Token, JWT
- [ ] Caching
  - [ ] CDN, Client side, Server side
- [ ] Web sockes
- [ ] Web servers basic
- [ ] Search Engine
- [ ] GraphQL
- [ ] Scalability (Migration strategies, Horizontal and Vertical scaling, Building with Observibilty
- [ ] Web Security (basic)

## `DBA`

- [ ] Basic RDBMS terms 
  - [ ] Object Model (data types, columns, rows, tables, schemas, databases, queries)
  - [ ] Relation Model (domains, attributes, tuples, relations, constraints, NULL)
  - [ ] Database high-level concepts: ACID, MVCC, transactions, write-ahead log, query processing
- [ ] How to install postgresql
  - [ ] using pacakge managers (apt, yum)
  - [ ] using docker
  - [ ] managing postgres server `systemd` (start, stop, restart, reload)
  - [ ] managing postgres server `pg_ctl`
  - [ ] connecting using `psql`
  - [ ] deploy database service in cloud env (aws, digital ocean, linode)
- [ ] SQL Concepts
  - [ ] Basic data types
  - [ ] DML queries: querying data, modifying data, filtering data, joining tables
  - [ ] Advanced topics: transactions, CTE, subqueries, lateral join, grouping, set operations
  - [ ] DDL queries: managing tables and schemas (create, alter, drop)
  - [ ] Import and export data using `COPY`
- [ ] Configuring Postgres 
  - [ ] postgresql.conf (resource usage, write-ahead log, checkpoints, cost-based vacuum, replication, query planner, reporting, logging .etc)
- [ ] Postgres Security concepts
  - [ ] Authentication models, roles, pg_hba.conf, SSL
  - [ ] Object priviliges: grant, revoke, default priviliges
  - [ ] Advacned topics: row-level security, seleniux
 - [ ] Infrastructure DBA:
    - [ ] Replication: streaming replication, logical replication
    - [ ] Backup/recovery tools: builtin (pg_dump), 3rd part (barman), backup validation procedures
    - [ ] Upgrading procedures (pg_upgrade, logical_replication)
    - [ ] Connection Pooling (Pgbouncer, alternatives .etc)
    - [ ] Monitoring (prometheus .etc)
    - [ ] Cluster management tool (patroni)
    - [ ] Load balancing and service discovery (haproxy, consul)
    - [ ] deploying on kuberneetes
    - [ ] resource usage and provisioning, capacity planning
- [ ] Automating Routines
  - [ ] Shell scripts (bash, python)
  - [ ] configuration management (ansible)
- [ ] Application DBA skills
  - [ ] Migrations (practical patterns, tools: liquibase)
  - [ ] Data import/export, bulk loading and processing 
  - [ ] Queues (skytools pgq)
  - [ ] Data partioning and sharding patterns
  - [ ] Database normalization and normal forms
- [ ] Postgresql Advanced Topics
   - [ ] Low level internals (process and memory architecture, vacuum processing, buffer management, lock managemen, system catalog)
   - [ ] Fine-grained tuning (per-user, per-database settings, Workload-dependant tuning (OLTP, OLAP, HTAP))
   - [ ] Advanced SQL topics (pl/pgsql, procedures  and function triggers, aggregation, recursive CTE)
- [ ] Troubleshooting
   - [ ] Operating system tools (top, sysstat, iotop)
   - [ ] postgres system views (pg_stat_activity, pg_stat_statements)
   - [ ] postgres tools (pgcenter)
   - [ ] query analyzing (explain, depesz, PEV, tensor)
   - [ ] log analyzing (pgBadger, ad-hoc analyizng)
   - [ ] external tracing/profiling tools: gdb, strace, ebpf
   - [ ] troubleshooting methods: USE, RED, Golden signals
 - [ ] SQL Optimization techincs
   - [ ] Indexes, and their use cases: B-tree, Hash, gist, gin, brin
   - [ ] sql query patterns
   - [ ] sql schema design patterns
 - [ ] DB Architect Skills
   - [ ] Postgres forks and extensions
   - [ ] RDBMS general benfits and limitations
   - [ ] differences between nosql and rdbms

## `Software Design`

 - [ ] Clean Code
 - [ ] Programming Paradigms
    - [ ] Structured Programming
    - [ ] Functional Programming
    - [ ] Object Oriented Programming
 - [ ] Object Oriented Programming
    - [ ] Model-Driven Design (domain models, anemic models .etc.)
    - [ ] Paradigm Features (abstract classes, scope visibilty .etc.)
    - [ ] Primary Principles (inheritance, polymorphism, abstraction)
 - [ ] Design Principles
    - [ ] Composition over inheritance
    - [ ] Encapsulate what varies
    - [ ] Program against abstractions
    - [ ] Hollywood principle
    - [ ] SOLID, DRY, YAGNI
 - [ ] Design Patterns
    - [ ] GoF Design Patterns
    - [ ] PoSA Patterns
 - [ ] Architectual Principles
    - [ ] component principles
    - [ ] policy vs detail
    - [ ] coupling vs cohesion
    - [ ] boundaries
 - [ ] Architectual Styles
    - [ ] Messaging (event driven, publish-subscribe)
    - [ ] Distributed (client-server, peer to peer)
    - [ ] Structural (component-based, monolithic, layered)
 - [ ] Architectual Patterns
    - [ ] SOA
    - [ ] CQRS
    - [ ] Domain driven design
    - [ ] model view controller
    - [ ] microservices
    - [ ] blackboard pattern
    - [ ] microkernel
    - [ ] serverless architecture
    - [ ] message queues/ streams
    - [ ] event sourcing
 - [ ] Enterprise Patterns
    - [ ] DTOs
    - [ ] Identity Maps
    - [ ] Use Cases
    - [ ] Repositories
    - [ ] Mappers
    - [ ] Transaction Script
    - [ ] Commands / Queries
    - [ ] Value Objects
    - [ ] Domain Models
    - [ ] Entitites
    - [ ] ORMs

## `DevOps`

- [ ] ALT - Go
- [ ] OS Concepts
  - [ ] process management, threads and concurrency, sockets, posix basics, networking concepts
  - [ ] IO management, virtualization, memory/storage, file systems, startup management, service management
  - [ ] Practical - Linux (Ubuntu, CentOS, RHEL)
- [ ] Terminal
  - [ ] Bash Scripting + Vim/Nano/Emacs
  - [ ] Tools (text manipulation tools
  - [ ] Tools (process monitoring
  - [ ] Tools (network)
  - [ ] Tools (system performance
- [ ] Networking
  - [ ] Security, Protocols (HTTP, HTTPS, FTP, SSL/TLS, SSH, Port Forwarding
  - [ ] Web servers (Nginx, Apache)
  - [ ] How to set up a (Reverse Proxy, Forward Proxy, Caching Server, Load Balancer, Firewall)
- [ ] Infrastructure
  - [ ] Containers (Docker)
  - [ ] Configuration Management (Ansible)
  - [ ] Container Orchestration (Kubernetees)
  - [ ] Provisioning (Terraform)
- [ ] CI/CD (Gitlab, Github, Jenkins)
- [ ] Monitoring
  - [ ] Infrastructure (Prometheus, Grafana)
  - [ ] Application (Jaeger, New relic)
  - [ ] Logs Management (Elastic Stack)
- [ ] Cloud
  - [ ] AWS
  - [ ] Linode, Digital Ocean
- [ ] Cloud Design Patterns
  - [ ] Availability
  - [ ] Data Management
  - [ ] Design and Implementation
  - [ ] Management and Monitoring

## `Compsci`

> This page is on another page

- [ ] Programming 
- [ ] Computer Architecture 
- [ ] Algorithms and Data Strcutures
- [ ] Operating Systems 
- [ ] Computer Networking 
- [ ] Databases 
- [ ] Languages and Compilers 
- [ ] Graphics
- [ ] Artifical Intelligence
