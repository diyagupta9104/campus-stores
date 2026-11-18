# Campus Stores

Campus Stores is a Product Engineer work sample set at a fictional campus media equipment desk. Work through a club’s screening, from equipment pickup to a partial return and the next morning’s handover. Open **Candidate brief** in the app for the assignment.

## My decision

I would keep the one-slip-per-unit model and change the handover. During pickup, request `RQ-214` tells me what the Film Society is allowed to take. Inventory shows that projector `PR-04`, speaker `SP-02`, and adapter `AD-12` are available; `PR-06` is in repair. I can issue the three available units to Kabir Sen and, when he brings back only the projector and speaker, close those two slips without losing track of the adapter. That part works well.

The awkward part comes at the next shift. Originally, **Record return** closed a slip immediately, and the explanation that Leela would bring the adapter at 9 am lived in a separate free-text note. There are two adapters, `AD-12` and `AD-15`, in the same bin. I wanted the morning clerk to see which one was still out and check its label before closing anything.

I put the handover on the slip because the slip already connects the request to a physical unit. Making the Desk book note more prominent would still leave the next clerk matching a message to a slip; a status on the whole request would not distinguish the units in a partial return. Free-text notes remain useful for context, but the expected returner and time need to travel with the outstanding unit.

### What I changed

The [prototype in the loan register](app.js) lets the evening clerk add a return plan directly to the `AD-12` slip: Leela Das, Saturday 9 am. That plan also appears in the Desk book. Recording a return now shows the request and unit details, asks for the ID on the physical item, and saves who returned it and when. The independent slips, inventory view, and ordinary Desk book notes still work as before. [The CSS changes](styles.css) keep the new controls usable on narrow screens.

Try the same job in the app:

1. Restart the sample shift. Check `RQ-214`, then issue `PR-04`, `SP-02`, and `AD-12` to Kabir Sen from **Loan register**, due Friday at 8 pm.
2. Move to return time. Return `PR-04` and `SP-02` by entering their label IDs. Add a handover plan to the open `AD-12` slip for Leela Das at Saturday 9 am.
3. Move to the next morning. The outstanding slip and Desk book both point to `AD-12`. Verify the adapter label and record Leela's return. `AD-15` stays on the shelf; Debate Union's `MI-09` remains on loan.

I replayed that path in a browser: the wrong ID (`AD-15`) does not close the `AD-12` slip, the correct ID does, and the handover survives a reload. I also checked the narrow layout. Typing an ID is a deliberate extra step, not proof that the clerk actually read the label. At a real counter I would watch a morning clerk handle a partial kit without calling the previous shift. I would note whether they find the right unit, how long it takes, and whether they close any wrong slips. That would tell me if the extra check is worth keeping.

## Run the app

Open `index.html` in a modern browser. The app includes its scripts, styles, and icons and can run offline.

To serve it over local HTTP, run this from the repository folder and visit `http://localhost:8000`.

```sh
python3 -m http.server 8000 --bind 127.0.0.1
```

Each browser stores its own sample shift locally when browser storage is available. **Restart sample shift** restores the fictional starting records.

## Source

- `index.html` contains the desk layout, candidate brief, and bundled icons.
- `app.js` contains the sample records and interactions.
- `styles.css` defines the desktop and mobile layouts.

Icon license notices are in [third-party/lucide-LICENSE.txt](third-party/lucide-LICENSE.txt).


## Submit your work

1. [Fork Campus Stores](https://github.com/virinchi-healthcare/campus-stores/fork) into your GitHub account. Complete the candidate brief and push your changes to your public fork. In your README, point reviewers to your work and explain the decision you made.
2. In your fork, open **Commits**, select the final commit you want reviewed, and copy the page URL. It should look like `https://github.com/YOUR-USERNAME/campus-stores/commit/COMMIT-SHA`.
3. [Submit your work through the Google Form](https://docs.google.com/forms/d/e/1FAIpQLScvzoh1R4WS-SkiwAVBQbMvniieJYSoOEfLMyVo5CyjOvYUgQ/viewform). Your **roll number**, **email ID**, and **final commit link from your public fork** are required. Enter your roll number and email ID in the form only.
