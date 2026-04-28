---
name: ui-designer
description: Loaded by any agent creating user-facing
  tools, interfaces, or formatted outputs. Applies user's
  visual preferences, accessibility considerations, and
  mobile-first defaults. Ensures consistency.
triggers:
  - building user-facing tool
  - creating HTML interface
  - designing report layout
  - formatting Discord output
model: claude-sonnet-4-6
---

# UI Designer

Apply consistent, accessible, user-tailored design
to anything PAP creates that the user will see or
interact with.

## Read first

Before designing anything, load:
- VOICE-AND-STYLE.md: COLOR_PRIMARY, COLOR_ACCENT_1,
  COLOR_ACCENT_2, DISPLAY_MODE, INFORMATION_STYLE
- CONFIG.md: TIME_FORMAT, DATE_FORMAT, WEEK_STARTS_ON
- VOICE-AND-STYLE.md: STANDING_PREFERENCES

User feedback during Build-Measure-Learn always
overrides these defaults for that workspace.

## Color usage

**Primary:** headers, navigation, primary actions
**Accent 1:** highlights, hover states, important values
**Accent 2:** secondary elements, supporting viz

**Fallback defaults (if no preferences set):**
- Primary: #2563eb
- Accent 1: #f59e0b
- Accent 2: #10b981

**Neutrals:**
- Light mode: bg #ffffff, text #1a1a1a, borders #e5e5e5
- Dark mode: bg #1a1a1a, text #f5f5f5, borders #333333
- System: detect from OS, default to dark if unclear

## Mobile-first defaults

Every user-facing tool starts as mobile design.

**Mobile (320px-767px):**
- Single column
- Tap targets 44x44px minimum
- Font size 16px minimum (prevents iOS zoom)
- Buttons full-width by default
- No hover-dependent interactions

**Tablet (768px-1023px):**
- Two-column where it helps

**Desktop (1024px+):**
- Multi-column when content benefits
- Hover states for additional info
- Keyboard shortcuts for power users

## Discord embed design

**Embed color:** COLOR_PRIMARY for sidebar.
Status colors: healthy #10b981, warning #f59e0b, error #ef4444

**Field layout:**
- Three fields per row maximum
- Inline fields for related short data
- Full-width for prose or longer content
- Maximum 5 buttons per row, 25 per message

**Always include:** timestamp where relevant.

## HTML tool design

**Typography:**
- System font: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif
- Headings 1.5x base minimum
- Line height 1.5 for body
- Max line length 75 characters

**Interactivity:**
- Buttons over typed commands always
- Dropdowns for 6+ options
- Date pickers for dates
- Loading states within 100ms

## Information density by INFORMATION_STYLE

**data:** Tables preferred, sortable columns, dense layout
**visual:** Charts preferred, color-coded states, iconography
**reading:** Narrative formatting, generous spacing, prose-based
**interactive:** Progressive disclosure, filters, saved views
**mix:** Tables with optional chart toggles

## Standing preferences

Apply STANDING_PREFERENCES from VOICE-AND-STYLE.md:
- "Always include an export option" → export buttons on every data view
- "Always show source data" → citations or links to originals
- "Always provide an undo option" → confirmation dialogs, undo buttons

## Accessibility floor

Non-negotiable:
- Color contrast WCAG AA (4.5:1 body, 3:1 large)
- Keyboard navigation for all interactive elements
- ARIA labels on icon-only buttons
- Focus indicators visible
- No information conveyed by color alone

If user noted accessibility needs in onboarding: those override defaults.

## What you never do

Build desktop-only unless user confirmed and approved it.
Use color alone to convey meaning.
Hide critical actions behind hover states on mobile.
Default to free text input where buttons would work.
Skip standing preferences check.
Build without testing mobile width first.
