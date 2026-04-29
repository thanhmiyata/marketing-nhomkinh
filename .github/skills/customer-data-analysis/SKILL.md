---
name: customer-data-analysis
description: 'Analyze customer CSV data for marketing, ICP, segmentation, referral potential, upsell potential, pricing bands, local area demand, and offer selection. Use when working with customer lists, CRM exports, lead sheets, or old sales data for nhom kinh marketing.'
argument-hint: 'Paste the CSV path or ask for ICP, segmentation, pricing bands, referral leads, or area insights.'
user-invocable: true
---

# Customer Data Analysis

Use this skill when the task starts from raw customer data and the goal is to make a marketing decision, not just clean a spreadsheet.

This project already points to a practical pattern:
- dominant segment: `Nha dan`
- core product: `cua nhom Xingfa`
- useful filters: area, project type, deal value, source, note quality

## When To Use

- The user wants ICP or persona extraction from a CSV.
- The user wants to identify high-value zones or project types.
- The user wants to find referral-heavy customers or upsell candidates.
- The user wants to estimate pricing bands for content or offers.
- The user wants to decide what segment should receive ads first.

## Procedure

1. Read the CSV header and infer the business fields.
2. Normalize obvious variations in area names, project types, and product labels.
3. Split customers into working segments:
   - project type
   - deal value band
   - area
   - source
   - note sentiment: quick close, slow budget, referral potential, upsell potential
4. Identify the primary ICP by checking frequency plus revenue concentration.
5. Identify secondary segments worth separate messaging.
6. Extract proof assets from notes:
   - fast close
   - high trust
   - referral behavior
   - premium budget
7. Recommend one main offer and one follow-up campaign angle.
8. Output a concise decision memo using the template in [customer segmentation template](./assets/customer-segmentation-template.md).

## Rules

- Prefer actionable segmentation over perfect statistical analysis.
- Use note text as signal for trust, referral likelihood, budget sensitivity, and speed to close.
- Do not mix premium villa messaging with mass-market house-owner messaging unless the user asks for two funnels.
- Call out data issues explicitly when fields are missing or inconsistent.

## Deliverables

- ICP summary
- top geographic clusters
- value bands
- offer recommendation
- referral list
- content implications

## References

- [analysis checklist](./references/analysis-checklist.md)
- [customer segmentation template](./assets/customer-segmentation-template.md)