# Crypto Tracker Dashboard — Architecture & System Design

## Overview
A high-performance real-time cryptocurrency portfolio tracker and analytics dashboard built with modern web technologies, adhering to strict WCAG 2.2 accessibility standards and professional data visualization guidelines.

---

## System Architecture Diagram

```mermaid
graph TD
    subgraph Client [Client Browser / Dashboard UI]
        UI[Tailwind UI & Interactive Components] --> ChartEngine[SVG / Canvas Visualization Engine]
        ChartEngine --> StateMgr[Reactive State Manager]
    end

    subgraph DataLayer [Data & API Services]
        StateMgr --> CoinAPI[CoinGecko / Binance WebSocket API]
        StateMgr --> LocalCache[IndexedDB / LocalStorage Cache]
    end

    subgraph Analytics [Analytics & Visualizations]
        CoinAPI --> PriceFeed[Live Price & Volume Feed]
        PriceFeed --> StatTiles[Hero Stat Tiles & KPI Cards]
        PriceFeed --> AreaChart[Portfolio Performance Area Chart]
        PriceFeed --> BarChart[Trading Volume Bar Chart]
        PriceFeed --> DonutChart[Asset Allocation Breakdown]
    end
```

---

## Data Flow & Sequence

```mermaid
sequenceDiagram
    participant User
    participant UI as Dashboard UI
    participant API as Crypto WebSocket Feed
    participant Store as Local Storage

    User->>UI: Opens Dashboard
    UI->>Store: Load cached portfolio preferences
    UI->>API: Establish WebSocket connection for BTC/ETH/SOL
    API-->>UI: Real-time price ticks & volume updates
    UI->>UI: Recalculate portfolio balance & re-render SVG charts
    UI->>User: Display live metrics with responsive tooltips
```

---

## Tech Stack
- **Frontend**: HTML5, Tailwind CSS, Vanilla JavaScript (ES6+), SVG Charts
- **Data Visualization**: Custom accessible SVG charts with hover crosshairs and tooltips
- **Deployment**: Vercel / Netlify / GitHub Pages
- **Testing**: Playwright E2E & unit tests
