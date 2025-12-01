# 分鏡板(storyboard) 

## 圖 1：首頁 
![1](https://github.com/adams7718/Smart-tourism/blob/main/1.png)

## A. 輸入欄位 (Input Fields)

| 欄位名稱 (Field Name) | 資料型態 (Data Type) | 驗證規則 / 觸發行為 (Validation Rules / Triggered Actions) |
| :--- | :--- | :--- |
| **電子郵件 (Email)** | 字符串 (String) | 1. **必填**。2. 必須為有效 Email 格式。 |
| **密碼 (Password)** | 字符串 (String) | 1. **必填**。2. **👁 圖標**：切換顯示/隱藏。 |
| **登入 (Login)** | 按鈕 (Button) | 點擊：使用 Email 與密碼進行**身份驗證**，成功後導向首頁。 |
| **忘記密碼？ (Forgot Password?)** | 連結/按鈕 (Link/Button) | 點擊：導向**忘記密碼**流程頁面。 |
| **前往註冊 (Go to Register)** | 按鈕 (Button) | 點擊：導向**使用者註冊**頁面。 |

---
## B. 螢幕顯示欄位 (Output Fields)

| 欄位名稱 (Field Name) | 功能描述 (Description) |
| :--- | :--- |
| **🔒 使用者登入 (User Login)** | 頁面標題。 |
| **電子郵件 (Email)** | 電子郵件輸入框的標籤。 |
| **密碼 (Password)** | 密碼輸入框的標籤。 |
| **👁 圖標 (Eye Icon)** | 切換密碼內容顯示/隱藏。 |
---


## 圖 2：註冊頁面 
![2](https://github.com/adams7718/Smart-tourism/blob/main/2.png)

## A. 輸入欄位 (Input Fields)
| 欄位名稱 (Field Name) | 資料型態 (Data Type) | 驗證規則 / 觸發行為 (Validation Rules / Triggered Actions) |
| :--- | :--- | :--- |
| **電子郵件 (Email)** | 字符串 (String) | 1. **必填**。2. 必須為有效 Email 格式。3. 系統中**唯一**。 |
| **暱稱 (Nickname)** | 字符串 (String) | 1. **必填**。2. 建議系統中唯一。3. 最小/最大長度限制。 |
| **密碼 (Password)** | 字符串 (String) | 1. **必填**。2. 建議有複雜度限制。3. **👁 圖標**：切換顯示/隱藏。 |
| **再次確認密碼 (Confirm Password)** | 字符串 (String) | 1. **必填**。2. 必須與 **密碼** 欄位的值**完全一致**。3. **👁 圖標**：切換顯示/隱藏。 |
| **註冊 (Register)** | 按鈕 (Button) | 點擊：執行所有欄位驗證，成功後建立帳號並導向指定頁面。 |
| **返回登入頁面 (Back to Login Page)** | 按鈕 (Button) | 點擊：導向「使用者登入」頁面。 |
---

## B. 螢幕顯示欄位 (Output Fields)

| 欄位名稱 (Field Name) | 功能描述 (Description) |
| :--- | :--- |
| **📋 註冊新帳號 (Register New Account)** | 頁面標題。 |
| **請輸入電子郵件 (Please enter email)** | 電子郵件輸入框的標籤。 |
| **請輸入暱稱 (Please enter nickname)** | 暱稱輸入框的標籤。 |
| **請輸入密碼 (Please enter password)** | 密碼輸入框的標籤。 |
| **請再次確認密碼 (Please confirm password again)** | 確認密碼輸入框的標籤。 |
| **👁 圖標 (Eye Icon)** | 切換密碼內容顯示/隱藏。 |
---

## 圖 3：忘記密碼 
![3](https://github.com/adams7718/Smart-tourism/blob/main/3.png)

## A. 輸入欄位 (Input Fields)

| 欄位名稱 (Field Name) | 資料型態 (Data Type) | 驗證規則 / 觸發行為 (Validation Rules / Triggered Actions) |
| :--- | :--- | :--- |
| **電子郵件 (Email)** | 字符串 (String) | 1. **必填**。2. 必須為有效 Email 格式。3. 該 Email **必須存在**於系統中。 |
| **發送驗證碼 (Send Verification Code)** | 按鈕 (Button) | 點擊：1. 驗證 Email。2. 成功後，**發送驗證碼**至該 Email 或手機。3. **觸發顯示**驗證碼/提示訊息，並可能在計時後**自動跳轉**到下一步 (輸入驗證碼/重設密碼)。 |
| **返回登入頁面 (Back to Login Page)** | 按鈕 (Button) | 點擊：導向「使用者登入」頁面。 |

---

## B. 螢幕顯示欄位 (Output Fields)
| 欄位名稱 (Field Name) | 功能描述 (Description) |
| :--- | :--- |
| **🔑 忘記密碼 (Forgot Password)** | 頁面標題，提示使用者當前頁面的功能。 |
| **電子郵件 (Email)** | 電子郵件輸入框的標籤。 |
| **您的驗證碼是 (Your verification code is)** | **（訊息區塊）** 成功發送驗證碼後顯示的提示訊息。 |
| **驗證碼 (Verification Code)** | **（訊息區塊）** 顯示系統生成的驗證碼（如圖中的 `625859`）。 |
| **自動跳轉提示 (Auto-redirect Prompt)** | **（訊息區塊）** 提示使用者畫面將在指定時間 (如圖中的 `5 秒`) 後自動跳轉到下一個步驟。 |
---

## 圖 4：重設密碼
![4](https://github.com/adams7718/Smart-tourism/blob/main/4.png)

## A. 輸入欄位 (Input Fields)

| 欄位名稱 (Field Name) | 資料型態 (Data Type) | 驗證規則 / 觸發行為 (Validation Rules / Triggered Actions) |
| :--- | :--- | :--- |
| **請輸入驗證碼 (Please enter verification code)** | 字符串 (String) | 1. **必填**。2. 必須輸入**有效的**、**未過期**的驗證碼。 |
| **請輸入新密碼 (Please enter new password)** | 字符串 (String) | 1. **必填**。2. 建議有複雜度限制 (如長度、包含字符類型)。3. **👁 圖標**：切換顯示/隱藏。 |
| **請再次確認新密碼 (Please re-confirm new password)** | 字符串 (String) | 1. **必填**。2. 必須與 **請輸入新密碼** 欄位的值**完全一致**。3. **👁 圖標**：切換顯示/隱藏。 |
| **重設密碼 (Reset Password)** | 按鈕 (Button) | 點擊：1. 驗證所有欄位。2. 成功後，**更新**使用者的密碼。3. 導向「登入頁面」或顯示成功訊息。 |
| **返回登入頁面 (Back to Login Page)** | 按鈕 (Button) | 點擊：導向「使用者登入」頁面。 |

---

## B. 螢幕顯示欄位 (Output Fields)
| 欄位名稱 (Field Name) | 功能描述 (Description) |
| :--- | :--- |
| **🔄 重設密碼 (Reset Password)** | 頁面標題，提示使用者當前正在進行密碼重設操作。前方的 **循環/更新圖標** 🔄 強化主題。 |
| **請輸入驗證碼 (Please enter verification code)** | 驗證碼輸入框的標籤。 |
| **請輸入新密碼 (Please enter new password)** | 新密碼輸入框的標籤。 |
| **請再次確認新密碼 (Please re-confirm new password)** | 確認新密碼輸入框的標籤。 |
| **👁 圖標 (Eye Icon)** | 切換密碼內容顯示/隱藏。 |
---

## 圖 5：使用者介面
![5](https://github.com/adams7718/Smart-tourism/blob/main/5.png)

## A. 輸入欄位 (Input Fields)

| 欄位名稱 (Field Name) | 資料型態 (Data Type) | 驗證規則 / 觸發行為 (Validation Rules / Triggered Actions) |
| :--- | :--- | :--- |
| **登出 (Logout)** | 按鈕 (Button) | 點擊：執行**登出**操作，清除使用者會話 (Session/Token)，導向「使用者登入」頁面。 |
| **使用 AI 自動排行程** | 按鈕 (Button) | 點擊：**啟動 AI 智慧排程**功能，導向相關配置頁面，讓 AI 根據需求自動生成行程。 |
| **自己搜尋瀏覽景點** | 按鈕/連結 (Button/Link) | 點擊：**啟動手動自由配置**功能，導向景點搜尋或地圖瀏覽頁面，讓使用者自行規劃行程。 |
| **<<** | 圖標/按鈕 (Icon/Button) | 點擊：**切換側邊欄**的顯示/隱藏狀態，用於釋放更多主畫面空間。 |
| **Deploy** | 文字/按鈕 (Text/Button) | 點擊：**(用途待定)** 依據上下文，可能是部署環境切換或特定系統功能。 |
| **⋮ (更多選項)** | 圖標/按鈕 (Icon/Button) | 點擊：**顯示更多**操作或設定的選單 (如：帳號設定、幫助等)。 |

---

## B. 螢幕顯示欄位 (Output Fields)

| 欄位名稱 (Field Name) | 功能描述 (Description) |
| :--- | :--- |
| **👤 123** | 顯示當前**登入的使用者暱稱或 ID** (圖中為 `123`)。 |
| **分隔線 (Horizontal Line 1 & 2)** | 視覺分隔線，用於區分側邊欄的不同區域 (如：個人資訊區與操作區)。 |
| **✨ 歡迎來到台灣旅遊小幫手** | 頁面主標題，歡迎使用者並說明產品名稱。 |
| **AI 智慧排程 (全新升級)** | **功能區塊標題 1**，介紹 AI 排程功能。 |
| **AI 介紹 (Description for AI)** | 描述 AI 智慧排程的功能細節，包括自動排程、排序、計算交通等。 |
| **手動自由配置** | **功能區塊標題 2**，介紹手動自由配置功能。 |
| **手動配置介紹 (Description for Manual)** | 描述手動配置的功能細節，包括自訂旅遊天數、搜尋資料圖片、自由加入行程。 |
---

## 圖 6：行程規劃頁(ai規劃行程)
![7](https://github.com/adams7718/Smart-tourism/blob/main/6.png)

## A. 輸入欄位 (Input Fields)
| 欄位名稱 (Field Name) | 資料型態 (Data Type) | 驗證規則 / 觸發行為 (Validation Rules / Triggered Actions) |
| :--- | :--- | :--- |
| **想去哪裡玩？** | 字符串 (String) | 1. **必填**。2. 建議提供地點列表供使用者選擇 (如下拉選單或自動完成)。3. 圖中範例值為：`臺北市`。 |
| **旅遊天數 (Days of Travel)** | 數字 (Number) | 1. **必填**。2. 必須為正整數。3. **加號 (+)/減號 (-)**：用於增加或減少天數。4. 圖中範例值為：`2`。 |
| **預算等級 (Budget Level)** | 選單 (Dropdown) | 1. **必選**。2. 透過下拉選單提供預算選項。3. 圖中範例值為：`經濟實惠 (背包客)`。 |
| **偏好交通 (Preferred Transportation)** | 多選標籤 (Multi-select Tag) | 1. **可選**。2. 透過下拉選單或標籤形式選擇多個交通方式。3. **X 圖標**：用於移除已選擇的交通方式。4. 圖中範例值為：`大眾運輸`。 |
| **偏好與必去景點 (Preferences & Must-see Spots)** | 多行文本 (Textarea) | 1. **可選**。2. 自由輸入文字，描述個人偏好、必去景點或特殊需求。3. 圖中範例值為：`九份、101、夜市`。 |
| **開始規劃 (Start Planning)** | 按鈕 (Button) | 點擊：1. 驗證所有必填欄位。2. 將所有參數送給 AI 引擎。3. 成功後，導向**行程結果顯示頁面**。 |
| **回到主選單 (Back to Main Menu)** | 按鈕 (Button) | 點擊：導向**首頁/儀表板**。 |
| **登出 (Logout)** | 按鈕 (Button) | 點擊：執行**登出**操作，導向「使用者登入」頁面。 |

---

## B. 螢幕顯示欄位 (Output Fields)
| 欄位名稱 (Field Name) | 功能描述 (Description) |
| :--- | :--- |
| **✈️ 規劃您的旅程 (Plan Your Trip)** | 頁面主標題。前方的 **飛機圖標** ✈️ 強化旅遊主題。 |
| **👤 123** | 顯示當前**登入的使用者暱稱或 ID**。 |
| **想去哪裡玩？ (Where do you want to go?)** | 旅遊地點輸入框的標籤。 |
| **旅遊天數 (Days of Travel)** | 旅遊天數輸入框的標籤。 |
| **預算等級 (Budget Level)** | 預算等級下拉選單的標籤。 |
| **偏好交通 (Preferred Transportation)** | 偏好交通選擇區的標籤。 |
| **偏好與必去景點 (Preferences & Must-see Spots)** | 景點/偏好多行文本框的標籤，附帶範例提示 (`如：台北101、士林夜市`)。 |

---

## 圖 7：AI 輸出行程（總覽/列表）
![7](https://github.com/adams7718/Smart-tourism/blob/main/7.png)

## A. 輸入欄位 (Input Fields)

| 欄位名稱 (Field Name) | 資料型態 (Data Type) | 驗證規則 / 觸發行為 (Validation Rules / Triggered Actions) |
| :--- | :--- | :--- |
| **想去哪裡玩？** | 字符串 (String) | 1. **必填**。2. 允許修改地點。3. 圖中範例值為：`臺北市`。 |
| **旅遊天數 (Days of Travel)** | 數字 (Number) | 1. **必填**。2. 必須為正整數。3. **加號 (+)/減號 (-)**：用於修改天數。4. 圖中範例值為：`1`。 |
| **預算等級 (Budget Level)** | 選單 (Dropdown) | 1. **必選**。2. 允許透過下拉選單修改預算。3. 圖中範例值為：`經濟實惠 (背包客)`。 |
| **偏好交通 (Preferred Transportation)** | 多選標籤 (Multi-select Tag) | 1. **可選**。2. 允許透過標籤形式修改交通方式。3. **X 圖標**：用於移除已選擇的交通方式。4. 圖中範例值為：`大眾運輸`。 |
| **偏好與必去景點 (Preferences & Must-see Spots)** | 多行文本 (Textarea) | 1. **可選**。2. 允許修改必去景點或偏好。 |
| **重新生成 (Re-generate)** | 按鈕 (Button) | 點擊：1. 驗證所有修改後的參數。2. 將新參數送給 AI 引擎。3. **重新生成**行程並更新右側的顯示結果。 |
| **行程編輯** | 標籤/按鈕 (Tab/Button) | 點擊：**切換到**行程編輯模式/介面。 |
| **圖文詳情** | 標籤/按鈕 (Tab/Button) | 點擊：**切換到**以圖片和文字呈現的詳細行程說明介面。 |
| **導覽圖** | 標籤/按鈕 (Tab/Button) | 點擊：**切換到**地圖顯示介面，通常會顯示景點位置和導航路線。 |
| **Day 1 導航** | 按鈕 (Button) | 點擊：**啟動**當日行程在地圖上的導航或路線顯示功能。 |

---
## B. 螢幕顯示欄位 (Output Fields)
| 欄位名稱 (Field Name) | 功能描述 (Description) |
| :--- | :--- |
| **🛠️ 修改設定 (Modify Settings)** | 頁面主標題，提示當前頁面主要功能。 |
| **🚀 Google Maps 路線導航** | 行程結果區塊的標題，提示此區塊提供路線導航相關資訊。 |
| **Day (日)** | 行程表格欄位：顯示行程是第幾天 (例如：`1`)。 |
| **序 (Order)** | 行程表格欄位：顯示當日景點的順序 (例如：`1, 2, 3...`)。 |
| **City (城市)** | 行程表格欄位：顯示該景點所在的城市 (例如：`臺北市`)。 |
| **District (區域)** | 行程表格欄位：顯示該景點所在的區域 (例如：`萬華區`)。 |
| **景點 (Attraction)** | 行程表格欄位：顯示具體的景點名稱。 |
| **交通 (Transportation)** | 行程表格欄位：顯示從上一個景點/地點到達此景點的**交通建議和路線說明**。 |
---

## 圖 8：手動排行程（詳細 / 卡片樣式）
![8](https://github.com/adams7718/Smart-tourism/blob/main/8.png)

## A. 輸入欄位 (Input Fields)

| 欄位名稱 (Field Name) | 資料型態 (Data Type) | 驗證規則 / 觸發行為 (Validation Rules / Triggered Actions) |
| :--- | :--- | :--- |
| **景點名稱 (Attraction Name)** | 字符串 (String) | 1. **右側頂部**的輸入框。2. 景點名稱，圖中範例為：`野柳漁港`。 |
| **新北市** | 選單 (Dropdown) | 1. **地點/城市**選擇。2. 允許透過下拉選單修改景點城市。 |
| **萬里區** | 選單 (Dropdown) | 1. **地點/區域**選擇。2. 允許透過下拉選單修改景點區域。 |
| **野柳漁港 (下拉選單)** | 選單 (Dropdown) | 1. **景點名稱**的選擇/輸入欄位。2. 允許搜尋並選擇景點名稱。 |
| **Day 1 Google 導航** | 按鈕 (Button) | 點擊：**啟動** Day 1 行程在地圖上的導航或路線顯示功能。 |
| **開啟 Day 2 Google 導航** | 按鈕 (Button) | 點擊：**啟動** Day 2 行程在地圖上的導航或路線顯示功能。 |
| **景點編輯圖標 (✏️)** | 圖標/按鈕 (Icon/Button) | 點擊：用於**編輯**行程清單中指定景點的資訊。 |
| **景點移除圖標 (🗑️)** | 圖標/按鈕 (Icon/Button) | 點擊：用於**移除**行程清單中指定景點。 |
| **清除所有行程** | 按鈕 (Button) | 點擊：**清除**左側清單中所有已排的行程。需有二次確認機制。 |
| **登出 (Logout)** | 按鈕 (Button) | 點擊：執行**登出**操作，導向「使用者登入」頁面。 |
| **加入哪一天？** | 數字/選單 (Number/Dropdown) | 1. **天數選擇**。2. 選擇景點要加入到哪一天的行程中。3. 圖中範例值為：`2`。 |
| **加入 Day X (➕)** | 按鈕 (Button) | 點擊：將右側選定的景點**加入**到左側清單中指定的天數 (Day X)。 |

---

## B. 螢幕顯示欄位 (Output Fields)

| 欄位名稱 (Field Name) | 功能描述 (Description) |
| :--- | :--- |
| **手動行程清單 (Manual Itinerary List)** | 頁面標題（左側），提示當前功能。 |
| **Day 1 / Day 2** | 行程清單區塊：顯示行程劃分的天數標籤。 |
| **1. 景點名稱 (左側清單)** | 行程清單區塊：顯示該天的景點名稱和順序。圖中範例為：`1. 外木山海灣`。 |
| **想搜尋甚麼？ (What do you want to search?)** | 景點名稱輸入框的**提示文字/標籤**。 |
| **新北市 / 萬里區 / 景點** | 右側景點詳情頁面中，地點輸入框的標籤。 |
| **景點照片 (Attraction Photo)** | 顯示景點的圖片 (圖中為野柳漁港的照片)。 |
| **景點標題 (Title)** | 右側景點詳情卡片的標題 (圖中為 `野柳漁港`)。 |
| **📍 地址 / 📞 電話 / ⏰ 開放時間** | 景點詳情資訊：顯示靜態的地址、電話和開放時間等詳細資訊。 |
| **景點描述 (Description)** | 景點詳情資訊：提供景點的詳細文字介紹。 |

---

## 圖 9：直接帶入 Google Map 執行路線
![9](https://github.com/adams7718/Smart-tourism/blob/main/9.png)

## A. 輸入欄位 (Input Fields)

| 欄位名稱 (Field Name) | 資料型態 (Data Type) | 驗證規則 / 觸發行為 (Validation Rules / Triggered Actions) |
| :--- | :--- | :--- |
| **起點 (Origin)** | 字符串 (String) | 1. **必填**。2. 必須為有效的地址或地點名稱。 |
| **終點 (Destination)** | 字符串 (String) | 1. **必填**。2. 必須為有效的地址或地點名稱。 |
| **新增目的地 (Add Stop)** | 按鈕 (Button) | 點擊：在路線中**新增**一個中途停靠點輸入欄位。 |
| **立即出發 (Leave Now)** | 選單 (Dropdown) | 點擊：切換或設定**出發時間**或**到達時間**。 |
| **選項 (Options)** | 按鈕 (Button) | 點擊：開啟路線設定選項 (如：避開收費站/高速公路)。 |
| **駕駛 (Car Icon)** | 按鈕 (Button) | 點擊：切換**開車**交通模式。 |
| **大眾運輸 (Bus Icon)** | 按鈕 (Button) | 點擊：切換**大眾運輸**交通模式。 |
| **步行 (Walking Icon)** | 按鈕 (Button) | 點擊：切換**步行**交通模式。 |
| **單車 (Bike Icon)** | 按鈕 (Button) | 點擊：切換**單車**交通模式。 |
| **機車 (Motorcycle Icon)** | 按鈕 (Button) | 點擊：切換**機車**交通模式。 |
| **複製連結 (Copy Link)** | 按鈕 (Button) | 點擊：**複製**當前路線的地圖連結。 |
| **加油站 / 飯店等** | 按鈕 (Button) | 點擊：**搜尋**沿途的加油站、飯店或其他類型的地點。 |
| **導航 (Navigation)** | 按鈕 (Button) | 點擊：**開始**手機裝置上的即時語音導航。 |

---

## B. 螢幕顯示欄位 (Output Fields)

| 欄位名稱 (Field Name) | 功能描述 (Description) |
| :--- | :--- |
| **路線搜尋結果 (Route Search Result)** | 顯示該交通模式下**最佳、最快或多個替代**路線的距離與預計時間。 |
| **已儲存 / 最近** | 側邊欄選單：顯示已儲存的地點或最近的路線紀錄。 |
| **住家 & 辦公室** | 側邊欄選單：顯示或設定「家」與「公司」的常用位置。 |
| **地圖顯示區 (Map Display)** | 視覺輸出：顯示**地理地圖**、**計算出的路線** (藍色線段) 和路線上的交通資訊。 |
| **路線摘要時間 (Summary Time)** | 路線結果頂部：顯示不同交通模式的預計時間摘要 (如：最佳 4 分、步行 31 分)。 |
| **地點標記 (Place Markers)** | 地圖上標示**景點** (`獅子公園`)、**起點/終點**或**路段上的車輛資訊**。 |

---
