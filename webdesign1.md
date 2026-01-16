Create a high-fidelity "Deep Void" Financial Dashboard using React, Tailwind CSS, and Framer Motion. The aesthetic is high-contrast dark mode: Background #0f172a (Slate 900), Surface #1e293b (Slate 800), Accent #3b82f6 (Blue 500).
Layout & Architecture:
Sidebar: Fixed width (250px). "ScaleUp" logo top left. Navigation items (Dashboard, Orders, Products) use a shared layout animation—when a tab is selected, a dark gray rounded background slides to that position.
Top Bar: Large H1 "Dashboard". Right-aligned "Last 30 days" button with an outline style (border-slate-700).
Metrics Grid: 4 Cards. Each card has a border-slate-700, white label, large H2 value, and a small trend indicator. The trend indicator (e.g., +12.5%) uses text-emerald-400 for positive and text-rose-400 for negative.
Main Chart: A large container taking up the rest of the screen.
Use Recharts or Visx.
The Line: Thick stroke (3px), color #3b82f6. Curve type: monotone.
The Fill: A <defs> linear gradient fading from #3b82f6 (opacity 0.3) at the top to transparent at the bottom.
The Axes: Minimalist. Hide Y-axis lines. X-axis shows "Week 1", "Week 2", etc.
Animation Specification:
Sequence: Staggered entrance. Sidebar (Instant) -> Top Bar (Fade Down) -> Cards (Fade Up, stagger 0.1s) -> Chart (Draw Line).
Number Logic: Use react-countup for the dollar amounts inside the cards. They should count up from 0 over 1.5s on load.
Chart Entrance: Animate the stroke-dashoffset of the chart line so it "draws" itself from left to right over 2 seconds.
Hover Effects: On chart hover, display a custom Tooltip that follows the cursor (magnetic X-axis snapping).
Font: Inter. Use tabular-nums for all currency data to prevent jitter during animation.
