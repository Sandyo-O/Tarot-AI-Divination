# 🔮 命運之塔 — AI 塔羅占卜師

> 用 RAG + LLM 打造可自訂風格的塔羅占卜 Web App

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Sandyo-O/FamilyCare_Agent/blob/main/%E3%80%90%E6%9C%9F%E6%9C%AB%E5%B0%88%E6%A1%88%E3%80%91%E7%94%A8RAG%E6%89%93%E9%80%A0AI%E5%A1%94%E7%BE%85%E5%8D%A0%E5%8D%9C%E5%B8%AB%E7%9A%84%E5%89%AF%E6%9C%AC.ipynb)

---

## 專案簡介

這是一個以 **RAG（Retrieval-Augmented Generation，檢索增強生成）** 架構為核心的 AI 塔羅占卜系統。

使用者輸入問題後，系統會從塔羅牌義向量資料庫中檢索相關內容，結合使用者自選的占卜主題、牌陣與占卜師風格，動態組合 Prompt 並呼叫 LLM 生成個人化的占卜解讀，最後透過 Gradio Web UI 呈現結果。

---

## 技術架構

```
使用者輸入問題
      ↓
FAISS 向量資料庫檢索相關塔羅牌義
（multilingual-e5-small embedding）
      ↓
動態組合 Prompt
（占卜主題 + 牌陣 + 風格 + 檢索結果）
      ↓
LLM 生成占卜解讀
（支援 GPT-4 / GPT-3.5 / LLaMA 3 / Mistral / Gemini / HuggingFace）
      ↓
Gradio Web UI 呈現結果
```

---

## 使用技術

| 類別 | 工具 / 套件 |
|------|------------|
| RAG 框架 | LangChain |
| 向量資料庫 | FAISS |
| Embedding 模型 | HuggingFace `intfloat/multilingual-e5-small` |
| LLM API | OpenAI API、Groq API |
| 支援模型 | GPT-4、GPT-3.5、LLaMA 3、Mistral、Gemini、HuggingFace |
| Web UI | Gradio |
| 開發環境 | Google Colab、Python |

---

## 功能特色

### 🔮 占卜主題（6 種）
- 不限主題、感情、工作、學業、人際、人生目標

### 🃏 牌陣（4 種）
- **單張占卜**：快速針對單一問題獲取命運訊息
- **三張牌**：分別代表「過去」「現在」「未來」
- **愛情十字陣**：五張牌，專門針對感情問題設計
- **五芒星陣**：五張牌，分別代表現況、障礙、潛能、建議、結果

### ✨ 占卜師風格（4 種）
- **冷靜分析型**：條理清晰、客觀務實
- **溫柔療癒型**：溫暖柔和、安慰人心
- **中二魔幻型**：神祕戲劇化、充滿儀式感
- **搞笑活潑型**：幽默風趣、輕鬆正能量

### 🧠 多 LLM 支援
使用者可在介面上切換不同模型，系統會依選擇呼叫對應的 API 或本地模型。

---

## 快速開始

1. 點擊上方 **Open In Colab** 按鈕開啟 Notebook
2. 在 Colab 的 Secrets 中設定你的 API Key（`Groq` 或 `OPENAI_API_KEY`）
3. 依序執行所有 Cell
4. 在 Gradio 介面中選擇占卜主題、牌陣、風格與模型，輸入問題即可開始占卜

---

## 專案結構

```
FamilyCare_Agent/
├── 【期末專案】用RAG打造AI塔羅占卜師的副本.ipynb   # 主程式
└── tarot_db/                                        # FAISS 塔羅牌義向量資料庫
```

---

## 學習歷程與反思

這個專案是我第一次實作完整的 RAG 架構，從資料準備、向量資料庫建置、Prompt 設計到 Web UI 串接都親手完成。

過程中發現幾個值得改進的地方：

- **回答品質**受 embedding 模型和資料庫內容品質影響很大，未來可從改善資料清理流程著手
- **Prompt 設計**對輸出風格影響顯著，不同語氣的 system prompt 讓模型回應差異很大，這是個有趣的發現
- 多 LLM 支援的架構讓我理解了不同模型 API 的串接方式，以及各模型在同樣 prompt 下的回應差異

---

## 相關技術關鍵字

`RAG` `LangChain` `FAISS` `HuggingFace Embeddings` `OpenAI API` `Groq` `Gradio` `LLM` `生成式AI` `Python`
