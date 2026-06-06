# Meta Ad Performance Analysis Dashboard

A comprehensive Power BI dashboard for analyzing advertising campaign performance across Facebook and Instagram, tracking KPIs from awareness to conversions.

**Developed by:** Vishal Agarwal  


---

## 📋 Table of Contents

- [Business Objective](#business-objective)
- [Project Scope](#project-scope)
- [Key Performance Indicators (KPIs)](#key-performance-indicators-kpis)
- [Dataset Overview](#dataset-overview)
- [Data Model](#data-model)
- [Dashboard Visualizations](#dashboard-visualizations)
- [Key Insights & Recommendations](#key-insights--recommendations)
- [Getting Started](#getting-started)
- [Project Structure](#project-structure)

---

## 📁 Project Structure
meta-ad-performance-analysis/
│
├── Report/
│   └── Meta Ad Dashboard.pbix
│
├── dataset/
│   ├── ad_events.csv
│   ├── ads.csv
│   ├── campaigns.csv
│   └── users.csv
│
└── README.md

---

## 🎯 Business Objective

The business requires a **performance tracking report** for advertising campaigns running on Facebook and Instagram. This dashboard provides visibility into:

- **Campaign Reach** – How many people saw the ads (Impressions)
- **Engagement** – How users interacted with ads (Clicks, Shares, Comments)
- **Conversions** – Purchases and conversion rates
- **Budget Utilization** – Cost analysis and ROI optimization

**Goals:**
1. Identify the most effective platform (Facebook vs Instagram)
2. Track campaign ROI and optimize budget allocation
3. Understand audience engagement patterns
4. Enable data-driven marketing decisions

---

## 📊 Project Scope

### ✅ In Scope
- Campaigns running on **Facebook and Instagram only**
- Paid ads performance metrics
- User demographic and geographic analysis
- Time-based and seasonal trends
- Ad creative type performance

### ❌ Out of Scope
- Other platforms (Messenger, Audience Network)
- Organic engagement (unpaid interactions)
- Non-advertising content analysis

---

## 📈 Key Performance Indicators (KPIs)

### Basic Metrics

| KPI | Definition | Formula | Use Case |
|-----|-----------|---------|----------|
| **Impressions** | Number of times ads were displayed | COUNT(event_type = 'Impression') | Measure reach |
| **Clicks** | Number of times users clicked ads | COUNT(event_type = 'Click') | Measure engagement intent |
| **Shares** | Number of times ads were shared | COUNT(event_type = 'Share') | Identify viral engagement |
| **Comments** | Number of user comments on ads | COUNT(event_type = 'Comment') | Understand user sentiment |
| **Purchases** | Number of purchases after seeing ads | COUNT(event_type = 'Purchase') | Track conversions |

### Derived Metrics

| KPI | Definition | Formula | Use Case |
|-----|-----------|---------|----------|
| **Engagements** | Total user interactions | Clicks + Shares + Comments | Engagement volume |
| **CTR** (Click-Through Rate) | % of impressions that resulted in clicks | (Clicks ÷ Impressions) × 100 | Ad effectiveness |
| **Engagement Rate** | % of impressions that resulted in engagements | (Engagements ÷ Impressions) × 100 | Overall ad appeal |
| **Conversion Rate** | % of clicks that resulted in purchases | (Purchases ÷ Clicks) × 100 | Funnel efficiency |
| **Purchase Rate** | % of impressions that resulted in purchases | (Purchases ÷ Impressions) × 100 | Conversion from reach |

### Cost Metrics

| KPI | Definition | Formula | Use Case |
|-----|-----------|---------|----------|
| **Total Budget** | Total spend allocated to campaigns | SUM(campaigns.total_budget) | Cost analysis |
| **Avg. Budget per Campaign** | Average budget allocation per campaign | Total Budget ÷ Campaign Count | Budget distribution |

---

## 📁 Dataset Overview

The dataset represents **Meta Ads Performance Data** covering campaigns, ads, user demographics, and ad interaction events. It consists of 4 tables:

- **ads** – Ad metadata (platform, type, targeting)
- **campaigns** – Campaign budget and timeframe
- **users** – User demographics and interests
- **ad_events** – Event-level logs (impressions, clicks, purchases)

---

## 🗂️ Data Model

**Star Schema** architecture with dimension tables filtering to the fact table:

```
    ┌────────┐      ┌──────────┐      ┌────────┐
    │  ads   │      │campaigns │      │ users  │
    │        │      │          │      │        │
    └───┬────┘      └────┬─────┘      └────┬───┘
        │                │                 │
        │                │                 │ 
        ▼                ▼                 ▼
    ┌──────────────────────────────────────────┐
    │          ad_events (Fact)                │
    │     (Event-level interactions)           │
    └──────────────────────────────────────────┘
```

**Relationships:**
- `ads.ad_id` → `ad_events.ad_id`
- `campaigns.campaign_id` → `ads.campaign_id`
- `users.user_id` → `ad_events.user_id`

---

## 📊 Dashboard Visualizations

| Visual | Type | Purpose | Key Insight |
|--------|------|---------|-------------|
| **Target Gender** | Donut Chart | Segment performance by gender | Females (43%) engage more than males (22%) |
| **Target Age Group** | Bar Chart | Compare engagement by age | 18–30 age group drives majority of interactions |
| **Country** | Map | Geographic reach analysis | US & UK: high Impression and high Purchase Rate |
| **Calendar Month** | Heat Map | Identify seasonal trends | Engagement spikes on event/promotion dates |
| **Weekly Trend** | Stacked Column | Compare ad type performance over weeks | Track which formats perform best over time |
| **Hourly Trend** | Area Chart | User activity patterns by hour | Peak engagement: afternoon & evening hours |
| **Ad Type** | Matrix | Compare formats (Video, Image, Carousel, Story) across platforms | Video ads: highest CTR and conversion rate |

---

## 💡 Key Insights & Recommendations

### Current Performance Summary For Facebook

**Funnel Overview:**
- **216K Impressions** → **25.4K Clicks** (CTR: **11.76%** – well above industry average)
- **13.56% Engagement Rate** (strong user interaction)
- **1.3K Purchases** (Conversion Rate: **5.21%** from clicks)
- **Purchase Rate: 0.61%** from impressions

### Key Findings

1. **Strong Awareness & Engagement, Low Conversion**
   - Ads excel at generating awareness and engagement
   - Significant drop-off from engagement to purchase indicates funnel leak
   - **Action:** Optimize landing pages, implement retargeting, strengthen offers

2. **Target Audience Profile**
   - **Demographics:** Young females, primarily 18–30 years old
   - **Geography:** US & UK
   - **Action:** Tailor campaigns by segment and region.

3. **Best Performing Ad Formats**
   - **Story ads:** Highest **71.5K** IMPR & **5.52%** CR for Story.
   - **Video ads:** 0.62% PR WITH 45.8K IMPR, **Strong Chances for PR Improvments.**
   - **Image & Carousel ads:** Similat Metrics, Lag slightly in PR & conversion efficiency.
   - **Action:** Increase budget allocation to Video and Stories. Need Improvments in Image & Carousel

4. **Optimal Timing**
   - Peak engagement: **Morning and Evening hours**
   - Consistent weekly performance with event-driven spikes
   - **Action:** Schedule ads during high-engagement windows; leverage event-based campaigns


### Recommendations

1. **Conversion Optimization** – Focus on landing page UX, checkout flow, and post-click experience
2. **Retargeting Strategy** – Capture engaged users who don't convert with targeted follow-ups
3. **Ads Improvment** - Image & Carousel ads have low metrics need Improvment in both
4. **Budget Reallocation** – Shift spend toward Video and Story ads (proven higher ROI)
5. **Audience Refinement** – Double-down on young female demographic in US & UK
6. **Time-Based Optimization** – Concentrate budget in morning/evening hours
7. **Geographic Segmentation** – Different messaging and offers for high-volume vs. high-value regions

---

## 🚀 Getting Started

### Prerequisites
- **Power BI Desktop** or Power BI Service subscription
- Access to the Meta Ads dataset (4 tables: ad_events, ads, campaigns, users)
- Basic understanding of Power BI data modeling and DAX

### Dataset Import Steps

1. **Load the 4 CSV/Excel files:**
   - `ad_events.csv` (Fact table)
   - `ads.csv` (Dimension)
   - `campaigns.csv` (Dimension)
   - `users.csv` (Dimension)

2. **Create relationships in Power BI:**
   - `ad_events.ad_id` → `ads.ad_id`
   - `ad_events.user_id` → `users.user_id`
   - `ads.campaign_id` → `campaigns.campaign_id`

3. **Create calculated columns (if not in source data):**
   - `day_of_week` = FORMAT([timestamp], "dddd")
   - `time_of_day` = IF(HOUR([timestamp])>=5 AND HOUR([timestamp])<12,"Morning", IF(HOUR([timestamp])>=12 AND HOUR([timestamp])<17,"Afternoon","Evening"))`
   - `duration_days` = campaigns[end_date] - campaigns[start_date]

4. **Build visualizations** following the Dashboard Visualizations section above

5. **Add slicers** for dynamic metric selection and date filtering

---





