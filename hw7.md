```mermaid
erDiagram
    %% 1. 使用者與認證 (對應圖 1, 2, 3)
    USER {
        int user_id PK "12"
        string email "UK, 必填, 登入帳號"
        string password_hash "加密後的密碼"
        string username "顯示名稱 (王小明)"
        string oauth_provider "Google/FB"
        string oauth_uid "第三方ID"
    }

   %% 2. AI 對話紀錄 (對應圖 4)
    CHAT_SESSION {
        int session_id PK "1"
        int user_id FK "12"
        string title "對話摘要"
        datetime created_at "12/30"
    }

   CHAT_MESSAGE {
        int message_id PK "1"
        int session_id FK "1"
        string sender_type "User/AI"
        text content "訊息內容"
        datetime sent_at "12/30"
    }

    %% 3. 行程總表 (對應圖 3, 5, 6)
    ITINERARY {
        int itinerary_id PK "1"
        int user_id FK "12"
        string title "行程標題 台北半日遊"
        date start_date "12/31"
        date end_date "12/31"
        string status "規劃中/已確認/警示中(圖6)"
        datetime created_at "12/30"
    }

    %% 4. 行程細項 (對應圖 5, 6 的時間軸與卡片)
    ITINERARY_ITEM {
        int item_id PK"1"
        int itinerary_id FK "1"
        int spot_id FK "1321"
        int day_number "第幾天 (Day 1)"
        time start_time "13:00"
        time end_time "22:00"
        string note "備註 (午餐/室內備案)"
        boolean is_alternative "是否為備案 (圖6)"
    }

    %% 5. 景點資料庫 (對應圖 5 的地圖與資訊)
    SPOT {
        int spot_id FK "1321" 
        string City "臺北市"
        string District "信義區"
        string ScenicSpotName PK "景點名稱 (台北101)"
        string Address "臺北市信義區信義路五段7號"
        string description " 台北101購物中心為地上5樓……"
        string Class "標籤 (地標景觀類)"
        string image_url "http://www.tonyhuang39.com/tony/tony1299/20171110_01.JPG"
    }

  %% 關聯定義
    USER ||--o{ CHAT_SESSION : "發起 (Initiates)"
    CHAT_SESSION ||--o{ CHAT_MESSAGE : "包含 (Contains)"
    USER ||--o{ ITINERARY : "擁有 (Owns)"
    ITINERARY ||--|{ ITINERARY_ITEM : "由...組成 (Consists of)"
    SPOT ||--o{ ITINERARY_ITEM : "被加入 (Is added to)"
