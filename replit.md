# Quran Reading Application

## Overview

This is a comprehensive web-based Islamic application providing the complete Holy Quran with Arabic text, English translations, and audio recitation. It also includes daily Islamic supplications (duas), and a prayer times calendar with Hijri dates. Key features include real-time search, bookmarking, and dark/light theme modes. The application aims to offer an authentic Islamic aesthetic and a modern, user-friendly experience.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture

The frontend is built with React.js and TypeScript, utilizing Vite for development and bundling. It employs a tabbed interface for navigation, featuring Quran reading, Daily Duas, and Prayer Times Calendar sections. Wouter handles client-side routing, and TanStack Query manages data fetching and caching.

**UI/UX Design:**
- **Design System:** Islamic aesthetic with teal-green, gold, and soft beige colors. Uses Radix UI primitives and shadcn/ui for components, styled with Tailwind CSS.
- **Typography:** Amiri and Scheherazade New for Arabic, DM Sans for UI, and Source Serif Pro for translations.
- **Responsiveness:** Mobile-first design approach.
- **Theme:** Dark/light mode toggle with persistence via local storage.

**State Management:**
- React Context API for theme management.
- Local Storage for user preferences and bookmarks.
- Custom hooks for specific functionalities like audio playback.

**Features:**
- **Quran Reading:** Accordion-style surah display with inline ayahs, Bismillah (where appropriate), multi-reciter audio playback system, search, and bookmarking.
- **Multi-Reciter Audio:** 4 world-renowned reciters (Alafasy, Husary, Minshawi, Abdul Basit) with dropdown selector, progress bar, time display, and localStorage persistence.
- **Daily Duas:** Collection of essential duas with Arabic text, English translation, and contextual usage, presented in a responsive card grid with bookmarking.
- **Prayer Times Calendar:** Displays current Hijri and Gregorian dates, along with daily prayer times (Fajr, Dhuhr, Asr, Maghrib, Isha).
- **Hadith Module:** Integrates Sahih al-Bukhari with full Arabic, Urdu, and English text, featuring a redesigned UI, smart caching, and a daily Hadith widget on the Quran homepage.

### Backend Architecture

The backend uses Express.js with TypeScript, primarily serving as a proxy for external APIs, notably for audio streaming and prayer times. It has a minimal API surface, as much of the data is client-side. An abstract storage interface is defined, currently using in-memory storage, but designed for future database integration.

### Data Architecture

- **Data Storage:** Quran text data is stored locally in JSON format (`client/src/data/quran.json`) and bundled with the application for an offline-first approach.
- **Schema:** Zod schemas are used for runtime type validation and TypeScript inference, with shared types between frontend and backend.
- **Audio:** Audio files are referenced via CDN links and proxied through the backend.

## External Dependencies

- **Audio Streaming:** Islamic Network CDN (direct CORS-free access) for multi-reciter Quran recitations (Alafasy, Husary, Minshawi, Abdul Basit).
- **Prayer Times API:** Aladhan API (via backend endpoint) for real-time prayer times and Hijri dates.
- **Hadith Data:** jsdelivr CDN API for Sahih al-Bukhari (Arabic, English, Urdu editions).
- **Database:** Drizzle ORM for PostgreSQL (via Neon serverless driver) for potential future features.
- **Font Services:** Google Fonts for various Arabic and English typographies (Amiri, Scheherazade New, DM Sans, Source Serif Pro, Noto Nastaliq Urdu).
- **Key NPM Packages:**
    - `@radix-ui/*`: Accessible UI component primitives.
    - `@tanstack/react-query`: Server state management.
    - `drizzle-orm`: Type-safe database ORM.
    - `react-hook-form`: Form validation.
    - `date-fns`: Date manipulation.
    - `embla-carousel-react`: Carousel functionality.
    - `cmdk`: Command palette component.

## Recent Changes

**October 20, 2025 - Multi-Reciter Audio System Added**

**Audio Playback System:**
- **4 World-Renowned Reciters**:
  - Mishary Rashid Alafasy (مشاري بن راشد العفاسي) - Default
  - Mahmoud Khalil Al-Husary (محمود خليل الحصري)
  - Mohamed Siddiq Al-Minshawi (محمد صديق المنشاوي)
  - Abdul Basit Abdul Samad (عبد الباسط عبد الصمد)
- **Reciter Selector**: Dropdown menu in Quran page header with Volume2 icon
- **Display**: Shows English and Arabic names for each reciter
- **Instant Switching**: Change reciter anytime with toast notification
- **Auto-Replay**: Automatically replays current surah when reciter is changed

