# Meeting Action Tracker

A single-page app for teams that keep forgetting agreed actions. No build step, no dependencies.

- Add an action with an owner and a due date
- Actions are grouped by owner, each with a tick box for done
- Open, done and overdue counts at the top; overdue actions are highlighted in red
- Sign in with a username and password; everyone who is signed in shares one list
- Data is stored in Supabase (table `public.meeting_actions`) and updates live across open copies of the app

## Data and sign-in

The page talks to Supabase directly with the project's publishable key (in `index.html`). Row-level security only lets signed-in users read, add, tick and delete actions.

Passwords live in Supabase Auth (`auth.users`). `public.profiles` holds each user's username and display name and is filled automatically when a user is added.

Users sign in with a username. The app turns it into the email `<username>@meeting-tracker.local` (set by `LOGIN_DOMAIN` in `index.html`); no mail is sent to that address. Typing a full email address also works.

### Adding a user

In the Supabase dashboard go to **Authentication → Users → Add user → Create new user**:

- Email: `<username>@meeting-tracker.local`, for example `sara@meeting-tracker.local`
- Password: their first password
- Tick **Auto Confirm User**

The profile is created with the username before the `@` and a capitalised display name (for example "Sara"). To change the display name, edit `display_name` in the `profiles` table.

## Deploy to Vercel

1. Go to [vercel.com/new](https://vercel.com/new) and import this repository.
2. Leave **Framework Preset** as `Other`. Leave the build command and output directory empty.
3. Click **Deploy**. Vercel serves `index.html` from the repository root.

## Run locally

Open `index.html` in a browser, or serve the folder:

```
npx serve .
```
