## 工作項目：基於 UI 流程的實體關係圖 (ERD) 設計

**設計依據**：本資料庫設計係依據前述六張介面規劃圖（Landing Page, Login, Dashboard, Chat, Itinerary View）之輸入與輸出欄位進行正規化分析。

### 資料庫實體關係圖 (ER Diagram)

erDiagram
    %% 1. 使用者與認證
    USER {
        int user_id PK
        string email
        string password_hash
        string username
        string oauth_provider
        string oauth_uid
        datetime created_at
    }

    %% 2. AI 對話紀錄
    CHAT_SESSION {
        int session_id PK
        int user_id FK
        string title
        datetime created_at
    }

    CHAT_MESSAGE {
        int message_id PK
        int session_id FK
        string sender_type
        text content
        datetime sent_at
    }

    %% 3. 行程總表
    ITINERARY {
        int itinerary_id PK
        int user_id FK
        string title
        date start_date
        date end_date
        string status
        datetime created_at
    }

    %% 4. 行程細項
    ITINERARY_ITEM {
        int item_id PK
        int itinerary_id FK
        int spot_id FK
        int day_number
        time start_time
        time end_time
        string note
        boolean is_alternative
    }

    %% 5. 景點資料庫
    SPOT {
        int spot_id PK
        string name
        string description
        string tags
        float location_lat
        float location_lng
        string image_url
    }

    %% 關係定義 (修正語法錯誤)
    USER ||--o{ CHAT_SESSION : "initiates"
    CHAT_SESSION ||--o{ CHAT_MESSAGE : "contains"
    USER ||--o{ ITINERARY : "owns"
    ITINERARY ||--|{ ITINERARY_ITEM : "consists_of"
    SPOT ||--o{ ITINERARY_ITEM : "is_added_to"
