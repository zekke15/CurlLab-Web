# CurlLab-Web｜網頁版 HTTP 請求測試工具

> **習題 1：製作一個類似 curl 的專案程式**  
> 使用 **HTML、CSS、JavaScript、Python Flask** 開發的視覺化 HTTP 請求工具。

![Python](https://img.shields.io/badge/Python-3.10%2B-3776AB?logo=python&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-3.x-000000?logo=flask&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-Vanilla-F7DF1E?logo=javascript&logoColor=black)
![Deploy](https://img.shields.io/badge/Deploy-Render-46E3B7)

##  專案介紹

**CurlLab-Web** 是一個在瀏覽器中操作的簡易 HTTP/API 測試工具。它將 `curl` 常用的網路請求功能改成圖形化介面，讓使用者不必記住複雜的指令，也能送出 GET、POST 等 HTTP 請求，觀察伺服器回傳的狀態碼、內容、標頭與回應時間。

本專案由 **前端網頁（HTML / CSS / JavaScript）** 搭配 **Python Flask 後端** 實作，並部署至 Render 以支援網際網路存取。

- **GitHub 原始碼：** https://github.com/zekke15/CurlLab-Web
- **網站公開網址：** `（Render 顯示 Live 後，在此貼上你的 .onrender.com 網址）`
- **程式目錄：** `homework-1/`

> 這是供教學展示使用的 HTTP 測試網站，**不是無限制的通用代理伺服器**。公開版僅允許向指定教學 API 傳送 HTTPS 請求。

## 主要功能

| 功能 | 說明 |
| --- | --- |
| HTTP 方法選擇 | 支援 GET、POST、PUT、PATCH、DELETE、HEAD |
| URL 輸入 | 指定要測試的 API 網址 |
| 自訂 Headers | 使用 JSON 格式輸入 HTTP 請求標頭 |
| Request Body | 傳送一般文字或 JSON 資料（不適用 GET、HEAD） |
| 回應內容 | 顯示文字、JSON 等伺服器回應 |
| 回應標頭 | 查看伺服器回傳的 HTTP Headers |
| 狀態與效能 | 顯示 HTTP 狀態碼、耗時及回應大小 |
| 快速範例 | 提供常見 GET / POST 測試情境 |
| 錯誤提示 | 顯示網址、JSON 格式、網路連線等錯誤 |

##  使用技術

| 類別 | 技術 | 用途 |
| --- | --- | --- |
| 前端結構 | HTML5 | 網頁介面 |
| 前端樣式 | CSS3 | 深色主題、響應式排版 |
| 前端互動 | JavaScript | 操作表單、呼叫 Flask API、顯示結果 |
| 後端 | Python + Flask | API 端點及請求驗證 |
| HTTP 連線 | requests | 向指定測試網站發送 HTTP 請求 |
| 正式伺服器 | Gunicorn | 雲端啟動 Flask 應用 |
| 版本管理 | GitHub | 保存與分享原始碼 |
| 雲端部署 | Render | 公開網站託管 |

## 📁 專案結構

```text
CurlLab-Web/
└── homework-1/
    ├── app.py              # Flask 主程式與 HTTP 請求 API
    ├── requirements.txt    # Python 套件需求
    ├── render.yaml         # Render 部署設定
    ├── README.md           # 專案說明
    ├── templates/
    │   └── index.html      # HTML 網頁畫面
    ├── static/
    │   ├── style.css       # 網頁樣式
    │   └── app.js          # 前端互動邏輯
    └── tests/
        └── test_app.py     # 自動化測試
```

##  本機執行方式

**需求：** Python 3.10 或以上版本。

1. 下載專案：

   ```bash
   git clone https://github.com/zekke15/CurlLab-Web.git
   cd CurlLab-Web/homework-1
   ```

2. 安裝套件（Windows）：

   ```bash
   py -m pip install -r requirements.txt
   ```

3. 啟動 Flask：

   ```bash
   py app.py
   ```


macOS / Linux 可將 `py` 改為 `python3`。

##  使用教學

### 範例一：GET 取得 JSON 資料

1. HTTP Method 選擇 `GET`。
2. URL 輸入：

   ```text
   https://jsonplaceholder.typicode.com/todos/1
   ```

3. 按下「送出請求」。
4. 檢查右側 HTTP Status、回應時間、Response Body 與 Headers。

**預期回應內容範例：**

```json
{
  "userId": 1,
  "id": 1,
  "title": "delectus aut autem",
  "completed": false
}
```

### 範例二：POST 傳送 JSON 資料

1. HTTP Method 選擇 `POST`。
2. URL 輸入：

   ```text
   https://jsonplaceholder.typicode.com/posts
   ```

3. 在 Body 輸入：

   ```json
   {
     "title": "CurlLab 測試",
     "body": "Hello from CurlLab!",
     "userId": 1
   }
   ```

4. 啟用 JSON 格式選項，按下「送出請求」。
5. 查看回傳結果。

> JSONPlaceholder 是模擬 API，POST 並不代表資料真的永久儲存。網站需能連上外部測試 API 才能成功。

##  Render 公開部署

本專案的程式位於 GitHub 儲存庫的 `homework-1/`，因此在 Render 建立 **Web Service** 時，請設定：

| Render 欄位 | 設定值 |
| --- | --- |
| Repository | `zekke15/CurlLab-Web` |
| Branch | `main` |
| Language | `Python 3` |
| **Root Directory** | **`homework-1`** |
| Build Command | `pip install -r requirements.txt` |
| Start Command | `gunicorn app:app --bind 0.0.0.0:$PORT` |

部署完成並顯示 **Live** 後，在本文件上方填入 Render 所提供的真實公開網址。Render 免費服務閒置後可能休眠，重新進站會有啟動延遲。

> 只有 GitHub Pages 無法直接執行本專案，因為專案需要 Python Flask 後端。

## 程式運作流程

```text
使用者開啟 CurlLab 網站
        ↓
輸入 URL、HTTP 方法、Headers、Body
        ↓
JavaScript 呼叫 Flask：POST /api/request
        ↓
Python 驗證網址與請求內容
        ↓
requests 向允許的教學 API 發送請求
        ↓
Flask 回傳狀態碼、耗時、內容與 Headers
        ↓
JavaScript 將結果顯示於畫面
```

## 網站安全與使用限制

- 公開版僅允許向 `jsonplaceholder.typicode.com` 與 `httpbin.org` 發送 HTTPS（443 埠）請求，除非部署者另行變更安全設定。
- 禁止直接請求私人／本機 IP，且不自動跟隨 HTTP 重新導向。
- 請求大小限制為 100 KB，回應最多讀取約 1 MB。
- 有基本的請求頻率限制，但不應視為完整的防濫用機制。
- 不要在網站中輸入密碼、API Key、Cookie、個資或其他敏感資訊。

## 自動化測試

在 `homework-1` 資料夾內執行：

```bash
py -m unittest discover -s tests -v
```

測試用於驗證 HTTP 端點與相關輸入處理；是否全部通過，應以自己電腦或部署環境的實際執行結果為準。

## 🎓 作業說明與學習心得

本次習題要求製作一個類似 `curl` 的專案。原本 `curl` 主要透過命令列指令操作，我將其設計成較容易使用的網頁介面，讓使用者可以直接選擇 HTTP 方法、輸入資料，並觀察伺服器回應。

透過此次實作，可以學習：

1. HTTP GET、POST 等請求方法的用途。
2. HTTP Headers、Request Body、Status Code 與 JSON 格式。
3. HTML、CSS、JavaScript 如何與 Python Flask 後端合作。
4. 使用 GitHub 管理專案，以及透過 Render 部署公開網站。
5. 公開 HTTP 工具時，為什麼需要對外部請求進行安全限制。

**開發方式：** 使用 ChatGPT 協助規劃程式架構、產生與調整程式碼和文件，再透過 VS Code、GitHub、Render 進行實作與部署。

## 📸 專案截圖（自行補上）

建議補上三張實際操作畫面：**網站首頁、GET 成功回應、POST 成功回應**。完成截圖後可存入專案的 `screenshots/` 資料夾，再於此處加入 Markdown 圖片連結。

---

**專案名稱：** CurlLab-Web  
**作業主題：** 習題 1 — 類似 curl 的網頁版專案  
**GitHub：** https://github.com/zekke15/CurlLab-Web
