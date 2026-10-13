---
name: atlas-cloud-audit-spend
description: Check Atlas Cloud account balance, daily model usage and daily model cost through the read-only Billing Public API.
api: atlas-cloud:atlas-cloud-billing-public-api
operations:
  - get_public_v1_balance
  - get_public_v1_model_usage
  - get_public_v1_model_costs
generated: 2026-10-13
method: generated
source: https://www.atlascloud.ai/docs/public-api
---
# Audit Atlas Cloud spend

1. Call `get_public_v1_balance` for the current balance and credit grant summary.
2. Call `get_public_v1_model_usage` with `start_date` and `end_date` for daily usage buckets; page with `limit` (1 to 1000, default 100).
3. Call `get_public_v1_model_costs` with the same range; use repeated `group_by[]` parameters (comma-delimited values are rejected).
4. On `429 rate_limit_error`, honour the `Retry-After` header.
