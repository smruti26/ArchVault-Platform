# ArchVault-Platform
ArchVault-Platform
Multi-channel wealth management infrastructure — 7 architectural layers, 33 microservices, enterprise-grade security

Table of Contents

Overview
Architecture

Layer 1 — Client Layer
Layer 2 — API Gateway & Security
Layer 3 — Core Microservices


Tech Stack
Getting Started
Contributing
License


Overview
ArchVault is a full-stack wealth management platform designed for multi-persona access — from retail clients and mobile users to institutional investors and wealth advisors. The platform is built on a layered microservices architecture with enterprise-grade security, real-time data flows, and high-availability infrastructure.
Client Layer  →  API Gateway & Security  →  Core Microservices  →  ...

Architecture
The platform is organized into 7 layers containing 33 services, each responsible for a distinct domain of the wealth management lifecycle.
Layer 1 — Client Layer
Multi-channel user interfaces for different user personas.
ServiceDescriptionStackWeb PortalResponsive SPA for retail clients to view portfolios and execute tradesReact, TypeScript, TailwindMobile AppNative application for on-the-go portfolio monitoring and alertsReact Native, Swift, KotlinAdvisor DashboardComplex terminal for wealth managers managing multiple client portfoliosAngular, RxJS, AG GridInstitutional PortalHigh-density data portal for institutional investors with advanced analyticsReact, D3.js, WebSockets

Layer 2 — API Gateway & Security
Secure entry point and routing layer for all incoming requests.
ServiceDescriptionStackWAFWeb Application Firewall protecting against OWASP Top 10 and DDoSAWS WAF, CloudFlareAPI GatewayRoutes requests, handles SSL termination, and aggregates microservice responsesKong, Nginx, GraphQLIdentity (OAuth 2.0)Handles authentication, authorization, and SSO via OpenID ConnectOkta, KeyCloak, JWTRate LimiterThrottles incoming requests to protect downstream servicesRedis, Envoy

Layer 3 — Core Microservices
Business logic and domain services handling wealth management operations.
ServiceDescriptionPortfolio ManagementMaintains current positions, asset allocations, and performance trackingWealth AnalyticsCalculates performance metrics, attribution, and reportingOrder ManagementRoutes orders to execution venues, handles FIX protocolRisk AssessmentComputes Value at Risk (VaR), runs stress tests, and monitors exposureClient ManagementManages client profiles, KYC/AML status, and onboarding workflows

Additional layers (Data, Infrastructure, Observability, etc.) are documented in the Architecture Guide.


Tech Stack
Frontend

React / TypeScript / Tailwind CSS — Web Portal
React Native / Swift / Kotlin — Mobile App
Angular / RxJS / AG Grid — Advisor Dashboard
D3.js / WebSockets — Institutional Portal

API & Security

Kong / Nginx / GraphQL — API Gateway
AWS WAF / CloudFlare — Edge Security
Okta / KeyCloak / JWT — Identity & Access
Redis / Envoy — Rate Limiting & Proxy

Backend Services

Microservices architecture with domain-driven design
FIX protocol support for order routing
Real-time data flows via WebSockets and event streaming

Data Flows
ArchVault uses a layered data flow model:

Client Request
    │
    ▼
CloudFlare / AWS WAF  ←── DDoS & OWASP protection
    │
    ▼
API Gateway (Kong)    ←── SSL termination, routing, GraphQL aggregation
    │
    ▼
Identity (Okta/JWT)   ←── AuthN / AuthZ / SSO
    │
    ▼
Core Microservices    ←── Portfolio, Orders, Risk, Analytics, CRM
    │
    ▼
Data Layer            ←── Time-series DBs, event streams, cache

URL : https://smruti26.github.io/ArchVault-Platform/