**Audio Player Features:**
- **Play/Pause Toggle**: Click to play or pause any surah
- **Progress Bar**: Visual timeline with clickable seeking
- **Time Display**: Current time / Total duration (MM:SS format)
- **Stop Button**: Completely stop playback and hide player
- **Auto-Stop**: Previous surah stops when new one starts
- **Loading State**: Spinner animation while audio loads
- **Error Handling**: Toast notification if audio unavailable
- **Single Player**: Only one surah plays at a time

**UI Design:**
- **Gradient Player Card**: Primary/accent gradient background with border
- **Reciter Badge**: Shows current reciter at top of Quran section
- **Islamic Theme**: Beige (#fdf9f2), gold (#c9a227), teal (#066c5f) colors
- **Smooth Animations**: Hover effects on play buttons and controls
- **Responsive**: Works on mobile and desktop

**Technical Implementation:**
- **Direct CDN Access**: No backend proxy needed (CORS-free)
- **Lazy Loading**: Audio loads only when play is pressed
- **No Preloading**: Credit-efficient, minimal bandwidth usage
- **localStorage Persistence**: Remembers user's reciter choice
- **HTML5 Audio**: Native browser audio element, no external libraries
- **Audio URLs**: `https://cdn.islamic.network/quran/audio-surah/128/ar.{reciterId}/{surahNumber}.mp3`

**Performance:**
- ✅ **Zero backend processing** for audio (direct CDN streaming)
- ✅ **Lazy-load** only on user interaction (play button)
- ✅ **localStorage caching** for reciter preference
- ✅ **Efficient state management** with React hooks
- ✅ **Minimal re-renders** using React memo and callbacks

**October 20, 2025 - Home Page Redesign: Featured Qur'anic Ayah & Ramadan Countdown (Earlier)**

**Home Page Transformation:**
- **Replaced Daily Hadith** with a spiritually peaceful **Featured Qur'anic Verse**
- **Verse**: Surah At-Tawbah (9:40) - "لَا تَحْزَنْ إِنَّ اللَّهَ مَعَنَا" (Do not grieve; indeed, Allah is with us)
- **Display Hierarchy**:
  - Arabic at TOP (text-4xl to text-6xl, gold accent, Amiri font)
  - Urdu translation CENTER (text-2xl to text-3xl, bold, teal/primary, Noto Nastaliq Urdu)
  - English translation BOTTOM (text-lg to text-xl, italic, muted gray)
- **Card Design**: Beige background (#fdf9f2), rounded-3xl, gold dividers, decorative sparkle icon
- **Smooth Animations**: Fade-in (0.8s), slide-up (1s), all GPU-optimized

**Ramadan Countdown Timer:**
- **Live countdown** to Eid-ul-Fitr (Ramadan 2026: March 20, 2026)
- **Four-unit display**: Days | Hours | Minutes | Seconds
- **Real-time updates** every second via efficient setInterval
- **Visual Design**:
  - Gradient background (from-primary/5 to-accent/5)
  - Individual cards for each time unit with rounded corners and shadows
  - Moon icons with glowing animation
  - Accent/primary colors for numbers
  - Footer: "رَمَضَانُ مُبَارَكٌ" (Ramadan Mubarak)
- **Animations**: Glow effect on moon icons, subtle pulse on countdown numbers
- **Optimized**: Lightweight CSS animations, no heavy libraries, minimal CPU usage

**Performance Optimizations:**
- ✅ **No API calls** required (Featured Ayah is hardcoded)
- ✅ **Instant load** - no loading states needed
- ✅ **GPU-accelerated** animations (transform/opacity only)
- ✅ **Single setInterval** for countdown updates
- ✅ **Credit-efficient** - zero external API costs for home page

**Hadith Module (Separate Tab):**
- **Complete Sahih al-Bukhari** with Arabic, Urdu, and English translations
- **Beautiful gradient header** (rose-pink to teal)
- **Arabic text prominence**: Large gold font at top of each hadith
- **Smart caching**: 7-day localStorage expiry per language
- **Lazy loading**: Books fetch on-demand when accordion expands
- **Footer**: Book name + hadith number on each card

**Design Philosophy:**
- Culturally Islamic aesthetic with teal, gold, and beige palette
- Authentic typography: Amiri (Arabic), Noto Nastaliq Urdu (Urdu), Inter (English)
- Minimalist, peaceful, spiritually uplifting home page experience
- Responsive design for mobile and desktop