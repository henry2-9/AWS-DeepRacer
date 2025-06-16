# 2025_AWS-DeepRacer_NTUT_第8組

> Reinforcement learning strategies for AWS DeepRacer — from stable baseline to sub-9 second laps on the re:Invent 2018 track.

本倉庫記錄了使用 **強化學習（Reinforcement Learning）** 技術，在 AWS DeepRacer 模擬器中針對 re:Invent 2018 賽道所進行的多階段訓練過程，最終成功達成 **單圈低於 9 秒** 的高速完賽模型。

---

## 📌 專案目標

- 建立可穩定完賽的 baseline 模型  
- 持續優化動作空間與獎勵函數  
- 提升速度同時保持穩定，挑戰圈速極限  
- 完整記錄訓練演進歷程，供後續調參或 fine-tune 使用  

---

## 🚀 專案特色

- ✅ **多版本 reward 設計（v1.0 ~ v1.3）**
- 🧠 精細轉向控制與速度獎勵聯動
- 🕹 自定義動作空間（最高達 10 組動作）
- 📊 每次訓練皆有 reward 曲線與評估圖
- 🏁 模型最終單圈最快達 **8.617 秒**

---

## 🧪 訓練版本一覽

| 版本 | 說明                           | 圈速    | 特點摘要                                             |
|------|--------------------------------|---------|------------------------------------------------------|
| v1.0 | 最初穩定完賽 baseline           | 11.062s | 預設 reward，無懲罰機制，穩定但慢                    |
| v1.1 | 強化速度與出界懲罰              | 9.011s  | 提升 reward 強度，開始進入 單圈低於 10 秒 表現        |
| v1.2 | 精細化轉向與速度聯動           | 8.817s  | 引入 steering 轉向角度分級獎懲，動作空間 ±15° 提升至 3.0       |
| v1.3 | 轉向懲罰微調、訓練更穩定        | 8.617s  | 更細緻的轉向邏輯、learning rate 微調                  |



📄 詳細內容請見：`v1.0/README.md`、`v1.1/README.md` 等
