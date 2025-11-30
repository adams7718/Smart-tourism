```mermaid
erDiagram
    %% 1. 使用者與認證 (對應圖 1, 2, 3)
    USER {
        int user_id PK
        string email "UK, 必填, 登入帳號"
        string password_hash "加密後的密碼"
        string username "顯示名稱 (王小明)"
        string oauth_provider "Google/FB (圖2)"
        string oauth_uid "第三方ID"
        datetime created_at
    }

   %% 2. AI 對話紀錄 (對應圖 4)
    CHAT_SESSION {
        int session_id PK
        int user_id FK
        string title "對話摘要"
        datetime created_at
    }

   CHAT_MESSAGE {
        int message_id PK
        int session_id FK
        string sender_type "User/AI"
        text content "訊息內容"
        datetime sent_at
    }

    %% 3. 行程總表 (對應圖 3, 5, 6)
    ITINERARY {
        int itinerary_id PK
        int user_id FK
        string title "行程標題 (台南古蹟...)"
        date start_date
        date end_date
        string status "規劃中/已確認/警示中(圖6)"
        datetime created_at
    }

    %% 4. 行程細項 (對應圖 5, 6 的時間軸與卡片)
    ITINERARY_ITEM {
        int item_id PK
        int itinerary_id FK
        int spot_id FK
        int day_number "第幾天 (Day 1)"
        time start_time "10:00"
        time end_time
        string note "備註 (午餐/室內備案)"
        boolean is_alternative "是否為備案 (圖6)"
    }

    %% 5. 景點資料庫 (對應圖 5 的地圖與資訊)
    SPOT {
        int spot_id PK
        string name "景點名稱 (赤崁樓)"
        string description
        string tags "標籤 (AI, 古蹟, 室內)"
        float location_lat "緯度 (Map Marker)"
        float location_lng "經度 (Map Marker)"
        string image_url
    }

  %% 關聯定義
    USER ||--o{ CHAT_SESSION : "發起 (Initiates)"
    CHAT_SESSION ||--o{ CHAT_MESSAGE : "包含 (Contains)"
    USER ||--o{ ITINERARY : "擁有 (Owns)"
    ITINERARY ||--|{ ITINERARY_ITEM : "由...組成 (Consists of)"
    SPOT ||--o{ ITINERARY_ITEM : "被加入 (Is added to)"
