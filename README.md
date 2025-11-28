# Calendar Import

A PWA + Google Apps Script solution to import calendar events to Google Sheets.

## Features

- Imports events from the **previous month**
- Includes date, start time, end time, and duration
- Supports multiple calendars
- Detects video meeting links (Google Meet, Zoom, Calendly)
- Installable PWA with offline support

## Setup

### 1. Google Apps Script

1. Open your Google Sheet
2. Go to **Extensions → Apps Script**
3. Delete any default code
4. Create two files: `props.gs` and `code.gs`
5. Copy the contents from `gas/props.gs` and `gas/code.gs`
6. Edit `props.gs` to add your calendar IDs:

```javascript
const CALENDARS = [
  { id: 'primary', name: 'My Calendar' },
  { id: 'work@company.com', name: 'Work' },
];
```

7. Deploy as a web app:
   - Click **Deploy → New deployment**
   - Select type: **Web app**
   - Execute as: **Me**
   - Who has access: **Anyone** (or your org)
   - Click **Deploy** and copy the URL

### 2. GitHub Pages (PWA)

1. Create a new repository on GitHub
2. Upload the entire contents of the `pwa/` folder to the repo root
3. Go to **Settings → Pages**
4. Select branch: `main`, folder: `/ (root)`
5. Save and wait for deployment

### 3. Using the App

1. Open your GitHub Pages URL
2. Paste your Apps Script deployment URL
3. Select the calendars you want to import
4. Tap **Import**

Settings are saved locally—configure once and you're set.

## Sheet Output

| Column | Description |
|--------|-------------|
| Meeting ID | Unique event identifier |
| Name | Event title |
| Date | Event date (YYYY-MM-DD) |
| Start Time | Start time (HH:mm) |
| End Time | End time (HH:mm) |
| Duration (min) | Duration in minutes |
| Attendees | Comma-separated emails |
| Video Link | Detected meeting URL |
| Calendar | Source calendar name |

## Install as App

On mobile, use your browser's "Add to Home Screen" option to install as a standalone app.

## File Structure

```
├── gas/
│   ├── props.gs      # Calendar configuration
│   └── code.gs       # Main script logic
├── pwa/
│   ├── index.html    # App UI
│   ├── manifest.json # PWA manifest
│   ├── sw.js         # Service worker
│   ├── favicon.ico   # Browser favicon
│   └── icons/        # App icons (all sizes)
└── README.md
```
