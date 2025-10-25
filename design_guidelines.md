# Design Guidelines: QuranReadify - Islamic Companion App

## Design Approach
**Selected Approach:** Design System (Material Design + Islamic Traditional Aesthetics)
**Justification:** Religious companion app requiring clarity, reverence, and serenity. Material Design's content-focused patterns enhanced with traditional Islamic visual language—geometric harmony, calligraphic elegance, and contemplative color palettes create a professional yet spiritually resonant experience.

**Key Design Principles:**
- Sukoon (Tranquility): Soft, harmonious colors and generous spacing
- Reverence: Elevated treatment of sacred text with elegant typography
- Clarity: Content-first hierarchy for easy reading and navigation
- Sophistication: Modern UX with traditional Islamic aesthetic sensibilities

## Core Design Elements

### A. Color Palette

**Light Mode (Primary):**
- Background Base: 40 25% 96% (soft warm cream)
- Background Elevated: 40 30% 98% (lighter cream for cards)
- Surface: 0 0% 100% (pure white for elevated panels)
- Primary: 165 50% 42% (teal green - mosque dome inspired)
- Primary Hover: 165 50% 35%
- Primary Light: 165 40% 90% (subtle teal backgrounds)
- Accent Gold: 42 85% 55% (warm gold for highlights)
- Accent Gold Muted: 42 60% 88% (subtle gold tints)
- Text Primary: 220 25% 15% (deep charcoal for Arabic)
- Text Secondary: 220 15% 45% (muted for English/metadata)
- Border: 40 20% 88%
- Shadow: 40 30% 75% at 8% opacity

**Dark Mode:**
- Background Base: 220 20% 14% (warm charcoal)
- Background Elevated: 220 18% 18%
- Surface: 220 15% 22%
- Primary: 165 45% 48% (brighter teal)
- Primary Hover: 165 45% 40%
- Primary Light: 165 30% 25%
- Accent Gold: 42 75% 60%
- Accent Gold Muted: 42 40% 30%
- Text Primary: 40 15% 94% (warm off-white)
- Text Secondary: 40 10% 70%
- Border: 220 15% 28%

### B. Typography

**Font Families:**
- Arabic Text: 'Amiri' (primary), 'Scheherazade New' (fallback) via Google Fonts
- English UI: 'Inter' (headings), 'DM Sans' (body)
- Translation/Body: 'Source Serif Pro' for readability

**Type Scale:**
- App Title: text-3xl md:text-4xl, font-bold
- Surah Names Arabic: text-2xl md:text-3xl, font-semibold
- Surah Names English: text-lg md:text-xl, font-medium
- Ayah Arabic: text-xl md:text-2xl, leading-loose (1.8-2.0)
- Ayah Translation: text-base md:text-lg, leading-relaxed
- Section Headers: text-xl md:text-2xl, font-semibold
- Card Titles: text-lg, font-medium
- Body Text: text-sm md:text-base
- Metadata/Labels: text-xs md:text-sm, opacity-70

### C. Layout System

**Spacing Primitives:** Tailwind units of 2, 4, 6, 8, 12, 16, 20, 24
- Micro (icons, badges): p-2, gap-2
- Standard (card padding): p-4 md:p-6, gap-4
- Component spacing: p-6 md:p-8, gap-6
- Section spacing: py-12 md:py-16, gap-8
- Major sections: py-16 md:py-20

**Grid & Containers:**
- App Container: max-w-7xl mx-auto px-4
- Content Reading: max-w-4xl mx-auto (Quran text optimal width)
- Card Grid: grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6
- Two-column layouts: grid grid-cols-1 lg:grid-cols-2 gap-8

### D. Component Library

**Top Navigation Tabs:**
- Fixed header with backdrop-blur-lg, height h-16 md:h-20
- Tabs: Horizontal flex layout with border-b-3 on active tab (primary color)
- Tab items: "Quran", "Daily Duas", "Prayer Times", "Settings"
- Logo left: Arabic calligraphy "QuranReadify" + icon
- Right utilities: Search icon, dark mode toggle, profile/settings
- Active indicator: border-b-3 border-primary with smooth slide transition
- Background: bg-background-elevated/95 with subtle shadow

**Quran Reading Section:**
- Accordion Cards: Surah list as expandable accordions
  - Header: Surah number badge (circular, bg-primary-light, gold border), Arabic + English names, revelation info, play button
  - Expanded: Ayah verses with alternating subtle backgrounds
  - Border-radius: rounded-xl, shadow-md with shadow-lg on hover
  - Border-left: 4px solid gold accent when expanded
  - Animation: Smooth height transition, rotate chevron icon

