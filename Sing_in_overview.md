# Sign In — UI Layout Overview
 
> **Note:** This file documents the `Sing_in` login window — a separate component of the MR.SLADOF tool.
 
---
 
## 📌 General Info
 
| Property | Value |
|----------|-------|
| Name | `Sing_in` |
| Inherits from | `QWidget` (PySide6) |
| Window size | `400 × 600` px (fixed) |
| Background color | `color.bg_main` |
 
---
 
## 🗂️ Component Structure
 
### 1. Logo
 
| Component | Type | Position (x, y) | Size |
|-----------|------|-----------------|------|
| `logo` | Image | (100, 20) | 200×200 |
 
- **Image:** `logo_tool.png` — opacity `2`
 
---
 
### 2. Boxes
 
| Component | Position (X, Y) | Dimensions (Q×L) | Purpose |
|-----------|----------------|------------------|---------|
| `my_frame_001` | (50, 250) | 300×300 | Main card frame (form area) |
| `my_frame_002` | (60, 220) | 280×65 | Header label frame |
 
> All boxes share: `border_color=color.border` , `border_width=3` , `border_radius=15`
> - `my_frame_001` background: `color.card_bg`
> - `my_frame_002` background: `color.card_alt`
 
---
 
### 3. Labels
 
| Component | Text | Position (X, Y) | Size | Style |
|-----------|------|-----------------|------|-------|
| `label_001` | `Welcome to Sladof OSINT` | (50, 215) | 300×50 | Bold, `size_3`, `fonts.text_large` |
| `label_002` | `Log in to your account` | (48, 240) | 300×50 | Bold, `size_2`, `fonts.text_medium` |
 
Both labels use `color.text_primary`.
 
---
 
### 4. Input Fields
 
| Component | Placeholder | Position (X, Y) | Size | Echo Mode |
|-----------|-------------|-----------------|------|-----------|
| `email_input` | `Email` | (70, 315) | 260×40 | Normal |
| `password_input` | `Password` | (70, 370) | 260×40 | `QLineEdit.Password` |
 
**Shared input properties:**
 
```
font_size          = SizeFonts.size_2
text_color         = color.text_primary
bg_color           = color.card_bg
border_color       = color.border
border_focus_color = color.input_border
border_size        = 1
radius             = 8
```
 
---
 
### 5. Buttons
 
| Component | Text | Position (x, y) | Size | Function |
|-----------|------|-----------------|------|----------|
| `toggle_btn` | `🔒` | (300, 377) | 25×25 | `toggle_password_visibility(password_input, toggle_btn)` |
| `login_btn` | `Sing in` | (145, 480) | 120×30 | `button_sing_in(self)` |
 
**`toggle_btn` style:** fully transparent background, no border — acts as an icon overlay on the password field.
 
**`login_btn` shared properties:**
 
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
 
### 6. Input Access (Runtime)
 
```python
email    = self.email_input.text()     # get email field content
password = self.password_input.text()  # get password field content
print(email, password)
```
 
> ⚠️ These lines run at `__init__` time — both values will be empty strings on startup. Move them inside `button_sing_in()` for actual use.
 
---
 
## 📦 Imports & Dependencies
 
```python
from PySide6.QtWidgets                                import QWidget, QLineEdit
from all_data.core.theme.all_color_tool               import color
from all_data.image.Assets                            import Assets
from all_data.core.utils.add_image                    import add_image
from all_data.core.utils.add_box                      import add_box
from all_data.core.utils.add_text                     import add_text
from all_data.core.fonts.fonts_list                   import fonts
from all_data.core.fonts.size_fonts                   import SizeFonts
from all_data.core.utils.add_input                    import add_input
from all_data.core.utils.sing_in.button               import button_sing_in
from all_data.core.utils.add_button                   import add_button
from all_data.core.utils.sing_in.toggle_password      import toggle_password_visibility
```
 
---
 
## 🗺️ Layout Diagram (approximate)
 
```
┌───────────────────────────────┐
│                               │
│       [ Logo  200×200 ]       │
│                               │
│     ╔═══════════════════╗     │
│     ║ Welcome to Sladof ║     │  (frame_002)
│     ║ Log in to account ║     │
│     ╚═══════════════════╝     │
│   ╔═══════════════════════╗   │
│   ║                       ║   │
│   ║  [   Email input   ]  ║   │
│   ║  [ Password input  ]  ║   │  (frame_001)
│   ║                       ║   │
│   ║      [ Sign in ]      ║   │
│   ║                       ║   │
│   ╚═══════════════════════╝   │
└───────────────────────────────┘
```
 
---
 
*Last updated: March 2026 — MR.SLADOF Tool Project*
