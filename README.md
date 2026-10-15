# Aerospace BMSCE — Web Portal Redesign

**Live Deployment:** [https://ananyashreeas.github.io/AeroBMSCE_TASK_REPO/](https://ananyashreeas.github.io/AeroBMSCE_TASK_REPO/)

---

## 1. Flaws Observed in the Original Website

While inspecting and testing the original `AeroBMSCE_TASK_REPO` website, several structural bugs and UI/UX issues stood out:

* **Broken Hyperlinks and Navigation Issues:** Several navigation links and page cross-references across the header/footer were either broken, pointing to incorrect paths, or failing to route smoothly between the 5 core pages (`index.html`, `journey.html`, `projects.html`, `partners.html`, and `contact.html`).
* **Image Sizing and Aspect Ratio Distortions:** Multiple assets—including team gallery photos, airframe renders, and partner logos—suffered from improper sizing constraints, overflowing containers, or stretched aspect ratios across different screen widths.
* **Lack of Visual Consistency Across Pages:** Font pairings, button styles, spacing, and card layouts varied inconsistently from page to page, making the site feel disjointed rather than part of a unified web portal.
* **Poor Contrast and Partner Logo Legibility:** On `partners.html`, sponsor and ecosystem logos (such as DRDO, CSIR-NAL, Siemens, SimScale, and flow5) suffered from severe contrast issues against the background, making dark-text emblems nearly unreadable.

---

## 2. Design Route and UI/UX Decisions

To address these flaws, I took a **Deep-Space & Avionics HUD (Heads-Up Display)** design route tailored specifically to an aerospace engineering and UAV development team:

* **Avionics Telemetry Aesthetic:** I introduced a dark, high-contrast color palette accented with precision grid lines and an interactive HUD telemetry bar on the hero section alongside an exploded drone cutout. This immediately establishes a strong technical identity the moment a visitor or potential sponsor lands on `index.html`.
* **Information Architecture Across 5 Dedicated Pages:** Instead of overwhelming the user with long walls of text, I structured the content into scannable cards, timelines, and data ribbons:
  * **Home (`index.html`):** Added an immediate credibility stats ribbon right below the hero, followed by clean modular sections for *Who We Are (Propel Lab–3)*, *What We Do*, *Why It Matters*, and the *4 Competitive Squads*.
  * **Journey (`journey.html`):** Redesigned the 2018–2026 competition history into a structured chronological timeline highlighting podium finishes and awards alongside a dedicated photo gallery.
  * **Projects & R&D (`projects.html`):** Separated flagship hardware specs (*Flying Phantoms* drone and CAD airframe) from the 7 active/upcoming R&D tracks (DRDO defense project, indigenous flight controller, custom ESC, GPS-denied navigation, and morphing wings) using structured spec cards.
  * **Partners (`partners.html`):** Created distinct collaboration tiers with custom tier icons so prospective sponsors can immediately compare deliverables and value propositions.
  * **Contact (`contact.html`):** Framed the contact page around Propel Lab–3's exact campus location and GPS coordinates with an interactive, client-side validated transmission form.
* **Typography & Readability:** Tested and paired clean geometric display headings with highly legible technical monospace/sans-serif body text so dense engineering specifications and telemetry figures remain easy to read across both desktop and mobile viewports.

---

## 3. Problem / Edge Case Faced and How I Solved It

### The Problem: Dual-Contrast Partner Logos & Asset Visibility on a Dark Theme
While building `partners.html` and the global navigation bar, I ran into a major visual edge case with the official partner and sponsor logos (`drdo.png`, `csir-nal.png`, `siemens.png`, `simscale.png`, `flow5.png`, `drkstore.png`, and `uav-marketplace.png`). 

Because the redesigned portal uses a deep-space dark theme, several official logos that contained dark navy or black typography/emblems became almost completely invisible against the page background. Conversely, simply forcing a white background card behind every logo broke the dark aerospace aesthetic and caused light/white-tinted logos to disappear.

### How I Worked Around It
1. **Visual Auditing & Contrast Testing:** I created isolated test sheets and montage comparisons (`logos_contrast_test.jpg` and `logos_montage.jpg`) to inspect the alpha channels and color values of every single partner logo against different background shades.
2. **Dual-Contrast Ecosystem Showcase:** Rather than applying a single one-size-fits-all CSS filter (like `filter: invert(1)`, which distorts official brand colors on multi-color emblems like DRDO and CSIR-NAL), I engineered a **dual-contrast logo showcase** in CSS. Logos with dark typography/details were assigned subtle, high-contrast frosted surface containers (`light-surface` cards with balanced padding and border highlights), while light/monochrome logos were styled to sit cleanly on dark glassmorphic containers.
3. **Result:** Every partner logo retained its authentic, unmodified brand colors while remaining 100% legible and visually balanced within the dark UI theme.
