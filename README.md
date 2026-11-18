# statistical-consulting_final (SES)
The Effect of Students' Socioeconomic Status on Academic Performance: A Causal Inference Approach

# Statistical Consulting: Final Project
## 學生社會經濟地位（SES）對學業表現之影響 — 兼論因果推論與中介分析
**Group 5:** 潘皓心、劉育甄、何佩勳、黃芯鈺、何淑雯  
**日期:** 2025-06-19

---

## 📋 專案簡介 (Background & Objectives)
教育常被視為促進社會階層流動的重要手段，但學生的學業表現往往深受其家庭社會經濟地位（Socioeconomic Status, SES）影響。本專案基於 Kaggle 上的學生表現資料集（Students Performance Dataset），跳脫傳統僅以「相關性」或「迴歸分析」探討關聯的侷限，改從**因果推論（Causal Inference）**的角度出發：
1. **直接與間接效應評估**：探討家長教育程度（$\text{edu}$）與午餐類型（$\text{lunch}$）等 SES 代理變數對學生學業表現（數學、語文、三科平均）的因果效應。
2. **中介機制檢驗**：建構中介分析與結構方程模型（SEM），檢驗學校提供的「完成備考課程（$\text{course}$）」是否在 SES 與學業成績之間扮演顯著的中介角色。
3. **穩健性與敏感度分析**：結合 10 種不同的因果推論方法與 E-value，全面評估結果對未觀察混淆變項的穩健性。

---

## 📂 資料來源與前處理 (Data Description & Preprocessing)
* **原始資料**：`StudentsPerformance.csv`（共 1,000 筆觀察值，12 個變數）。
* **核心變數說明**：
  * **Treatment (處置變項)**：家長教育程度（$\text{edu}$）、學生午餐類型（$\text{lunch}$）、是否完成備考課程（$\text{course}$）。
  * **Outcome (結果變項)**：數學分數（$\text{math.score}$）、語文分數（$\text{reading}$ 與 $\text{writing}$ 平均，$\text{language}$）、整體平均成績（$\text{results}$）。
  * **Confounders (混淆變項)**：性別（$\text{gender}$）、種族/族群（$\text{race/ethnicity}$）。
* **資料清洗重點**：
  * 將家長教育程度二元化（$\text{edu} = 1$ 代表具大學以上背景，$\text{edu} = 0$ 代表其餘）。
  * 將午餐類型與備考課程轉為數值或二元變數以利建模。

---

## ⚙️ 系統需求與所需 R 套件 (Prerequisites & Libraries)
本專案完全以 R 語言進行分析與建模，執行前請確保安裝以下套件：

```R
install.packages(c(
  "fastDummies", "Matching", "ipw", "survey", "estimatr", 
  "dplyr", "tidyr", "GGally", "kableExtra", "car", "cobalt", 
  "boot", "readr", "lavaan", "Hmisc", "mediation", "broom", "EValue"
))
