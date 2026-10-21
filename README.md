# Meeting Action Tracker

A single-page app for teams that keep forgetting agreed actions. No build step, no dependencies.

- Add an action with an owner and a due date
- Actions are grouped by owner, each with a tick box for done
- Open, done and overdue counts at the top; overdue actions are highlighted in red
- Data is saved in the browser's local storage (per browser and device, not shared between teammates)

## Deploy to Vercel

1. Go to [vercel.com/new](https://vercel.com/new) and import this repository.
2. Leave **Framework Preset** as `Other`. Leave the build command and output directory empty.
3. Click **Deploy**. Vercel serves `index.html` from the repository root.

## Run locally

Open `index.html` in a browser, or serve the folder:

```
npx serve .
```
