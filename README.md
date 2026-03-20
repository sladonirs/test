# Basic Interface — UI Layout Overview
 
> **ملاحظة:** هذا الملف يوثّق جزءًا واحدًا فقط من أداة أكبر، وهو الواجهة الرئيسية `Basic_interface`.
 
---
 
## 📌 معلومات عامة
 
| الخاصية | القيمة |
|---------|--------|
| الاسم | `Basic_interface` |
| الموروث من | `QWidget` (PySide6) |
| حجم النافذة | `1100 × 700` px (ثابت) |
| لون الخلفية | `color.bg_main` |
 
---
 
## 🗂️ هيكل المكوّنات
 
### 1. الشعار والعنوان
 
| المكوّن | النوع | الموضع (x, y) | الحجم |
|---------|-------|--------------|-------|
| `logo` | صورة | (70, 15) | 150×150 |
| `label_logo` | نص | (20, 170) | 250×30 |
 
- **الصورة:** `logo_tool.png` — شفافية `0.9`
- **النص:** `====>> MR.SLADOF <<====` — خط عريض، لون `color.text_title`
 
---
 
### 2. الصناديق (Boxes)
 
| المكوّن | الموضع (X, Y) | الأبعاد (Q×L) | الغرض |
|---------|--------------|--------------|-------|
| `add_box_001` | (10, 166) | 270×39 | إطار حول تسمية الشعار |
| `add_box_002` | (10, 210) | 270×410 | إطار حول منطقة الأزرار |
| `add_box_003` | (10, 630) | 270×60 | إطار حول زر الإعدادات |
 
> جميع الصناديق تشترك في: `border_color=color.border` ، `border_width=3` ، `border_radius=15` ، `background_color=color.card_bg`
 
---
 
### 3. أزرار القائمة الجانبية (btn 1–10)
 
الأزرار العشرة مرتّبة عموديًا داخل `add_box_002`، كل زر بارتفاع `30px` وعرض `250px`.
 
| الزر | النص | الموضع y | الدالة المرتبطة |
|------|------|----------|-----------------|
| `add_button_001` | `btn.text_btn_1` | 220 | `btn.btn_1()` |
| `add_button_002` | `btn.text_btn_2` | 260 | `btn.btn_2(self)` |
| `add_button_003` | `btn.text_btn_3` | 300 | `btn.btn_3(self)` |
| `add_button_004` | `btn.text_btn_4` | 340 | `btn.btn_4(self)` |
| `add_button_005` | `btn.text_btn_5` | 380 | `btn.btn_5(self)` |
| `add_button_006` | `btn.text_btn_6` | 420 | `btn.btn_6(self)` |
| `add_button_007` | `btn.text_btn_7` | 460 | `btn.btn_7(self)` |
| `add_button_008` | `btn.text_btn_8` | 500 | `btn.btn_8(self)` |
| `add_button_009` | `btn.text_btn_9` | 540 | `btn.btn_9(self)` |
| `add_button_010` | `btn.text_btn_10` | 580 | `btn.btn_10(self)` |
 
**خصائص مشتركة لجميع الأزرار:**
 
```
border_size    = 3
border_radius  = 15
bg_color       = color.btn_primary
hover_color    = color.btn_primary_hover
pressed_color  = color.btn_primary_active
text_color     = color.btn_disabled
bold           = True
```
 
---
 
### 4. زر الإعدادات
 
| المكوّن | النص | الموضع (x, y) | الدالة |
|---------|------|--------------|--------|
| `add_button_011` | `Settings ⚙️` | (20, 645) | `Settings_function.settings()` |
 
---
 
## 📦 الاستيرادات والتبعيات
 
```python
from PySide6.QtWidgets import QWidget
from all_data.core.theme.all_color_tool    import color
from all_data.core.fonts.fonts_list        import fonts
from all_data.core.fonts.size_fonts        import SizeFonts
from all_data.image.Assets                 import Assets
from all_data.core.utils.add_image         import add_image
from all_data.core.utils.add_text          import add_text
from all_data.core.utils.add_button        import add_button
from all_data.core.utils.add_box           import add_box
from all_data.core.utils.Basic_interface.Button_functions import btn
from all_data.core.Settings.function       import Settings_function
```
 
---
 
## 🗺️ تخطيط الواجهة (تقريبي)
 
```
┌─────────────────────────────────────────────────────────┐
│  [Logo 150×150]                                         │
│  ╔══════════════════════╗                               │
│  ║  ====>> MR.SLADOF <<=║  (box_001)                   │
│  ╚══════════════════════╝                               │
│  ╔══════════════════════════╗                           │
│  ║  [ btn_1  ]              ║                           │
│  ║  [ btn_2  ]              ║                           │
│  ║  [ btn_3  ]              ║  (box_002)                │
│  ║  ...                     ║                           │
│  ║  [ btn_10 ]              ║                           │
│  ╚══════════════════════════╝                           │
│  ╔══════════════════════════╗                           │
│  ║  [ Settings ⚙️ ]         ║  (box_003)               │
│  ╚══════════════════════════╝                           │
└─────────────────────────────────────────────────────────┘
```
 
---
 
*آخر تحديث: March 2026 — MR.SLADOF Tool Project*
