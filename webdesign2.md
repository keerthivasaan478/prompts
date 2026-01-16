Create a "Gamified" SaaS Dashboard for "ListingLaunchKit" using React, Tailwind CSS, and Framer Motion. The design aesthetic is "Educational Quest"—playful but professional.
Layout Architecture:
Sidebar: Slim (80px), fixed left, white background. Column of gray icons (Grid, Folder, Palette) that turn Emerald Green (text-emerald-500) on hover.
Hero Section (Top 40%):
Background: Deep Navy (bg-slate-900).
Content: Large centered H1 "Unlock Your Marketing Potential!".
Search Component: A large, white, pill-shaped input (rounded-full, h-14, w-2/3 max-w-2xl). Inside right: A circular arrow button (bg-slate-900 text-white).
CTA Button: "Start a New Staging Adventure". Green gradient (bg-gradient-to-r from-emerald-500 to-teal-500), rounded-full, distinct shadow.
Quick Filters: Row of dark pill buttons ("Daily Challenge", "New Mission") using bg-white/10 and backdrop-blur.
Content Section (Bottom 60%):
Filter Bar: Horizontal scrolling list. Pill tabs. Active tab is White shadow-md text-black. Inactive is bg-transparent text-gray-500. Use icons (e.g., FileText, Share2, Megaphone) for each category.
Mission Grid: 4-column grid.
Cards: Gray background (bg-gray-100), rounded-xl.
Top Left Badge: Essential. Small pill (e.g., "Flyer Mission") with specific colors (Blue/Pink/Green).
Image: Covers 75% of card height.
Text: Simple title at bottom left.
Animation Physics:
Tab Interaction: Use a "Shared Layout Animation" (Magic Motion). When a user clicks a filter tab, the white active background slides smoothly to the new tab.
Hero Entrance: The Search Bar should expand outwards from the center (scaleX: 0 -> 1) on load.
Card Hover: On hover, apply y: -10px and a colored shadow glow (shadow-emerald-500/20). The card should feel "springy" (stiffness 300, damping 20).
Typography: Inter or Quicksand (for a friendlier vibe).
