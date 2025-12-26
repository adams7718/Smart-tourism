# 台灣旅遊小幫手 - 系統架構與資料庫設計文件
### 1.整理使用的api，資料筆數，適用什麼架設網站(架構)，網頁功能，製作理由
### 2.確認使用哪一個版本的python，Gemini
## 1. 實體關聯圖 (Entity Relationship Diagram)

此圖表展示了使用者資料 (`users_db.json`)、行程紀錄 (`history_db.json`) 與 景點資料庫 (`taiwan_attractions.csv`) 之間的關聯性。

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
```
## 2. 資料流向
```mermaid
graph TD
    User["使用者瀏覽器"] <-->|HTTP/WebSocket| Server["Streamlit 伺服器 (Python)"]
    
    subgraph App ["Streamlit 應用程式(trip.py)"]
        direction TB
        UI["UI 渲染與路由 (Presentation)"]
        Logic["業務邏輯與狀態管理 (Logic)"]
        Data["檔案讀寫模組 (Data)"]
    end
    
    Server --- UI
    UI --- Logic
    Logic --- Data
    
    Logic <-->|"API Request"| Gemini["Google Gemini AI"]
    Logic <-->|"API Request"| Meteo["Open-Meteo 天氣"]
    
    Data <-->|"Read/Write"| JSON["JSON 資料庫 (Users/History)"]
    Data <-->|"Read Only"| CSV["CSV 景點資料 (Attractions)"]
```


## 3. 網頁架構圖 
```mermaid
graph LR
    %% 設定為由左至右 (LR)，這是最能減少交錯的佈局
    %% 使用 basis 曲線讓線條平滑
    %% 【修改處】新增 themeVariables 來放大連線文字字體 (fontSize: 22px)
    %%{init: {'flowchart': {'curve': 'basis', 'rankSpacing': 80, 'nodeSpacing': 20}, 'themeVariables': {'fontSize': '22px'}}}%%

    %% --- 樣式設定 (保留您喜歡的大字體與高對比色) ---
    classDef user fill:#ff80ab,stroke:#880e4f,stroke-width:4px,color:#000,font-size:24px,font-weight:bold;
    classDef ui fill:#81d4fa,stroke:#01579b,stroke-width:3px,color:#000,font-size:22px,font-weight:bold;
    classDef logic fill:#fff59d,stroke:#f9a825,stroke-width:3px,color:#000,font-size:22px,font-weight:bold;
    classDef db fill:#e0e0e0,stroke:#424242,stroke-width:3px,color:#000,font-size:22px,font-weight:bold;
    classDef api fill:#ffcc80,stroke:#ef6c00,stroke-width:3px,color:#000,font-size:22px,font-weight:bold;

    %% --- 節點佈局 (由左至右) ---

    %% 1. 最左側：使用者
    User((使用者)):::user

    %% 2. 中間：應用程式 (分為上、中、下三層以對齊右側資源)
    subgraph Streamlit_App [Streamlit Application]
        direction TB
        
        %% 上層：認證
        subgraph Top_Layer [ ]
            direction TB
            Auth[🔐 認證模組]:::logic
            Session[💾 Session State]:::logic
        end
        
        %% 中層：核心操作
        subgraph Middle_Layer [ ]
            direction TB
            UI[💻 前端介面 UI]:::ui
            AI_Planner[🤖 AI 行程規劃]:::logic
            Manual_Planner[🗺️ 手動規劃]:::logic
        end

        %% 下層：輸出處理
        subgraph Bottom_Layer [ ]
            direction TB
            Weather_Mod[☁️ 天氣預報]:::logic
            Output[📊 輸出呈現]:::ui
        end
    end

    %% 3. 最右側：資源 (資料庫與API混合排列，只為了對齊線條)
    subgraph Resources [後端資源與 API]
        direction TB
        
        %% 上層資源 (對應 Auth)
        UserDB[(User DB)]:::db
        
        %% 中層資源 (對應 Planner)
        GeminiAPI[✨ Gemini API]:::api
        CSV[(景點 CSV)]:::db
        HistDB[(History DB)]:::db
        
        %% 下層資源 (對應 Weather/Output)
        OpenMeteo[☔ Weather API]:::api
        GoogleMaps[📍 Google Maps]:::api
    end

    %% --- 連線關係 (由上而下順序定義，確保平行) ---

    %% 上層連線 (Login Flow)
    User ==> Auth
    Auth <==> UserDB
    UI -.->|狀態| Session

    %% 中層連線 (Core Flow)
    User ==> UI
    UI ==> AI_Planner
    UI ==> Manual_Planner
    
    %% 核心邏輯對接右側資源 (盡量平行)
    AI_Planner ==>|提示詞| GeminiAPI
    AI_Planner ==>|檢索| CSV
    Manual_Planner ==>|搜尋| CSV
    AI_Planner ==>|儲存| HistDB
    
    %% 下層連線 (Output Flow)
    AI_Planner ==> Weather_Mod
    Manual_Planner ==> Weather_Mod
    
    Weather_Mod ==>|查詢資料| OpenMeteo
    Weather_Mod ==> Output
    
    Output ==>|生成連結| GoogleMaps

    %% 補充連線 (跨層級)
    UI ==>|歷史紀錄| HistDB
    Manual_Planner ==> Output

    %% 全域連線樣式：黑色、加粗(4px)
    %% 注意：原本您的代碼是 stroke:#FFF (白色)，在白底會看不見。
    %% 若您是深色背景請維持 #FFF，若在白底請改為 #000。
    linkStyle default stroke:#FFF,stroke-width:4px;
```
