# 台灣旅遊小幫手 - 實體關聯圖

本文件為系統資料庫結構的橫向視圖，方便在寬螢幕上檢視各實體間的關聯。

```mermaid
classDiagram
    direction LR
    
    %% 使用者資料庫
    class USER {
        +string email (PK)
        +string password
        +string nickname
    }

    %% 行程歷史紀錄
    class TRIP {
        +string id (PK)
        +string email (FK)
        +string trip_name
        +int days
        +string mode
        +string timestamp
        +json data
    }

    %% 行程明細
    class ITINERARY_ITEM {
        +int Day
        +int Order
        +string Place (FK)
        +string City
        +string District
        +string Transport
        +string StayTime
    }

    %% 台灣景點資料
    class ATTRACTION {
        +string ID (PK)
        +string ScenicSpotName (UK)
        +string City
        +string District
        +string Address
        +string Description
        +string OpenTime
        +string Class_1_2_3
        +string Position
        +string Picture
    }

    %% 關係定義
    USER "1" --> "*" TRIP : 擁有 (Owns)
    TRIP "1" *-- "*" ITINERARY_ITEM : 包含 (Contains)
    ITINERARY_ITEM ..> ATTRACTION : 參考 (Refers to)
