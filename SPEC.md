# Co-Parenting Hub MVP Specification

## Project Overview
- **Name:** Co-Parenting Hub
- **Type:** Single-file HTML web application
- **Core Functionality:** A shared digital coordination tool for co-parents to manage custody schedules, track expenses, communicate, and maintain child profiles—all with local storage persistence
- **Target Users:** Divorced or separated parents sharing custody

---

## UI/UX Specification

### Layout Structure
- **Header:** Logo/title, navigation tabs
- **Main Content Area:** Tab-based single-page app
- **Footer:** Minimal, copyright only

### Responsive Breakpoints
- Mobile: < 640px (stacked layout, touch-friendly)
- Tablet: 640px - 1024px
- Desktop: > 1024px

### Visual Design

#### Color Palette
- **Primary:** `#2D5A5A` (Deep teal - trust, stability)
- **Secondary:** `#F7F3E8` (Warm cream - warmth, family)
- **Accent:** `#E8A87C` (Soft coral - warmth, energy)
- **Success:** `#7FB069` (Sage green - growth, harmony)
- **Warning:** `#D4A574` (Warm tan)
- **Danger:** `#C97C7C` (Muted rose)
- **Text Primary:** `#2C3E3E` (Dark teal-gray)
- **Text Secondary:** `#6B7C7C` (Muted gray-teal)
- **Background:** `#FDFBF7` (Off-white warm)
- **Card Background:** `#FFFFFF`
- **Border:** `#E5DFD3` (Warm gray)

#### Typography
- **Font Family:** 'DM Sans' for body, 'Fraunces' for headings (warm, distinctive)
- **Headings:** Fraunces, 600 weight
  - H1: 28px
  - H2: 22px
  - H3: 18px
- **Body:** DM Sans, 400 weight, 15px
- **Small/Caption:** 13px

#### Spacing System
- Base unit: 4px
- XS: 4px, S: 8px, M: 16px, L: 24px, XL: 32px, XXL: 48px

#### Visual Effects
- Card shadows: `0 2px 8px rgba(45, 90, 90, 0.08)`
- Hover lift: `translateY(-2px)` with shadow increase
- Border radius: 12px (cards), 8px (buttons), 6px (inputs)
- Transitions: 200ms ease-out

### Components

#### Navigation Tabs
- 5 tabs: Calendar, Expenses, Messages, Children, Settings
- Active state: filled background, bold text
- Hover: subtle background tint

#### Calendar
- Month view with navigation arrows
- Day cells showing custody indicators (colored dots/badges)
- Click day to add/edit custody event
- Legend showing parent color coding

#### Expense Tracker
- List of expenses with amount, category, date, who paid
- Split calculator showing 50/50 split
- Add expense form
- Running total per parent

#### Message Log
- Chat-style interface
- Timestamps on every message (ISO 8601 format for court admissibility)
- Sender identification (Parent 1 / Parent 2)
- "Export for Court" button (downloads JSON)

#### Child Profiles
- Card per child with name, DOB, photo placeholder
- Add/Edit/Delete children

#### Settings
- Configure parent names
- Clear all data option
- Export/Import data

---

## Functionality Specification

### Core Features

1. **Custody Calendar**
   - Month navigation (prev/next)
   - Click date to toggle custody assignment
   - Visual distinction: Parent 1 (teal), Parent 2 (coral), Shared (gradient)
   - Persist to LocalStorage

2. **Expense Tracking**
   - Add expense: amount, description, category, date, paid by
   - Categories: Medical, Education, Extracurricular, Clothing, Food, Other
   - Auto-calculate split (50/50 default)
   - Show balance: who owes whom
   - Persist to LocalStorage

3. **Message Log**
   - Add message with sender selection
   - Timestamps in format: `YYYY-MM-DD HH:MM:SS`
   - Cannot be edited/deleted (court admissibility)
   - Export all messages as JSON file
   - Persist to LocalStorage

4. **Child Profiles**
   - Add child: name, date of birth
   - View list of children
   - Edit/Delete capability
   - Persist to LocalStorage

5. **Settings**
   - Set Parent 1 and Parent 2 names
   - Clear all data (with confirmation)
   - Export data as JSON
   - Import data from JSON

### Data Handling
- All data stored in LocalStorage under keys:
  - `cophub_calendar`
  - `cophub_expenses`
  - `cophub_messages`
  - `cophub_children`
  - `cophub_settings`
- Auto-save on every change

### Edge Cases
- Empty states for each section
- Validate expense amounts (positive numbers)
- Validate child DOB (not future)
- Handle LocalStorage quota exceeded
- Graceful degradation if LocalStorage unavailable

---

## Acceptance Criteria

1. ✅ Single HTML file loads without errors
2. ✅ All 5 navigation tabs function and display correct content
3. ✅ Calendar displays current month, navigates correctly
4. ✅ Can add custody events to dates, persists after reload
5. ✅ Can add expenses, calculates split correctly
6. ✅ Message log shows timestamps in court-admissible format
7. ✅ Can export messages for court
8. ✅ Child profiles can be added/edited/deleted
9. ✅ Settings allow naming parents
10. ✅ All data persists after page reload
11. ✅ Responsive on mobile devices
12. ✅ Professional but warm aesthetic achieved
