# Traveloop

Traveloop is a travel planning app for building and managing multi-city trips. The frontend is a React + Vite application, and the backend is a small Python/SQLite data layer that stores trips, stops, activities, budgets, packing items, and trip notes.

## What It Does

The app currently includes:

- A dashboard with upcoming trips, travel stats, and a create-trip flow.
- A trips view for browsing and searching all saved journeys.
- A trip details view with itinerary, budget breakdown, packing list, and notes.
- SQLite-backed demo data that is initialized automatically on first run.
- Cached data fetching through a lightweight RPC helper in the frontend.

## Tech Stack

- Frontend: React, TypeScript, Vite, Tailwind CSS
- UI helpers: custom component set in `src/components/ui`
- State/data access: browser RPC wrapper with sessionStorage caching
- Backend: Python, SQLite

## Project Structure

The actual application code lives under `traveloop_src/`:

- `apps/traveloop/frontend` - React app and UI components
- `apps/traveloop/backend` - Python data layer and SQLite schema
- `scripts/seed_sample_data.py` - optional extra demo data seeding

## Core Data Model

The backend schema includes:

- `users`
- `trips`
- `stops`
- `activities`
- `budget_items`
- `packing_items`
- `trip_notes`

On first import, the backend initializes the database and seeds a demo user plus a sample trip.

## Setup

### Frontend

From `traveloop_src/apps/traveloop/frontend`:

```bash
npm install
npm run dev
```

Build or preview the app with:

```bash
npm run build
npm run preview
```

### Backend Data

The backend uses SQLite and initializes its database automatically when `apps.traveloop.backend.main` is imported.

If you want to add more sample data, run this from `traveloop_src`:

```bash
python scripts/seed_sample_data.py
```

## Available Behaviors

- `get_dashboard_data`
- `create_trip`
- `get_trips`
- `get_trip_details`
- `add_stop`
- `add_activity`
- `update_budget_item`
- `toggle_packing_item`
- `add_note`
- `search_cities`

## Notes

- The frontend expects a runtime app config object to provide the data endpoint and app name.
- `requirements.txt` in the backend folder is currently empty.
- The current UI is focused on dashboard, trip management, trip details, packing, and notes. Some features in the design brief, such as auth, public sharing, and admin analytics, are not implemented yet.