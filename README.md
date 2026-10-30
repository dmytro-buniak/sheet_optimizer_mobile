**Optymalizator Cięcia Arkuszy (Sheet Cutting Optimizer)**
An intuitive, lightweight, single-page web application designed for 2D rectangular cutting optimization. It calculates optimal nesting layouts for sheet materials (e.g., sheet metal, wood panels, plastics), minimizes material waste, and helps estimate material requirements based on production metrics or SAP ERP (MB51) data.

### 🌟 **Key Features**
* **MaxRects Nesting Algorithm:** Employs a Fast Best-Area-Fit (BAF) heuristic to pack rectangular parts tightly onto master sheets.
* **Kerf / Saw Blade Width Support:** Adjusts for saw blade thickness or laser/waterjet kerf clearance between cuts.
* **Part Rotation Controls:** Per-part toggle to allow or prohibit 90° rotation during packing.
* **High-Demand (HD) Tagging:** Prioritizes high-demand parts and highlights SAP material codes.
* **SAP / MB51 Demand Calculator:** Automatically calculates required cutting quantities over configurable time periods (daily, weekly, monthly) using SAP MB51 stock movement data.
* **Standard & Custom Sheet Size Evaluator:** Compare custom sheet dimensions against standard stock sizes to automatically discover the best sheet size based on utilization rate, waste percentage, or total sheet count.
* **Visual Canvas Rendering:** Scalable, high-DPI HTML5 Canvas preview showing detailed sheet layouts with part names, dimensions, kerf boundaries, and SAP codes.
* **Mobile & Touch Friendly:** Built with a responsive dark-mode UI optimized for touch interaction on tablets and smartphones.
* **Zero Dependencies:** Pure HTML5, CSS, and vanilla JavaScript—no build steps, npm packages, or external frameworks required.

### 🛠 **Tech Stack**
* **HTML5:** Native canvas rendering and responsive markup.
* **CSS3:** Custom CSS properties (variables), Flexbox, CSS Grid, dark mode theme.
* **JavaScript:** Custom MaxRects packing algorithm, DOM manipulation, responsive canvas scaling.

📖 **How to Use**

### **1. Parts Tab (⚙️ Części)**
* Set your primary sheet width (Szerokość arkusza) and saw kerf (Szczelina / piła).
* Adjust quantities for each part using the stepper buttons (+ / -).
* Toggle the rotation button (⟳) on individual parts to enable or disable 90° rotation during layout generation.
* Click ▶ Optymalizuj układ cięcia to execute the optimization.

### **2. Layout Tab (📐 Układ)**
* View generated layout diagrams for each sheet using the top navigation pills.
* Inspect summary statistics: total sheets used, average utilization %, waste %, and placed parts ratio.
* Hover or view part dimensions, rotation indicators (↺), and SAP reference codes drawn directly on the canvas preview.

### **3. MB51 Calculator Tab (📊 MB51)**
* Input demand figures directly from your SAP MB51 material movement report.
* Select period type (Month, Day, or Week) and specify the coverage target.
* Click ↑ Zastosuj ilości do Części to automatically populate required quantities into the main optimizer.

### **4. Sheet Size Finder Tab (📋 Format)**
* Enter custom sheet dimensions or click 🔍 Znajdź najlepszy format arkusza.
* Compare packing efficiency across common standard sheet sizes (e.g., $$1220 \times 2440\text{ mm}$$, $$1130 \times 1100\text{ mm}$$, $$1250 \times 2500\text{ mm}$$).
* Sort standard sizes by Utilization, Waste, Sheet Count, or Total Area.

### 🧩 **Algorithm Overview**
* The cutting algorithm implements a 2D MaxRects (Maximal Rectangles) bin-packing algorithm with Best-Area-Fit (BAF) placement rules:
* Parts are pre-sorted by priority (High Demand first) and area ($$W \times H$$).
* For each part, the algorithm evaluates all free rectangular spaces in the current sheet.
* The fit that leaves the minimal remaining space dimension is selected.
* If a part doesn't fit on the active sheet, a new sheet is spawned until all parts are placed or flagged as non-fitting.

📄 **License**
This project is open-source and available under the MIT License.
