# Subscriber 360 Analytics

End-to-end telecom subscriber intelligence: Churn, ARPU, Usage, Network Quality, Billing Health, Interactions & AI-powered insights — entirely within your Snowflake account.

## Overview

The Subscriber 360 Analytics Accelerator is a turnkey Snowflake Native App that transforms your fragmented subscriber data into actionable telecom intelligence. Connect your existing subscriber, usage, billing, network, and interaction tables to a polished, interactive Streamlit dashboard spanning nine analytics modules. No data leaves your environment, and no external tools or credentials are required.

## Why Subscriber 360?

Telecom operations teams often struggle with scattered KPIs, disconnected churn signals, and manual reporting across multiple systems. Subscriber 360 solves this by delivering a unified subscriber intelligence platform that runs natively on your Snowflake warehouse. It combines real-time churn risk scoring with ARPU analysis, network quality correlation, and Cortex AI-powered insights to surface intelligence that typically requires dedicated CRM/BI platforms — at a fraction of the cost and complexity.

## What You Get

**Executive Summary** — Monitor portfolio-level subscriber count, churn rate, retention, ARPU, NPS, at-risk revenue, collection rates, and FCR with month-over-month deltas. Revenue concentration analysis by segment with Pareto insights.

**Subscriber Profile** — Complete 360-degree drill-down for any subscriber: demographics, usage, billing, network quality, risk scoring, and AI-generated retention recommendations.

**Churn Analysis** — Track churn and retention rates by segment. Identify top churn drivers through behavioral analysis. View at-risk subscribers ranked by composite risk score with segment×risk heatmaps.

**ARPU & Revenue** — Analyze average revenue per user by segment, plan type, and customer type. Identify upsell opportunities, top revenue contributors, and roaming revenue impact.

**Usage Analytics** — Monitor voice, SMS, data, roaming, and international usage patterns. Identify top consumers and segment-level usage distributions.

**Network & SLA** — Evaluate tower-level quality scores, download/upload speeds, latency, dropped calls, and SLA compliance by region. Correlate network quality with churn rates.

**Billing & Service** — Track collection rates, late payments, unpaid bills, and cost-to-serve by segment. Analyze service interaction volumes, FCR, escalation rates, and handling times by channel and issue category.

**Trends & Cohorts** — Monthly revenue trends, churn/retention trajectories, NPS evolution, and cohort retention analysis by activation month.

**AI/ML Predictions** — Cortex AI-powered Q&A, segment-level next-best-action recommendations, real-time alerts, and Snowflake ML time-series forecasting for churn, revenue, and subscriber growth.

## Required Input References (5 Tables)

| Reference | Description | Required Columns |
|-----------|-------------|-----------------|
| DIM_SUBSCRIBER | Subscriber master | SUBSCRIBER_SK, FULL_NAME, SEGMENT, STATUS, CUSTOMER_TYPE, TENURE_MONTHS, REGION, PLAN_TYPE, IS_CURRENT, ACTIVATION_DATE |
| FACT_USAGE | Daily usage records | SUBSCRIBER_SK, VOICE_MINUTES, SMS_COUNT, DATA_USAGE_GB, INTERNATIONAL_MINS, ROAMING_FLAG, USAGE_DATE |
| FACT_BILLING | Billing records | SUBSCRIBER_SK, BILLED_AMOUNT, PAID_AMOUNT, LATE_FEES, OVERAGE_CHARGES, DISCOUNTS, PAYMENT_STATUS, BILLING_DATE |
| FACT_NETWORK | Network metrics | TOWER_ID, REGION, DOWNLOAD_MBPS, UPLOAD_MBPS, LATENCY_MS, DROPPED_CALLS, DATA_OUTAGES, SIGNAL_STRENGTH_DBM |
| FACT_INTERACTIONS | Support records | SUBSCRIBER_SK, CHANNEL, ISSUE_CATEGORY, RESOLUTION_STATUS, HANDLING_MINUTES, NPS_SCORE |

## How the Pipeline Works

After binding the 5 references, `BUILD_PIPELINE()` automatically generates 15 Gold KPI tables:

| Generated Table | Description |
|----------------|-------------|
| kpi_subscriber_health | Composite subscriber profile with churn risk scoring |
| kpi_churn | Churn/retention rates by segment |
| kpi_arpu | Revenue metrics per subscriber |
| kpi_usage_summary | Aggregated usage per subscriber |
| kpi_network_performance | Tower-level quality scores |
| kpi_billing_health | Collection rates and payment status |
| kpi_interaction_analytics | Service interaction metrics by channel |
| kpi_segment_summary | Segment-level KPI rollup |
| kpi_monthly_trends | Time-series revenue and churn trends |
| kpi_cohort_retention | Cohort-based retention analysis |
| kpi_region_churn | Regional churn correlated with network quality |
| kpi_segment_risk_revenue | At-risk revenue by segment and tier |
| kpi_cost_to_serve | Segment profitability analysis |
| kpi_sla_availability | SLA compliance by region |
| pipeline_run_log | Pipeline execution audit trail |

## Permissions

- **SELECT** on 5 bound Silver tables
- **IMPORTED PRIVILEGES ON SNOWFLAKE DB** — for Cortex AI Complete function (AI/ML tab)
- All Gold tables are created internally. No data leaves your account.

## Version History

| Version | Date | Notes |
|---------|------|-------|
| 1.0.0 | 2026-05-25 | Initial marketplace release |
