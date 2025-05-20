# PgCat!

## Introduction

### 1. **Read/Write Splitting**

-   Automatically routes `SELECT` queries to **read replicas** and `INSERT`, `UPDATE`, `DELETE`, and other write queries to the **primary node**.
    
-   Uses SQL parsing to determine the type of query.
    
-   Helps in scaling read-heavy workloads by offloading read operations to replicas.
    

### 2. **Connection Pooling**

-   Reduces the overhead of establishing new connections by pooling and reusing existing ones.
    
-   Supports per-user and per-database connection pools.
    
-   Configurable pool sizes and timeouts.
    

### 3. **Replica Lag Awareness**

-   PgCat can track replication lag of read replicas and **avoid sending queries to lagging replicas**.
    
-   Helps ensure data freshness for read queries when consistency is important.
    

### 4. **Automatic Failover Handling**

-   Supports automatic failover to a new primary if the existing primary becomes unavailable.
    
-   Can integrate with external tools or services (like Patroni or custom scripts) for cluster failover management.
    

### 5. **Multi-Tenant and Multi-Database Support**

-   Can serve multiple databases and tenants from a single PgCat instance.
    
-   Each pool configuration can have its own primary and replicas.
    

### 6. **Config Reloading Without Restart**

-   Configuration can be reloaded on the fly (e.g., adding/removing replicas or changing settings) **without restarting PgCat**.
    
-   Makes it suitable for dynamic environments like Kubernetes.
    

### 7. **Lightweight and Fast**

-   Written in **Rust** for performance and safety.
    
-   Designed to handle thousands of concurrent connections efficiently.
    

### 8. **Observability**

-   Exposes Prometheus-compatible **metrics**.
    
-   Logging and monitoring features help track query distribution, pool usage, and replica health.

# Run
```
docker compose up
```

## Connection
**postgres_primary connection**

``
psql -U postgres -h 127.0.0.1 -d postgres
``

*** postgres_replica ****

```
psql -U replicator -h 127.0.0.1 -d postgres
```


*** pg_cat cnnection ****

```
 psql -h 127.0.0.1 -p 6432 -U test
```