**Ayah Display:**
- Container: bg-surface, rounded-lg, p-6 md:p-8, mb-4
- Ayah number: Decorative octagonal badge (w-10 h-10, border-2 border-gold, centered text)
- Arabic text: Right-aligned, generous line-height (leading-loose)
- Translation: Left-aligned, text-secondary color, mt-4
- Separator: Thin decorative line with geometric pattern (1px, opacity-20)

**Daily Duas Cards:**
- Card grid: 2-3 columns on desktop, single on mobile
- Card design: bg-gradient-to-br from-background-elevated to-primary-light/30
  - Rounded-2xl, shadow-lg with gold accent border-t-2
  - Padding: p-6 md:p-8
  - Icon/Symbol: Top left, teal color in circular bg
  - Dua Title: Arabic + English, text-xl font-semibold
  - Time/Category: Small badge with bg-accent-gold-muted
  - Arabic text: Center-aligned, generous spacing
  - Translation: Below, text-secondary
  - Bookmark icon: Top right corner

**Prayer Times Calendar:**
- Calendar header: Month/Year with navigation arrows, bg-primary text-white rounded-t-xl
- Grid: 7-column layout for days
- Today highlight: bg-primary text-white rounded-lg
- Prayer time indicators: Small dots or badges showing prayer times
- Selected day panel: Right sidebar or modal showing:
  - Fajr, Dhuhr, Asr, Maghrib, Isha times
  - Each prayer: Icon, name, time (text-lg), countdown if active
  - Next prayer highlighted with gold accent

**Audio Player:**
- Sticky bottom bar when playing: h-20, backdrop-blur-lg
- Controls: Play/pause (primary color), skip buttons, progress bar
- Progress bar: bg-primary-light with bg-primary fill, gold thumb
- Reciter name, surah info on left
- Volume control, playback speed on right

**Buttons:**
- Primary: bg-primary hover:bg-primary-hover, text-white, rounded-full, px-6 py-3, shadow-md
- Secondary: border-2 border-primary text-primary, rounded-full, backdrop-blur (on images)
- Icon buttons: p-3 rounded-full hover:bg-primary-light transition-all
- Gold accent buttons: bg-accent-gold text-white for special actions

**Search Component:**
- Full-width input: rounded-full, bg-surface, border-2 border-border focus:border-primary
- Magnifying glass icon left, "X" clear icon right when active
- Placeholder: "Search surahs, duas, or keywords..."
- Dropdown results: Absolute positioned, bg-surface, shadow-xl, rounded-xl

**Cards (General):**
- Shadow treatment: shadow-md default, shadow-xl on hover
- Subtle gradients: from-background-elevated to-primary-light/10
- Border treatment: border border-border or gold accent borders
- Hover: translate-y-[-2px] transform transition-all duration-200

**Dark Mode Toggle:**
- Moon/Sun icon switch in header
- Smooth transitions: transition-colors duration-300 on all elements
- Persist preference in localStorage

### E. Animations

**Subtle, Purposeful Only:**
- Accordion expand/collapse: max-height transition 300ms ease-in-out
- Card hover: transform translate-y-[-2px] duration-200
- Tab indicator slide: transform translateX with duration-300
- Audio playing: Gentle pulse on play button (scale 1.05)
- Page transitions: Fade-in opacity 200ms
- NO scroll-triggered, NO parallax effects

## Special Features

**Islamic Patterns:**
- Subtle geometric patterns in page backgrounds (arabesque motifs, 2-3% opacity)
- Header/footer decorative borders using geometric Islamic patterns
- Dua card corners with small geometric flourishes

**Bismillah Treatment:**
- Appears at top of each surah reading in decorative calligraphy
- Gold color with subtle shadow, centered, text-2xl

**Readability Optimizations:**
- Arabic text: RTL direction, leading-loose (2.0 line height)
- Max content width: max-w-4xl for reading sections
- High contrast: WCAG AAA compliance
- Generous padding around sacred text

**Accessibility:**
- Clear focus states: ring-2 ring-primary ring-offset-2
- Keyboard navigation for all interactive elements
- ARIA labels on icon buttons
- Screen reader optimized semantic HTML
- Sufficient touch targets: min-h-12 on mobile

## Images

**No Large Hero Images.** This is a content-first spiritual application. Visual interest comes from:
- Typography elegance (Arabic calligraphy)
- Subtle geometric Islamic patterns as backgrounds
- Color harmony and gradient treatments
- Small decorative icons representing prayers, duas
- Optional: Minimal illustrative icons for prayer times (mosque silhouette, prayer hands)

**Pattern Usage:**
- Background textures: Very subtle (2-3% opacity) geometric Islamic patterns
- Dua card decorations: Small corner flourishes or border patterns
- Section dividers: Decorative geometric lines

Focus remains on sacred text presentation with sophisticated, serene design language that honors the content.