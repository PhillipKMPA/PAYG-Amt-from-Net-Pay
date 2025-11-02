# KMP Reverse Pay Calculator — Australia FY26

Convert **net → gross**, compute **PAYG** using ATO Schedule 1 (resident scales), and add **Super at 12%**.  
Assumptions: **TFN provided**, **no STSL**, **no pre/post-tax deductions**.

> **What it is:** a single-file website (`index.html`). Open it in your browser—no build tools, no dependencies.

---

## Try it
- Download `index.html`
- Double-click to open in your browser

**Inputs**
| Field | Options |
|---|---|
| Net payment | Dollar amount (e.g. 2,350.00) |
| Pay frequency | Weekly / Fortnightly / Monthly |
| Tax-free threshold | Yes (Scale 2) / No (Scale 1) |

**Outputs**
- **Gross for period**
- **PAYG withholding**
- **Super (12%)**
- **Check:** Gross − PAYG ≈ Net

---

## Accuracy & notes
- Uses **ATO Schedule 1 weekly coefficients** and official weekly↔period conversion rules.  
- **Rounding:** cents ignored in weekly withholding; period withholding = weekly×2 or ×13/3, **then** ignore cents again.  
- **Monthly quirk:** if a monthly gross ends in **.33**, add $0.01 before the 3/13 conversion (per ATO method).  
- No STSL logic in this version (you can add it later if needed).

**Cross-check:**  
Use the official ATO **Tax Withheld Calculator** to verify your results.

---

## Customise (branding)
- Replace the logo `<img>` `src` with your firm’s logo URL or place `logo.png` next to `index.html` and set `src="logo.png"`.
- Update the page title and header text as needed.

---

## Deploy (GitHub Pages)
1. Create a public repo (e.g. `reverse-pay-calculator`).
2. Commit `index.html` (and your logo if used).
3. In **Settings → Pages**, set **Source** to “Deploy from a branch” (e.g. `main`, root).
4. GitHub will give you a public URL shortly.

*Alternative:* Drag-and-drop to Netlify for an instant link.

---

## Development
It’s pure HTML/CSS/JS. Open `index.html` in **VS Code**. Optional: install the **Live Server** extension for auto-refresh while editing.

Key constants:
- `SG_RATE = 0.12`  → Super Guarantee rate
- Resident scales with TFN are embedded as coefficient tables.

---

## Disclaimer
This tool implements ATO withholding **methods** for convenience only. It doesn’t provide tax advice and may not cover edge cases (e.g., STSL, offsets, irregular pay counts like 53 weekly / 27 fortnightly runs). Always verify with the ATO calculator and your payroll records.

---

## License
No License.
