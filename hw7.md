## 工作項目：智慧旅遊實體關係圖 (ERD)

**目標**：向使用者與開發團隊展示智慧旅遊系統內部的資料庫設計邏輯。
**說明**：下圖描述了使用者 (User)、景點 (Attraction)、行程 (Itinerary) 與評論 (Review) 之間的關聯。

### 資料庫實體關係圖 (ER Diagram)

```mermaid
erDiagram
    %% 使用者資料表
    USER {
        int user_id PK
        string username
        string email
        string preferences "偏好標籤"
    }

    %% 景點資料表
    ATTRACTION {
        int spot_id PK
        string name
        string category "自然/人文/美食"
        string location "GPS座標"
        float rating
    }

    %% 行程規劃資料表
    ITINERARY {
        int plan_id PK
        int user_id FK
        date start_date
        date end_date
        string status "規劃中/已完成"
    }

    %% 評論資料表
    REVIEW {
        int review_id PK
        int user_id FK
        int spot_id FK
        string comment
        int score
        date created_at
    }

    %% 關係定義
    USER ||--o{ ITINERARY : "規劃 (Plans)"
    USER ||--o{ REVIEW : "撰寫 (Writes)"
    ATTRACTION ||--o{ REVIEW : "收到 (Receives)"
    ITINERARY }|--|{ ATTRACTION : "包含 (Contains)"
