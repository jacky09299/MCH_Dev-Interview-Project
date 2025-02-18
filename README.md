# MCH_Dev-Interview-Project

## 任務要求

### 第一部分：自我介紹

來介紹一下你自己吧！這個任務要求你完成一個簡單且美化過的自我介紹區塊。
- **美化版面**：個人簡介的灰色框框是不是有點醜呢？希望你可以修改一下版面配置，以下是參考模板。
  ![img1](https://github.com/user-attachments/assets/fb78bddf-f21a-4203-96ca-9a2302da2e13)
- **內容填寫**：在 `<header class="intro-header">` 內撰寫個人簡介（不超過 200 字），並加入一張自己的照片。
- **資訊補充**（請使用模板）：如果想要展現更多自己的資訊，可以在下方用條列的形式呈現ㄛ。（非必寫）

### 第二部分：歷年梅竹黑客松網站

這個任務要求你實現一個顯示歷年梅竹黑客松網站的頁面。版面中會呈現了每個網站的圖片、名稱、描述以及一個連結按鈕。
初始頁面中，因為你尚未拿到後端的資料，所以只會出現 heading 是正常的。

- **版面設計**：在 `.websites-grid` 這個 css-style 內設計 RWD 網格布局，確保在小螢幕上顯示一行，大螢幕上顯示多行。
  ![img2](https://github.com/user-attachments/assets/262ff69e-35fc-45c5-b668-f416b299fb97)
- **API 取得資料**：你需要從 [後端 API](https://mch-dev.userwei.com/docs/) 獲取 `websites` 陣列的數據，並且確保從 API 取得的資料能夠正確渲染在 Vue 組件內。
> [!TIP]
> 你可以使用 Axios 獲取數據並儲存在 Vue 的 data 中。

## 如何開始

1. 點擊右上角 Fork 將此專案複製到自己的倉儲下。
   ![img3](https://github.com/user-attachments/assets/7d1d42c2-9262-452a-803b-17f84b8e7d35)

2. 將專案從自己的倉儲 clone 到本地端。

   ```bash
   git clone https://github.com/<username>/MCH_Dev-Interview-Project.git
   ```

3. 開啟 terminal，進入專案的 frontend 資料夾安裝所需的套件並啟動開發伺服器。

   ```bash
   cd frontend
   npm install
   npm run dev
   ```

4. 開啟瀏覽器，進入 http://localhost:5173/ 依照任務要求完成自己的個人網頁。
5. 完成後，將所有更改提交並推送到自己的倉儲。

   ```bash
   git add .
   git commit -m "feat: complete task requirements"
   git push
   ```

6. 在首頁頂部選擇 `GitHub Action`，選擇 `I understand my workflows, go ahead and enable them`。
![img4](https://github.com/user-attachments/assets/820a9d9b-6421-4dab-abbd-54a8ca18f00a)

7. 前往設定頁面開啟 GitHub Pages，並選擇部署的分支為 `gh-pages`。
![img5](https://github.com/user-attachments/assets/9bba9357-bec1-4768-8fe8-fb759619ff9c)

8. 點擊首頁右側 About 區域旁的設定，勾選 `Use your GitHub Pages website`，然後打開網站確認所有內容是否正常顯示。
![img6](https://github.com/user-attachments/assets/381e8098-b5a1-4a07-b5ba-732f4730fafa)

9. 在首頁頂部選擇 `Pull requests`，建立新的請求並提交。
![img7](https://github.com/user-attachments/assets/159c587b-f4a1-4425-97a1-65d90906fdbc)

## 注意事項
1. 請不要攻擊我們的 server，這邊都有做流量監控，你把它打下來不會加分，還會害別人沒後端可以寫網頁 QwQ。
2. 我們沒有限制使用大型 LLM 模型，若有使用的話要盡量理解其產生的內容，我們可能會在面試中詢問相關基礎問題。
3. 如果 GitHub Actions 顯示失敗，可以先確認 `Workflow permissions` 是否設定為 `Read and write permissions`。
![img8](https://github.com/user-attachments/assets/ec1c5dc0-a686-4a5f-b59f-f455033df7c4)

## 一些有用的東東

- 範例網站：https://mch-dev.userwei.com/
- 後端 API 文件：https://mch-dev.userwei.com/docs/
