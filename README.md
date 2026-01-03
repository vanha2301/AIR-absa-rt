<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&height=220&text=ABSA%20Lexicon%20Sentiment%20(VI)&fontAlign=50&fontAlignY=40&desc=%20%2B%20NegDict%20%2B%20SacThaiDict&descAlign=50&descAlignY=60&animation=fadeIn" />
</p>

<p align="center">
  <!-- Đổi <YOUR_USERNAME> và <YOUR_REPO> cho đúng repo của bạn -->
  <a href="https://colab.research.google.com/drive/1QelwEOB354N-ykg_Sy6dfbtSBaXpWbtM?usp=sharing">
    <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>
  </a>
  <img src="https://img.shields.io/github/stars/<YOUR_USERNAME>/<YOUR_REPO>?style=for-the-badge" />
  <img src="https://img.shields.io/github/forks/<YOUR_USERNAME>/<YOUR_REPO>?style=for-the-badge" />
  <img src="https://img.shields.io/github/issues/<YOUR_USERNAME>/<YOUR_REPO>?style=for-the-badge" />
  <img src="https://img.shields.io/github/last-commit/<YOUR_USERNAME>/<YOUR_REPO>?style=for-the-badge" />
</p>

---

## 📌 Overview

Baseline **Vietnamese lexicon-based sentiment analysis** phân loại **positive / neutral / negative** (không cần training model).

Ý tưởng chính:
- **VietSentiWordNet**: chấm điểm cảm xúc theo từ/phrase (PosScore − NegScore)
- **NegDict**: xử lý phủ định (đảo cực tính trong một *context window*)
- **SacThaiDict**: tăng/giảm cường độ (intensity weighting)

✅ Nhẹ • ✅ Dễ giải thích • ✅ Chạy nhanh  
⚠️ Hạn chế: sarcasm, ngữ cảnh dài, slang mới / từ vựng theo domain

---

## 🎯 Project Objectives

- Xây dựng sentiment classifier (pos/neu/neg) theo hướng **lexicon-based**
- Tích hợp **VietSentiWordNet + NegDict + SacThaiDict**
- Có notebook chạy được để **predict CSV** và **export kết quả**

---

## 🧠 Method (Pipeline)

```mermaid
flowchart LR
A["Text normalization\nUnicode + cleanup"] --> B["Vietnamese tokenization\n(underthesea)"];
B --> C["Lexicon scoring\nVietSentiWordNet\n(Pos - Neg)"];
C --> D["Negation handling\nNegDict + neg_window"];
D --> E["Intensity adjustment\nSacThaiDict weights"];
E --> F["Label mapping\npos / neu / neg"];

