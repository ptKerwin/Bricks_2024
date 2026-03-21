# 113BRICKS 前端文件
## 1. 專案簡介與架構總覽
113BRICKS 是一個以 Vue 3 為核心的前端專案，結合 Vuex 狀態管理、Vue Router 路由、Element Plus UI 框架與多個自訂元件，實現多頁面、模組化的應用架構。專案目錄分為主應用（frontend/frontend）與元件、頁面、狀態管理等子目錄。

## 2. 前端啟動流程
進入 frontend/frontend 目錄，執行 npm install 安裝依賴。
執行 npm run serve 啟動本地開發伺服器。
入口檔案為 src/main.js，掛載 App.vue 至 #app。

## 3. 元件與頁面結構
App.vue：全域入口元件，僅執行渲染行為作為頁面出口。
views/：存放各主要頁面（如 HomeView、Login、MeetingRecord 等）。
components/：存放可重用元件（如 NavBar、MeetingCards、UserInfo 等），並依開發者分子資料夾管理。
router/index.js：定義所有路由與對應頁面元件。

## 4. 路由設計與頁面切換
採用 Vue Router，使用 history 模式。
路由集中於 src/router/index.js，包含首頁、登入、註冊、各功能頁面等。
路由元件多以動態 import 方式載入，提升效能。

## 5. 狀態管理（Vuex store）
src/store/index.js 匯入 modules/records.js，進行模組化管理。
store/state.js 定義全域狀態（如使用者、會議、標籤、訊息等）。
mutations 負責同步修改狀態，getters 提供封裝存取。
使用 vuex-persistedstate 實現部分狀態持久化於 localStorage。(這對於單機host適用，後續 scale up 須調整快取作法)

## 6. 主要資料流與 API 互動
主要資料（如 allRecords、currRecord、userID 等）集中於 Vuex store。
透過 axios 進行 API 請求，與後端同步資料。
mutations、actions 控制資料流與狀態變更，元件透過 dispatch/commit 操作。

## 7. UI 框架與第三方套件
vuex-persistedstate：狀態持久化。
axios：API 請求。
Google Fonts、Bootstrap Vue、lodash 等輔助套件。

## 8. 注意事項與最佳實踐
路由與 store 採模組化設計，便於維護與擴充。
元件命名與資料夾結構依或開發者分組。
相似元件命名與設計請在組內會議時討論相對應作法。

*詳細維護紀錄請見 Git 版本控制。*
