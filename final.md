## 實體關聯圖 (Entity Relationship Diagram)

```mermaid
erDiagram
    direction LR
    %% 使用者資料庫 (users_db.json)
    USER {
        string email PK "使用者 Email (Key)"
        string password "密碼"
        string nickname "暱稱"
    }

    %% 行程歷史紀錄 (history_db.json - 外層)
    TRIP {
        string id PK "行程 ID"
        string email FK "關聯使用者 Email"
        string trip_name "行程名稱"
        int days "天數"
        string mode "規劃模式 (ai/manual)"
        string timestamp "建立時間"
        json data "行程明細列表 (Array)"
    }

    %% 行程明細 (history_db.json - data 內部結構)
    ITINERARY_ITEM {
        int Day "第幾天"
        int Order "當日順序"
        string Place FK "景點名稱 (關聯 Attraction)"
        string City "城市"
        string District "行政區"
        string Transport "交通方式"
        string StayTime "停留時間 (Optional)"
    }

    %% 台灣景點資料 (taiwan_attractions.csv)
    ATTRACTION {
        string ID PK "景點編號"
        string ScenicSpotName UK "景點名稱"
        string City "縣市"
        string District "行政區"
        string Address "地址"
        string Description "詳細介紹"
        string OpenTime "開放時間"
        string Class_1_2_3 "分類"
        string Position "經緯度資訊 (JSON)"
        string Picture "圖片資訊 (JSON)"
    }

    %% 關係定義
    USER ||--o{ TRIP : "擁有 (Owns)"
    TRIP ||--|{ ITINERARY_ITEM : "包含 (Contains)"
    ITINERARY_ITEM }|..|| ATTRACTION : "參考 (Refers to)"

---

### 2. 系統架構圖 (System Architecture) - 複製此段

```markdown
## 🏗️ 系統架構圖 (System Architecture)

```mermaid
graph TD
    %% 定義樣式
    classDef user fill:#f9f,stroke:#333,stroke-width:2px;
    classDef ui fill:#e1f5fe,stroke:#0277bd,stroke-width:2px;
    classDef logic fill:#fff9c4,stroke:#fbc02d,stroke-width:2px;
    classDef db fill:#e0e0e0,stroke:#616161,stroke-width:2px;
    classDef api fill:#ffe0b2,stroke:#f57c00,stroke-width:2px;

    %% 節點定義
    User((使用者)):::user
    
    subgraph Streamlit_App [Streamlit Application (b.py)]
        UI[💻 前端介面 UI]:::ui
        Auth[🔐 認證模組<br/>Login/Signup]:::logic
        Session[💾 Session State<br/>狀態管理]:::logic
        
        subgraph Core_Features [核心功能]
            AI_Planner[🤖 AI 行程規劃<br/>Gemini Pro]:::logic
            Manual_Planner[🗺️ 手動規劃<br/>資料庫搜尋]:::logic
            Weather_Mod[☁️ 天氣預報 &<br/>穿搭建議]:::logic
        end
        
        Output[📊 輸出呈現<br/>HTML卡片/圖表/文字檔]:::ui
    end

    subgraph Data_Storage [本地資料存儲]
        CSV[(taiwan_attractions.csv<br/>景點資料庫)]:::db
        UserDB[(users_db.json<br/>使用者資料)]:::db
        HistDB[(history_db.json<br/>行程歷史)]:::db
    end

    subgraph External_Services [外部 API 服務]
        GeminiAPI[✨ Google Gemini API<br/>LLM 生成]:::api
        OpenMeteo[☔ Open-Meteo API<br/>天氣資訊]:::api
        GoogleMaps[📍 Google Maps<br/>導航連結]:::api
    end

    %% 關係連線
    User -->|登入/註冊| Auth
    User -->|輸入需求/操作| UI
    UI --> Session
    
    Auth <-->|讀寫| UserDB
    
    UI -->|AI 模式| AI_Planner
    UI -->|手動模式| Manual_Planner
    UI -->|查看紀錄| HistDB
    
    AI_Planner -->|Prompt| GeminiAPI
    AI_Planner -->|查詢| CSV
    Manual_Planner -->|查詢| CSV
    
    AI_Planner -->|儲存結果| HistDB
    Manual_Planner -->|儲存結果| HistDB
    
    AI_Planner --> Weather_Mod
    Manual_Planner --> Weather_Mod
    Weather_Mod -->|查詢經緯度| OpenMeteo
    
    Weather_Mod --> Output
    AI_Planner --> Output
    Manual_Planner --> Output
    
    Output -->|生成連結| GoogleMaps
