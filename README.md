# SaversGarden

**A weekly budget garden.** Set a weekly spending limit, log what you spend, and watch your garden grow: every week you finish at or under budget earns a tree, and every week you overspend removes one.

Built for the module **LUBS3151 Contemporary Issues in Banking**.

> SaversGarden is a budgeting aid, not financial advice. Figures are based only on the spending you enter.

---

## The problem it tackles

People who set a weekly spending limit often go over it, because a budget feels abstract and overspending has no immediate consequence. SaversGarden makes each week's result visible straight away, as a plant gained or lost in a virtual garden.

**Who it's for:** students and young adults who set a weekly budget but struggle to stick to it.

---

## How to open it

- **Online (any phone or laptop):** `https://<your-username>.github.io/savertree/`
- **On your own computer:** download `index.html` and double-click it. It opens in your web browser with nothing to install and no internet needed.

---

## How to use it

1. **Set your budget.** Type your weekly budget (e.g. `50`) and press **Start week**. The budget then locks until the week ends.
2. **Log your spending.** Press **+ Add expense** and follow the three steps:
   1. What did you spend it on? (up to 30 characters)
   2. How much did it cost? (e.g. `3.45`)
   3. Are you sure this is correct? Press **Yes** to add it or **Cancel expense** to add nothing.

   "Spent this week" lists every expense, with the total **Spent** and the amount **Remaining**.
3. **End the week.** Press **End week**, check the summary, and press **Yes, end week**. The week is added to your history and your garden updates.
4. **See your garden and history.** Tap the **Garden & History** box to see every plant you've earned and a table of every completed week. Press **‹ Back** to return.

---

## The rules

| Rule | What it means |
|---|---|
| **Plant rule** | Spending **at or under** budget earns a plant. Going over removes your most recent plant. The garden never drops below zero. A week with £0 spent earns a plant. |
| **Overall total** | Sum of budgets − sum of spending, across **completed weeks only**. Shown as "Under budget by £X", "Overspent by £X" or "On budget". The app never says "saved", because spending less than a budget isn't the same as saving money. |
| **No editing** | Expenses can't be edited or deleted once confirmed. The "Are you sure?" step is the safeguard. |
| **Valid amounts** | Must be a number above £0 with no more than 2 decimal places. Blank, 0, negative numbers and text are rejected with a clear message. There is no maximum. |
| **Descriptions** | Required, up to 30 characters. |

---

## How it works (behind the scenes)

- **One file.** The whole app is `index.html`: HTML for the layout, CSS for the look, and JavaScript for the logic.
- **Money in whole pence.** £3.40 is stored as `340`. Pounds are only used for display, always with 2 decimal places. This avoids the computer rounding error where 0.1 + 0.2 = 0.30000000000000004.
- **The garden is rebuilt every time** from the list of completed weeks using the plant rule, so the plant count can never drift out of step with the history.
- **Automatic saving.** The app saves after every action (Start week, each expense, End week) in the browser's own storage (`localStorage`) and loads it when the page opens, so closing it mid-week loses nothing. If there's no saved data, or the data can't be read, it starts with an empty garden and a message instead of crashing.
- **Each device keeps its own garden.** Data stays in the browser where it was entered and is never sent anywhere.

---

## Privacy

SaversGarden has **no logins or accounts**. It does not collect names, bank details or location, and it does not send data anywhere. Everything you enter stays in your own browser on your own device.

---

## Testing

Every test figure from the project plan was checked in the browser.

| Test | Expected result | Result |
|---|---|---|
| £50 budget, spend £12.50 + £20 | Remaining £17.50 | ✅ |
| …then add a missed £5 | Remaining £12.50 | ✅ |
| Spend £50 of £50 | Earns a plant | ✅ |
| Then spend £50.01 of £50 | Loses a plant | ✅ |
| Overspend with an empty garden | Garden stays at 0 | ✅ |
| A week with £0 spent | Earns a plant | ✅ |
| Weeks £50/£32.50, £50/£61, £40/£40 | Under budget by £6.50, 1 plant | ✅ |
| One week £50/£70 | Overspent by £20.00 | ✅ |
| £0.10 + £0.20 against a £0.30 budget | Earns a plant (pence rule) | ✅ |
| Blank, 0, −5, "abc", 3.456 (budget and expense) | Each rejected with a message | ✅ |
| 31-character description | Rejected with a message | ✅ |
| Close and reopen, including mid-week | Same garden, totals, locked budget and expenses | ✅ |
| No saved data | Empty garden and a message, no crash | ✅ |
| More than 7 weeks / more than 5 plants | "Scroll for earlier weeks"; home shows the 5 most recent | ✅ |
| Opened on a laptop and a phone via GitHub Pages | Works on both | ✅ |

---

## Future development (not built)

Ideas deliberately left out of this version:

- Syncing one garden across several devices (would need user accounts and an online database)
- An automatic end of week based on the calendar
- Wilting plants, different tree types or growth stages
- Suggested budgets based on past weeks
- Open Banking connections to import spending automatically
- "Nothing logged" reminders
- A yearly projection
- Importing spending from a CSV file

---

## About the name

The app was first called **Savertree**. During development we found that a financial planning website already uses that name, so the app was renamed **Saver Garden** to avoid confusion with an existing financial business. On the module professor's advice, it was then renamed **SaversGarden** to further reduce the risk of copyright or trademark issues.

SaversGarden is a student project and is not connected to any company or website called Savertree. (Behind the scenes, the app's save key is still called `savertree-data`, so anyone who used the earlier version keeps their garden.)

---

## How it was built

The app was built in stages, with a git commit after each working step:

1. Home screen, Start week, Add expense and End week pop-ups, plant rule and overall total
2. Layout fixes: the "Spent this week" box stays one size and scrolls; the empty-garden message reads across the box
3. Garden & History screen and automatic saving
4. Published on GitHub Pages so it can be used on any phone or laptop (no logins; each device keeps its own garden)
5. Input checks
6. This README
7. Renamed from Savertree to Saver Garden (name already used by a financial planning website)
8. Renamed from Saver Garden to SaversGarden (on the professor's advice)
