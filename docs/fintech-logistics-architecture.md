# Fintech + Logistics Reference Architecture

Production-grade reference architecture for a **Laravel + Vue + Flutter** stack in a **fintech + logistics hybrid** domain.

**Blog post:** [Fintech + Logistics Architecture: A Production-Grade Blueprint](../blog/fintech-logistics-architecture.html)

## Overview

A deployable blueprint with:
- Bounded contexts and service decomposition
- DDD layered modular structure (Laravel)
- Event-driven coordination (Kafka / RabbitMQ)
- Operational concerns (security, observability, deployment)

## System Topology

```
[ Vue.js Web ]       [ Flutter Mobile ]
         │
         ▼
     API Gateway (BFF optional)
         │
 ┌──────────────────────────────────────┐
 │            Microservices             │
 │ Identity | User | Wallet | Payment   │
 │ Shipment | Routing | Notification   │
 └──────────────────────────────────────┘
         │
         ▼
 Event Bus (Kafka / RabbitMQ)
         │
         ▼
 Infrastructure (DBs, Cache, Storage)
```

## Bounded Contexts

| Context | Type | Description |
|---------|------|-------------|
| Wallet / Ledger | Fintech Core | Double-entry bookkeeping, transactions |
| Payment | Fintech | External gateways, payment lifecycle |
| Shipment | Logistics Core | Shipment lifecycle aggregate |
| Routing | Logistics Core | Optimization logic |
| Tracking | Logistics | Event ingestion (GPS, updates) |
| Identity, Notification, Reporting | Supporting | Cross-cutting concerns |

**Rule:** Each bounded context = independent Laravel service.

## Laravel Service Structure (DDD)

```
app/
├── Domain/          # Pure PHP, no Eloquent
├── Application/     # Commands, Handlers, UseCases
├── Infrastructure/  # Persistence, Messaging, External
└── Interfaces/      # Http, Console
```

## Key Principles

1. **Model the domain, not the database**
2. **Keep aggregates small and strict**
3. **Communicate via events, not calls**
4. **Isolate bounded contexts completely**
5. **Invest heavily in core domain (ledger + routing)**

## Critical Rules

- No Eloquent models in Domain
- No business logic in Controllers
- Never update balances directly—derive from transactions
- External models NEVER leak into Domain (Anti-Corruption Layer)
