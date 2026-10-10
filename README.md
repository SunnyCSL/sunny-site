# 陳思朗 Sunny Chan — 個人網站

靜態單頁個人網站。純 HTML + CSS，無 build step、無依賴、無外部字體。

## 本機預覽
```
python3 -m http.server 8755
```
開 http://127.0.0.1:8755

## 結構
- `index.html` — 單頁：Hero → 01 關於 → 02 工作 → 03 項目 → 04 點心·牛奶妹 → 05 聯絡
- `assets/site.css` — 全站樣式（技術製圖風設計語言）
- `assets/dimsum.jpg`、`assets/milky.jpg` — 狗相（900×900，已去 EXIF）

## 設計語言
技術製圖風結構 + 紫曜 Violet Aurora 色系。

- **結構**（來自製圖風）：兩側固定刻度尺、基線標尺、區段編號、等寬標籤、3px 直角
- **色系**（來自紫曜，`~/Projects/nexi-design-system/tokens.css`）：紫墨底
  `--ink-900:#0C0916`、`--surf-1:#171327`、紫階 `--violet-400:#A78BFA`、
  `--aurora` 簽名漸變

🔴 **紫曜鐵則：一屏一主角。** 極光漸變（`--aurora`）全站只准用一次 —— 現在用在
hero 名字。其餘元素一律降到 tint → surface → ghost，唔好再加第二個漸變主角。
紫色一定要用官方 token，唔好自己調色。

- `--rule` 控制兩側刻度尺寬度（手機會縮到 10px）
- 刻度線用紫調 `--tick` / `--tick-major`，唔好用灰色

## 內容原則
所有文字一律用一般性描述（車輛認證／流程工程／自動化），**不含**公司名、
客戶名、內部項目代號或任何基建資訊。改動前請保持這個原則。

## 上線前檢查
```bash
# 敏感字
grep -rniE "<公司名>|<客戶>|tailnet|~/Projects|skill" index.html assets/ README.md
# 相片 EXIF
python3 -c "from PIL import Image; print(len(Image.open('assets/dimsum.jpg').getexif()))"
```

## 未做
- 未有正式 domain
- 未有 OG 分享圖（social preview image）
