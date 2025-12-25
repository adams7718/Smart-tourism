# 台灣旅遊小幫手 - 系統資料庫架構 (System Architecture)

本文件詳細描述系統的資料實體、屬性及其關聯性。圖表採用橫向佈局以利閱讀。

## 實體關聯圖 (Class Diagram Style ERD)

> 註：採用 Class Diagram 語法以強制呈現橫向 (Left-to-Right) 排列，符合 GitHub Mermaid 渲染標準。

```mermaid
classDiagram
    direction LR

    %% 使用者 (Users)
    class USER {
        <<Collection: users_db.json>>
        +String email (PK)
        +String password
        +String nickname
    }

    %% 行程紀錄 (Trip History)
    class TRIP {
        <<Collection: history_db.json>>
        +String id (PK)
        +String email (FK)
        +String trip_name
        +Int days
        +String mode
        +String timestamp
        +List data
    }

    %% 行程節點 (Itinerary Items)
    class ITINERARY_ITEM {
        <<Nested Object>>
        +Int Day
        +Int Order
        +String Place (FK)
        +String City
        +String District
        +String Transport
        +String Date [Optional]
        +String Temp [Optional]
        +String Rain [Optional]
        +String Note [Optional]
    }

    %% 景點資料 (Attractions)
    class ATTRACTION {
        <<Table: taiwan_attractions.csv>>
        +Int ID (PK)
        +String ScenicSpotName (UK)
        +String City
        +String District
        +String Address
        +String Description
        +String OpenTime
        +String Phone
        +String TravelInfo
        +String WebsiteUrl
        +String Class1
        +String Class2
        +String Class3
        +String Keyword
        +String ParkingInfo
        +JSON Position
        +String Level
        +JSON Picture
        +String MapUrl
        +String DescriptionDetail
        +String IndoorOutdoor "室內室外分類"
    }

    %% 關聯定義
    USER "1" --> "*" TRIP : "Has History"
    TRIP "1" *-- "*" ITINERARY_ITEM : "Contains"
    ITINERARY_ITEM ..> ATTRACTION : "Refers to (by Name)"
