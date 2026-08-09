# 交接摘要｜作品集 pyRevit（給本機 Agent）

> 用途：開**本機 Cursor**、工作區設為 `C:\Users\USER\Desktop\MyRevitScripts` 後，把本檔給新 Agent 讀。  
> 勿提交進 `REVIT_MCP_study` 正式內容；用完可刪或移到 `d:\桌面\2026\`。

---

## 一、請先讀的本機檔

| 檔 | 用途 |
|----|------|
| `d:\桌面\2026\A1_flowchart_final.md` | A1 定稿 |
| `d:\桌面\2026\A2_flowchart_final.md` | A2 定稿 |
| `d:\桌面\2026\Technical_Projects_PDF_outline.md` | PDF 四頁大綱 |
| `d:\桌面\2026\PDF_TODO_manual_vs_done.md` | 已完成／待手動 |
| `d:\桌面\PDF_review_screenshots_and_naming.md` | 截圖校對 |
| `C:\Users\USER\Desktop\MyRevitScripts\VDC_Tools.extension\Audit.tab\QAQC.panel\AvoidA2.pushbutton\script.py` | **立刻要改的腳本** |
| 同面板 `AuditA1.pushbutton\script.py`、`Clear.pushbutton\script.py` | 相關工具 |

工作區請開：`C:\Users\USER\Desktop\MyRevitScripts`（不要只用雲端 / 不要只開 REVIT_MCP_study）。

---

## 二、已定案

### 工具列
- 頁籤：`Audit`
- 面板：`QA/QC`（原 Check；`QAQC.panel` + `bundle.yaml` title）
- 按鈕：`AuditA1`／`AvoidA2`／`Clear`（原 ClearA1；只清圖形覆寫，不還原參數／座標）

### A1
- 正式規則：mark 缺漏 → 上黃列冊 → **對 2D 圖資補值**（不是一律填 LV）
- LV = Demo 暫定值，僅驗證寫回閉環
- 對外數字 **N／M／K／R = 29／2／2／0**
- 對話框應與 A2 同款 N/M/K/R 風格（含「掃描 N：29」、Demo LV 聲明）
- `Clear` 是**獨立按鈕**：AuditA1 先回報對話框；Clear 事後另按  
  → 流程圖不要把 Clear 畫進 AuditA1 subgraph；順序是「回報 →（事後）Clear」

### A2
- 規則：自動**只避讓一次** → 對全部柱／梁全域複驗 → 不成 → 列冊寫問題 PPT（**無 5 次迴圈**）
- 方向：撞柱 ±X；撞梁 -Z；淨空 75mm；單次位移上限 500mm
- 後期實測數字：**29／2／1／1**（待人工 ID **64450**）
- 作品集預埋管：**統一灰材質**（不分消防紅／電管藍）
- 待人工色：**洋紅**（不是紅）
- 對話框**不要**出現「作品集模型預埋管統一灰材質…」等內部註記

### 環境／對外
- Revit **2022**
- 開源 MCP：`shuotao/REVIT_MCP_study`（PDF 寫 repo 名即可）
- 個人 GitHub `yuhan-arch`：**不放連結**
- 定位：AI 協同工具導入（Cursor／MCP 生成程式；本人定問題、驗收、驗證）

### 色碼（作品集）

| 色 | 意義 |
|----|------|
| 灰 | 預埋統一材質 |
| 黃 | A1 mark 缺漏 |
| 橘 | A2 撞柱 |
| 綠 | A2 撞梁 |
| 洋紅 | A2 待人工／寫 PPT |

---

## 三、立刻請本機 Agent 做

1. **改本機**  
   `...\QAQC.panel\AvoidA2.pushbutton\script.py`
   - 待人工覆寫用 `magenta = DB.Color(255, 0, 255)`
   - 對話框文字改「洋紅」
   - **刪除**任何「作品集模型預埋管…」「待人工用紅較直覺」字串
2. 請使用者 **Reload pyRevit** 後跑 AvoidA2，確認對話框已是洋紅、無作品集註記
3. 檢查並修正 `d:\桌面\2026\A1_flowchart_final.md`（若尚未修好）：
   - 章節編號：不可有兩個「三、」；圖例起改「四、」並順延
   - §一：改為強調 **29／2／2／0**（不是 29／2／0）
   - 圖例加「灰＝統一材質」
   - Mermaid：`Clear` 在 AuditA1 框**外**；先回報再 Clear
4. 若改 A2 定稿圖例：待人工維持**洋紅**；預埋材質為灰

---

## 四、使用者仍須手動（Agent 可提醒，不必代做）

- [ ] 重截 A1-2（新對話框含 N=29；視角對齊 A1-1）
- [ ] 重截 A2-1／A2-3（工具列顯示 QA/QC、Clear）
- [ ] 全灰材質後重截／重錄 Demo
- [ ] A2-1 與 A2-3 並排放 PDF P4（證明 Clear 可還原覆寫）
- [ ] 履歷：對圖補值用詞、姓名／聯絡／公司；個人 GitHub 不放

---

## 五、禁止

- 不要把作品集腳本／定稿提交進 `REVIT_MCP_study` 正式路徑
- 不要在雲端 Agent 假裝寫 `C:\...`（會變成假檔）
- 不要把待人工改回紅色（已定洋紅）
- 不要恢復 A2「最多 5 次」迴圈

---

## 六、驗證口令（改完對這幾句）

AvoidA2 對話框應類似：

```text
避讓流程完成！
掃描 N：29 件預埋管配件
結構對照：柱 9／梁 23
干涉 M：2 處
已避讓 K：1 處
待人工 R：1 處（洋紅；請列問題報告／PPT）

橘色：撞柱｜綠色：撞梁｜洋紅：一次避讓後仍無法在約束內解決
規則：自動只避讓一次 → 全域複驗 → 不成則交問題報告
淨空 75mm｜單次位移上限 500mm
待人工 ID：64450
```

（K／R 以當次模型為準；重點是「洋紅」＋沒有作品集註記。）
