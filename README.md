# Orbit — Personal OS

A responsive, dark-mode personal productivity web app for tasks, schedule, study sessions, workouts, habits, skills, goals, and progress. It is built with React + Vite and supports cross-device cloud sync through Supabase authentication and a per-user database.

## Features

- Email/password sign-up and sign-in
- Cloud-synced personal data (phone + laptop)
- Dashboard with daily overview, completion rate, and focus stats
- Tasks with priorities, categories, due dates, and completion toggles
- Calendar-style agenda with events and time blocks
- Study planner with subject, duration, and exam-prep categories
- Workout log and habit tracking
- Skills, hobbies, and personal goals
- Progress page with simple visual summaries
- Responsive layout with mobile navigation
- Local demo mode when Supabase is not configured (demo data stays in this browser only)

## Run locally

1. Install Node.js 20 or newer from https://nodejs.org/
2. Unzip the project and open a terminal in the project folder.
3. Install dependencies:
   ```bash
   npm install
   ```
4. Copy `.env.example` to `.env`.
5. Follow the Supabase setup below, then fill in the two values in `.env`.
6. Start the app:
   ```bash
   npm run dev
   ```
7. Open the local URL printed by Vite, usually `http://localhost:5173`.

## Enable accounts and cloud sync

1. Create a project at https://supabase.com/
2. In Supabase, open **Project Settings → API** and copy the Project URL and publishable/anon key.
3. Put them into `.env`:
   ```env
   VITE_SUPABASE_URL=https://your-project.supabase.co
   VITE_SUPABASE_ANON_KEY=your-publishable-or-anon-key
   ```
4. In Supabase, open **SQL Editor**, create a query, paste all of `supabase/schema.sql`, and run it.
5. In **Authentication → URL Configuration**, set the Site URL to your deployed app URL. For local testing, add `http://localhost:5173` to the allowed redirect URLs.
6. Restart Vite after changing `.env`.

Supabase's publishable/anon key is intended for browser use when Row Level Security is correctly enabled. **Never put a Supabase service-role key in this app or commit your `.env` file.** The included schema restricts every row to its owner.

## Put it online

You can deploy the Vite project to Vercel, Netlify, or another static host:
- Build command: `npm run build`
- Output folder: `dist`
- Add `VITE_SUPABASE_URL` and `VITE_SUPABASE_ANON_KEY` as deployment environment variables.
- Add the deployed URL to Supabase's allowed redirect URLs and set it as the Site URL.

Once deployed, sign in with the same account on your phone and laptop to see the same data. On mobile, use your browser's **Add to Home Screen** option for an app-like shortcut.

## Notes

- This is a starter project, not a hosted service: you must create your own Supabase project and deploy it to enable cloud sync.
- The app does not yet sync with Google Calendar, Apple Calendar, or device reminders; its built-in schedule syncs between devices through Supabase.
- If Supabase is not configured, the app opens in local demo mode using browser storage. Local demo data will not sync across devices.
