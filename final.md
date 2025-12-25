# 台灣旅遊小幫手 - 實體關聯圖 (ERD) 與資料庫結構

本文件描述了系統中各個資料檔案之間的關聯結構，包含使用者資料、行程歷史紀錄以及景點資料庫。

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
