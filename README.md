# 2026 本地 LLM 選型指南

🤖 一個互動式的開源大型語言模型選型工具，幫助你根據硬體規格找到最適合的模型。

## 功能特性

- 🖥️ **硬體支援**：NVIDIA GPU、AMD ROCm、Apple Silicon
- 🎯 **智能推薦**：根據 VRAM/統一記憶體大小自動推薦模型
- 📊 **完整規格表**：11 個精選開源模型的詳細對比
- 🔬 **深度技術分析**
  - VRAM 三桶模型（權重 + KV Cache + 執行期）
  - MoE 架構真實行為解析
  - KV Cache 壓縮策略
  - CPU 分流速度影響
  - Apple Silicon 統一記憶體規則
  - AMD 顯卡實施細節
  - 量化格式選擇指南
  - 推論工具對比

- 🎨 **用戶體驗**
  - 深色高對比主題
  - 字體放大選項
  - 響應式設計
  - 實時滑桿選擇

## 線上訪問

📱 直接訪問：**[jiarong0423.github.io/LLM](https://jiarong0423.github.io/LLM)**

## 本地部署

### 方式一：直接打開
```bash
# 克隆仓库
git clone https://github.com/jiarong0423/LLM.git
cd LLM

# 在瀏覽器中打開
open index.html  # macOS
start index.html # Windows
xdg-open index.html # Linux
```

### 方式二：本地 Web 服務器
```bash
# Python 3
python -m http.server 8000

# 訪問 http://localhost:8000
```

## 模型清單

| 模型 | 架構 | 參數 | 最低記憶體 | 效能分 |
|------|------|------|----------|--------|
| Gemma 4 E4B | Dense Edge | 4B eff. | 6 GB | 68 |
| Qwen 3.5 9B | Dense | 9B | 8 GB | 82 |
| DeepSeek R1-Distill 7B | Dense Distill | 7B | 6 GB | 70 |
| Phi-4 Mini | Dense | 15B | 12 GB | 74 |
| DeepSeek R1-Distill 14B | Dense Distill | 14B | 12 GB | 78 |
| Gemma 4 26B A4B | MoE | 26B/3.8B | 20 GB | 87 |
| Qwen 3.5 35B-A3B | MoE | 35B/3B | 22 GB | 88 |
| DeepSeek R1-Distill 32B | Dense Distill | 32B | 20 GB | 85 |
| Gemma 4 31B IT | Dense | 31B | 24 GB | 93 |
| Qwen 3.5 122B-A10B | MoE | 122B/10B | 72 GB | 91 |

## 推論工具推薦

- **Ollama** - 所有平台入門（最簡單）
- **LM Studio** - Windows/Mac 圖形介面
- **llama.cpp** - 進階調校、細粒度控制
- **mlx-lm** - Mac 最高性能

## 技術要點速查

### VRAM 計算公式
```
VRAM 總佔用 = 模型權重 + KV Cache + 執行期開銷
模型權重 ≈ 參數量(B) × 量化位元 ÷ 8 (GB)
```

### 量化選擇
- **Q4_K_M** ✓ 大多數用戶首選（28% 原始大小，極小品質損失）
- **Q5_K_M** 升級版（35% 大小，幾乎無損）
- **Q8_0** 最高品質（53% 大小）

### Mac 統一記憶體規則
```
可用模型記憶體 ≈ 統一記憶體 × 65%
16 GB → 約 10-11 GB 可用
24 GB → 約 14-17 GB 可用
```

## 數據更新

最後驗證日期：**2026 年 4 月 13 日**

資料來源：
- HuggingFace
- Google DeepMind
- Meta AI
- Alibaba Qwen
- Mistral Docs
- llama.cpp
- Apple ML Research

## 許可證

本項目基於開源精神創建，旨在幫助社區選擇和部署本地 LLM。

## 貢獻

歡迎提交 Issue 或 Pull Request 以改進本指南！

---

*由 Claude Sonnet 4.6 生成並核實*