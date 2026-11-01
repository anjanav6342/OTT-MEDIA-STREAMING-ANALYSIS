# OTT / Media Streaming Analysis (Power BI)

An interactive Power BI dashboard that analyses viewer behaviour, subscriber health, content performance and device usage for an OTT (video streaming) platform. The report is built on a **star schema** with one fact table and six dimension tables, and covers **20,000 streaming sessions** from **Jan 2024 to Dec 2025**.

## Dashboard Preview

### 1. Overview
![Overview]
<img width="1332" height="747" alt="01-overview" src="https://github.com/user-attachments/assets/8ef08939-4de2-47ec-9ec7-83bc25db3990" />

### 2. Audience & Subscribers
![Audience and Subscribers]<img width="1332" height="750" alt="image" src="https://github.com/user-attachments/assets/272dcb7f-bb1f-4140-9181-bee9adc1cf28" />


### 3. Engagement Details
![Engagement Details]<img width="1337" height="748" alt="03-engagement-details" src="https://github.com/user-attachments/assets/03e4d128-e039-4b89-900d-8ba2fb4daf1f" />


### 4. Content Performance
![Content Performance]<img width="1335" height="752" alt="04-content-performance" src="https://github.com/user-attachments/assets/bd9519b2-2552-4480-935a-f8423840a082" />


## Business Questions Answered

- How much are users watching, and how does it change month to month?
- Which genres and titles drive the most watch time?
- How healthy is the subscriber base (churn, new signups, ARPU, revenue per plan)?
- Which age groups and plans have the most active users?
- Which devices and days of the week see the most engagement?
- How do content ratings (IMDb score) relate to completion rate?

## Key KPIs

| KPI | Value (full date range) |
|---|---|
| Churn Rate % | 11.0% |
| Monthly Recurring Revenue | about $12K |
| Total Active Users | 890 |
| Distinct Users (Viewers) | about 1K |
| Total Watch Hours | 16.93K |
| Churned Users | 110 |
| ARPU | $13.86 |
| Total Sessions | 20,000 |
| Avg Completion % | 0.57 (57%) |

## Key Insights

- **Thriller, Crime and Animation** are the top genres by watch minutes; Reality is the lowest.
- **Movies account for about 61%** of content watched and TV shows about 39%.
- **Premium plan generates the largest share of monthly recurring revenue (about 37%)**, followed by Standard (about 29%).
- **The 25-34 age group has the most active users**, followed by 35-44 and 18-24.
- **Smart TV is the most used device (6.1K sessions)**, followed by Mobile Phone (4.9K).
- **Watch time peaks on Monday and dips on Friday**, with a second rise on the weekend.
- Average completion is steady at about **57% across genres**, so genre alone does not strongly change how much of a title people finish.

## Data Model

Star schema with a single fact table at session level.

| Table | Type | Purpose |
|---|---|---|
| `Fact_StreamingActivity` | Fact | One row per streaming session: WatchMinutes, CompletionPct, UserRating |
| `Dim_Content` | Dimension | ContentKey, Title, ContentType (Movie / TV Show), Genre, ReleaseYear, MaturityRating (300 titles) |
| `Dim_Date` | Dimension | Date, MonthYear, WeekdayName |
| `Dim_User` | Dimension | User attributes, AgeGroup |
| `Dim_Subscription` | Dimension | PlanName (Annual Premium, Annual Standard, Basic with Ads, Mobile Only, Premium, Standard) |
| `Dim_Device` | Dimension | DeviceType (Smart TV, Mobile Phone, Laptop, Streaming Stick/Box, Tablet, Desktop, Game Console) |
| `Dim_Geography` | Dimension | Region |
| `measure_tbl` | Measures | Holds all DAX measures |

## DAX Measures (in `measure_tbl`)

Total Watch Minutes, Total Watch Hours, Total Sessions, Total Active Users, Distinct Users (Viewers), Distinct Titles Watched, Churned Users, Churn Rate %, New Signups, Monthly Recurring Revenue, ARPU, Avg Completion %, Completion Rate %, Avg IMDb Score (Watched).

## Report Pages

1. **Overview**: headline KPIs, watch minutes by month and by genre, Movie vs TV Show split.
2. **Audience & Subscribers**: churned users, new signups, ARPU, MRR by plan, active users by age group and plan.
3. **Engagement Details**: watch minutes by weekday, sessions by device type, title-level engagement table.
4. **Content Performance**: watch minutes by genre and title, IMDb score vs completion rate scatter, genre x content type matrix.

All pages include slicers for **Genre, Region, Plan Name and Date range**, plus page navigation buttons.

## Tools & Skills Used

- Power BI Desktop
- Power Query (data loading, promoted headers, type changes)
- Data modelling (star schema, relationships)
- DAX measures
- Data visualisation and dashboard design (KPI cards, slicers, navigation)

## Dataset

The dataset is loaded into the model and saved inside the `.pbix` file. 

- Fact_StreamingActivity.csv
- Dim_Content.csv
- Dim_Date.csv
- Dim_Device.csv
- Dim_Geography.csv
- Dim_Subscription.csv
- Dim_User.csv


> Source note: *(edit this line: for example, "Synthetic dataset generated for this project" or the Kaggle link and licence if you downloaded it.)*

## How to Open

1. Install [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (free, Windows).
2. Download `Ott_Media_project.pbix` from this repository.
3. Open it in Power BI Desktop and explore the four report pages.

## Repository Structure

```
OTT-MEDIA-STREAMING-ANALYSIS/
├── Ott_Media_project.pbix
├── OTT_Streaming_StarSchema.xlsx
├── README.md
└── .gitignore
```

## Author

**Anjana V** | [GitHub](https://github.com/anjanav6342)
