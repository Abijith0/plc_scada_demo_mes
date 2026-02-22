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

### 1️⃣ Hardware & Network Architecture (Distributed PC Setup)
This diagram outlines the physical hardware separation, proving network routing capability between the field OT layer and the supervisory IT layer.

```mermaid
graph TD
    subgraph PC 1: Field Operations (OT)
        PLC[CODESYS Virtual PLC]
        OPC[Kepware OPC UA Server]
        PLC -- Raw Tag Data --> OPC
    end

    subgraph PC 2: Supervisory Control (IT)
        IG[Ignition 8.3 Gateway]
        DB[(MySQL Database)]
        HMI[Perspective Web Client]
        
        IG -- Exception Logging --> DB
        IG -- WebSockets / HTTPS --> HMI
    end

    OPC -- OPC UA Protocol via LAN --> IG
