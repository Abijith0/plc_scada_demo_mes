# Smart Factory MES  
## High-Performance SCADA & Industrial IoT Data Pipeline

---

## 🏭 Executive Summary

This project demonstrates a full-stack, bidirectional Industrial IoT (IIoT) architecture that bridges Operational Technology (OT) and Information Technology (IT).

A virtual PLC executes structured control logic. Data is standardized via OPC UA middleware, ingested by an Ignition 8.3 Gateway, logged using an optimized SQL Historian strategy, and visualized through a web-based High-Performance HMI designed according to ISA-101 standards.

The system simulates a scalable smart factory data pipeline aligned with Industry 4.0 architectural principles.

---

## 🛠 Technology Stack

| Layer | Technology |
|--------|------------|
| Control Layer | CODESYS (Virtual PLC) |
| Middleware | Kepware Server (OPC UA) |
| SCADA Gateway | Ignition 8.3 |
| Historian | MySQL (via Ignition SQL Historian) |
| Presentation Layer | Ignition Perspective (Web HMI) |

---

## 🏗 System Architecture

### 1️⃣ Network Architecture (OT → IT Data Flow)

```mermaid
graph TD
    subgraph Control Layer
        PLC[CODESYS Virtual PLC]
    end
    subgraph Middleware
        OPC[Kepware OPC UA Server]
    end
    subgraph SCADA Layer
        IG[Ignition 8.3 Gateway]
    end
    subgraph Storage Layer
        DB[(MySQL Database)]
    end
    subgraph Presentation Layer
        HMI[Perspective Web Client]
    end

    PLC -- Raw Tag Data --> OPC
    OPC -- OPC UA Protocol --> IG
    IG -- Exception Logging --> DB
    IG -- HTTPS / WebSockets --> HMI
