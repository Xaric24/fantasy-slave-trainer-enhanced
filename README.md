# Fantasy Slave Trainer — Enhanced Edition (v0.6 Mod)

A polished, performance-optimized, and visually overhauled mod of the SugarCube/Twine text-based game **Fantasy Slave Trainer** (v0.6 Beta). 

This mod preserves all original gameplay mechanics, narrative content, and balance while fixing underlying code bugs, overhauling the user interface, improving text-generation speed, and completing unfinished engine stubs.

---

## 🎨 Visual Overhaul Features
*   **Design System & Theme:** Built entirely on a modern CSS design system utilizing 50+ customizable CSS custom properties. Implements a rich dark fantasy theme with charcoal/indigo backgrounds, warm gold accents, and amethyst highlights.
*   **Modern Typography:** Automatically loads and displays **Cinzel** (for fantasy headings and labels) and **Inter** (for clean, highly-readable body text) from Google Fonts, complete with robust local system font fallbacks.
*   **Clean Tables:** Upgraded all tables (inventory, combat, attributes) to feature gold header styling, clean row margins, alternating background rows (for readability), and hover highlighting.
*   **Interactive Tooltips:** Replaced the default, abrupt hover windows with slide-in, drop-shadowed tooltips styled with a distinct gold left accent bar.
*   **Responsive Layout:** Fully optimized for mobile viewports (breakpoint at 768px). Sidebar automatically collapses/hides, tables scale to fit maximum width (`100%`), and font sizes scale down comfortably on touch interfaces.
*   **Themed Scrollbars & Dialogs:** Custom thin scrollbars and fully styled popups (Save/Load/Settings menus) with rounded borders and a purple ambient drop-glow.

---

## 🔧 Bug Fixes & Code Correctness
*   **Unreachable Cock Size 1 (`slave.cock.current`):** Fixed a critical object comparison bug (`slave.cock == 1` instead of `.current`) that made 3-inch size descriptors completely unreachable in-game.
*   **Always-Visible Inventory Link:** Fixed the `$endweeek` spelling typo in main checks so the inventory link is correctly hidden during end-of-week processing.
*   **September Auction House:** Corrected the `"Septmember"` typo so the auction house successfully opens and allows players to sell/bid in September.
*   **Missing Argument stamina checks (`getStamina()`):** Patched the function to return `0` instead of a truthy object (`{actor: 0, patient: 0}`) on missing arguments to prevent conditional check bypasses in SugarCube markup.
*   **Variable Leakage (`simulateStimulation()`):** Fixed a variable bleed-through bug where multi-partner combat loops would leak simulation stats from one partner to the next by resetting `data = null` inside the loop scope.
*   **Keyboard Handlers:** Fixed Key 2 targeting the wrong action slot (`#threeAct` instead of `#twoAct`) and removed duplicate bindings on Key 4.
*   **Assignment vs Comparison Operator Typos:** Fixed 6 occurrences of `==` (comparison) instead of `=` (assignment) in `<<set>>` macros for neck and underwear clothing slots.
*   **Typo Correction:** Fixed spelling mistakes throughout dialogue and status strings, including "peircing" -> "piercing", "monsterous" -> "monstrous", "Dranied" -> "Drained", "torid" -> "torrid", etc.

---

## ⚡ Performance & Quality-of-Life Optimizations
*   **Constant-Time Thesaurus Lookup:** Converted the procedural text generator's `thesaurus()` function from a ~570-line linear `if/else` scan (which executed hundreds of times per action) into a pre-compiled `O(1)` dictionary key-value lookup. This eliminates text-generation micro-stutters during combat scenes.
*   **Dynamic eval() Removal:** Replaced `eval(tuts)` inside the core `script()` engine with direct dictionary references, improving execution speed and security.
*   **Filled Body Descriptors:** Completed the empty `descriptor("body", character)` stub, allowing the game to dynamically generate body and figure descriptions matching the slave's weight, skintone, and gender flags.
*   **Stat Boundary Overflow Guards:** Fixed obedience, fear, trust, affection, and hate utility checks to use `>=` or `<=` instead of strict `==` at their highest values (so stats exceeding the max tier no longer return `undefined` or display blank names).

---

## 📥 Installation

1.  **Back up** your existing save (export your save state from the Settings menu or duplicate your original game HTML file).
2.  Download the latest [Fantasy Slave Trainer -Beta.html](Fantasy%20Slave%20Trainer%20-Beta.html) file.
3.  Replace your original `.html` file with this file.
4.  Open the file in any modern browser (Chrome, Firefox, Safari) and load your save game.

---

## 🛠️ Modifying the Theme

To customize the colors, typography, or styling:
1.  Open the HTML file in a text editor.
2.  Scroll down to the `:root` styling block (starting around line 108).
3.  Modify variables like `--gold` (e.g. changing it to blue or red) to instantly change the accent theme of the entire game interface.
