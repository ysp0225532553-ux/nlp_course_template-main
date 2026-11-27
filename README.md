# NLP 自然語言處理 (115 S1) - 課程專案

本專案為 NLP 課程開發環境與實作練習區。

---

## 開發者資訊 (Developer Info)
* **學號**：[U12627044]
* **姓名**：[蕭宇辰]

## 硬體與環境狀態 (Environment Setup)
* **PyTorch 執行環境**：[Windows CPU]

---

## 課程任務清單 (Task Checklist)

### Week 2：開發環境與專案架構初始化
請在完成下列任務後，將 `[ ]` 改為 `[x]`：
- [*] 成功建立 GitHub 帳號並 Clone 本專案至本機端。
- [*] 成功建立 `.venv` 虛擬環境，並透過 `.gitignore` 隱藏底層檔案。
- [*] 成功於虛擬環境內安裝通用套件清單 (`requirements.txt`) 與專屬硬體版本的 PyTorch。
- [*] 更新本 README 文件，填寫學號、姓名與 PyTorch 環境狀態。
- [*] 成功使用 Git 完成 `commit` 並 `push` 同步至 GitHub 雲端。

### Week 4 / 8：Data Ingestion & Topology-Aware Chunking
- [x] **環境建置與版控防護**：更新 `.gitignore` 忽略原始 PDF 與批次輸出，並保留 `.keep` 目錄結構。
- [x] **資料擷取與合併**：任務 1-A 頁首頁尾清除、1-B 雙語標題合併、1-C 雙語條文合併。
  - [x] 1-A：頁首頁尾清除的動態檔名擷取正則與斷言通過。
  - [x] 1-B：第二個標題限英文字母開頭；正向斷言通過，中文標題反例保持不變。
  - [x] 1-C：雙語條文合併斷言通過。
- [x] **結構健全度 (Mechanical Sanity)**：
  - [x] 拓撲錨定率
  - [x] 運用「中位數 (Median)」計算文本長度。
- [x] **語意品質 (Semantic Quality)**：
  - [x] (選修) 計算 Shannon Information Entropy，並比較 Cleaned 與 Raw 資料的中位數資訊熵。
- [x] **觀測儀表板與報告**：
  - [x] 成功繪製 4 拼圖資料觀測儀表板 (`metrics_dashboard.png`)。
  - [x] 成功將核心評估指標匯出為根目錄下的 `metrics.json`。

### Week 10：關鍵字檢索與語意檢索
- [x] 使用 TF-IDF、BM25 與句向量搜尋校規 chunks，並比較 10 個問題的 hit@3。
- [x] 完成 cosine 相似度、Dense 檢索、3-C 自選問題與反思。
- [x] 比較結果：TF-IDF 0.40、BM25 0.50、Dense 0.80；結果顯示關鍵字與語意檢索各有適用情境。
- **本週新增檔案**：
  - `notebooks/10_setup.ipynb`：Week 10 環境與句向量預先計算設定。
  - `notebooks/10_vector_similarity.ipynb`：向量相似度、三種檢索方法與評估練習。
  - `week10_retrieval_comparison.json`：10 個校規問題的檢索結果、人工判斷與 hit@3 統計。

### Week 12: Chunking Strategies & Vector Index

- [x] **依結構切塊**：執行 `src/rechunk_v2.py`，產生 `data/processed_v2/`（策略 C、D）
- [x] **固定長度 + 重疊**：完成 `fixed_chunks`（策略 B）
- [x] **向量索引**：儲存 `data/embeddings/week12_v2_emb.npy`（策略 D，第 14 週使用）
- [x] **自動評估**：完成 `hit_at_k`、`topk_chars`，比較四種策略
  | 策略 | hit@3 | hit@5 |
  |---|---:|---:|
  | A 第 8 週 | 0.75 | 0.79 |
  | B 固定長度 + 重疊 | 0.67 | 0.83 |
  | C 依條文（無標題） | 0.67 | 0.83 |
  | D 依條文 + 標題 | 0.71 | 0.88 |
- [x] **自己出題**：設計 2 題，並比較 A、B、D 的答案排名
- [x] **選做：調整 chunk 上限**：D 策略上限設為 800 字，243 個 chunks；hit@3 為 0.75、hit@5 為 0.92
