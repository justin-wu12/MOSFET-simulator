# MOSFET-simulator
# ⚡ MOSFET Physics Simulator (MOSFET 物理模擬器)

![React](https://img.shields.io/badge/Built_with-React-61DAFB?style=flat-square&logo=react)
![Physics](https://img.shields.io/badge/Physics-Semiconductor-orange?style=flat-square)
![Status](https://img.shields.io/badge/Version-v3.0-blue?style=flat-square)

An interactive educational tool designed to visualize the operation of Metal-Oxide-Semiconductor Field-Effect Transistors (MOSFETs).
(這是一個專為視覺化金屬-氧化物-半導體場效電晶體 (MOSFET) 運作原理而設計的互動式教育工具。)

This project helps students intuitively understand complex concepts like **Channel Pinch-off** and **Channel Length Modulation (CLM)** through dynamic graphics and real-time data plotting.
(本專案透過動態圖形與即時數據繪圖，幫助學生直觀理解「通道夾止」與「通道長度調變」等複雜概念。)

## 📸 Screenshots & Evolution (截圖與演進)

### v3.0: Advanced Simulation with CLM (進階模擬與 CLM 效應)
The latest version introduces the **Channel Length Modulation (CLM)** effect, allowing users to adjust the $\lambda$ parameter and observe the finite output resistance ($r_o$) in the saturation region.
(最新版本引入了 **通道長度調變 (CLM)** 效應，允許使用者調整 $\lambda$ 參數，並觀察飽和區有限的輸出阻抗 $r_o$。)

![MOSFET v3.0 Interface](image_2025de.png)
*(Includes real-time calculation of $r_o$, $g_m$, and $V_{ov}$ / 包含 $r_o$, $g_m$ 與 $V_{ov}$ 的即時計算)*

### v1.0: Core Functionality (核心功能)
The initial version focused on the basic operation regions: Cutoff, Triode, and Saturation.
(初始版本專注於基本操作區域：截止區、三極管區與飽和區。)

![MOSFET v1.0 Interface](image_20263d.png)

## 🧮 Physics Models (物理模型)

The simulator implements the standard **Square-Law Model** with extensions for non-ideal effects.
(本模擬器實作了標準的**平方律模型**，並針對非理想效應進行了擴展。)

### 1. Drain Current ($I_D$) Equations
The current is calculated based on the region of operation:

* **Triode Region (三極管區)** ($V_{GS} > V_{TH}, V_{DS} < V_{ov}$):
    $$I_D = \mu_n C_{ox} \frac{W}{L} \left[ (V_{GS} - V_{TH})V_{DS} - \frac{1}{2}V_{DS}^2 \right]$$

* **Saturation Region (飽和區)** ($V_{GS} > V_{TH}, V_{DS} \ge V_{ov}$):
    With CLM correction factor $(1 + \lambda V_{DS})$:
    $$I_D = \frac{1}{2} \mu_n C_{ox} \frac{W}{L} (V_{GS} - V_{TH})^2 (1 + \lambda V_{DS})$$

### 2. Small Signal Parameters (小訊號參數)
* **Transconductance ($g_m$):** Represents the sensitivity of the drain current to changes in gate voltage ($\partial I_D / \partial V_{GS}$).
* **Output Resistance ($r_o$):** Derived from the CLM effect, representing the slope in the saturation region ($\partial I_D / \partial V_{DS} \approx \lambda I_D$).

## 🚀 Key Features (主要功能)

- **Interactive Visualization:** Dynamically renders the electron channel (n-channel) and depletion region changes.
  (互動式視覺化：動態渲染電子通道 (n-channel) 與空乏區的變化。)
- **Real-time Plotting:** Automatically plots $I_D-V_{DS}$, $I_D-V_{GS}$, and $g_m-V_{GS}$ curves.
  (即時繪圖：自動繪製 $I_D-V_{DS}$、$I_D-V_{GS}$ 與 $g_m-V_{GS}$ 曲線。)
- **Parameter Tuning:** Adjustable Gate Voltage ($V_{GS}$), Drain Voltage ($V_{DS}$), and Lambda ($\lambda$).
  (參數調整：可調整閘極電壓、汲極電壓與 Lambda 值。)
- **Data Dashboard:** Displays calculated values for Overdrive Voltage ($V_{ov}$), Transconductance ($g_m$), and Output Resistance ($r_o$).
  (數據儀表板：顯示過驅動電壓、轉導與輸出阻抗的計算數值。)

## 🛠️ Tech Stack (技術堆疊)

- **Frontend:** React.js, TypeScript
- **Visualization:** Canvas API / SVG for device cross-section rendering
- **Charting:** Recharts / Chart.js for characteristic curves

## 📦 Getting Started (開始使用)

```bash
# Clone the repository
git clone [https://github.com/your-username/mosfet-simulator.git](https://github.com/your-username/mosfet-simulator.git)

# Install dependencies
npm install

# Run the simulator
npm start
