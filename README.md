# The Business of Bollywood

An interactive data story about the money behind Hindi cinema. Three charts, one scrollable page, no frameworks and no build step. Just open it in a browser.

It started as a simple question. Information Is Beautiful once mapped the most successful Hollywood movie of all time by return on investment instead of raw gross, and the answer looked nothing like the usual blockbuster list. I wanted to see what the same lens does to Bollywood. The answer turned out to be a good story, so it grew into three.

## Visual Insights

### 1. Bollywood by the years
Annual Hindi cinema box office from 2019 to 2025, with the all India total drawn behind it as a line. You can see the pandemic wipe out most of the business in 2020, a slow recovery led by South Indian films, and a genuine record set in 2025.
![Bollywood by the years](images/chart_years.png)

### 2. Percent of budget recovered
Every film plotted by what it cost against how much of that cost it earned back, on log scales, coloured by genre and sized by gross. The pattern is blunt: the smaller the budget, the bigger the percentage return.
![Percent of budget recovered](images/chart_recovered.png)

### 3. Biggest losers
The other side of the ledger. A ranked list of the Hindi films that recovered the least of their cost, with gold showing what came back and red showing what did not.
![Biggest losers](images/chart_losers.png)

---

## What is inside

**1. Bollywood by the years.** A toggle switches from rupees to Hindi's share of the whole market, which tells a quieter story about who actually drove the comeback.

**2. Percent of budget recovered.** A trend line makes it obvious, and the genre filter lets you ask which kinds of films punch above their weight.

**3. Biggest losers.** A toggle flips between percentage recovered and rupees lost.

## Live demo

If you enable GitHub Pages on this repo (Settings, then Pages, then deploy from the main branch root), the page will be live at:

```
https://YOUR-USERNAME.github.io/bollywood-data-story/
```

## Run it locally

There is nothing to install. Clone the repo and open the file.

```bash
git clone https://github.com/YOUR-USERNAME/bollywood-data-story.git
cd bollywood-data-story
open index.html        # macOS
# or just double click index.html
```

If you want a local server (handy for some browsers):

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## How it is built

Plain HTML, CSS and vanilla JavaScript. The charts are hand drawn as SVG, so there are no chart libraries, no npm install and no dependencies to break. Each of the three charts runs in its own isolated scope on the page, so their toggles and filters never interfere with each other. Fonts load from Google Fonts. Everything else is in one file.

## The data

The raw numbers live in the `data` folder as CSV so anyone can check or reuse them:

- `box_office_by_year.csv`
- `budget_recovered.csv`
- `biggest_losers.csv`

`data/SOURCES.md` explains where each figure comes from and, just as important, where the soft spots are. Indian box office data is messy. Budgets and grosses are rarely audited and trade sources often disagree, so treat everything here as a careful estimate rather than a final ledger. The short version of the caveats:

- Worldwide gross is not profit. Theatres, taxes and distributors take roughly half before the producer sees a rupee.
- Budgets exclude marketing, which can cost as much again.
- A few outliers (Dangal, Secret Superstar, Andhadhun) are lifted by huge runs in China.

## Credit

Inspired by the Information Is Beautiful piece on the most successful Hollywood movie of all time. Box office figures lean heavily on the Ormax year end reports, with per film numbers cross checked across Wikipedia, Box Office India, Koimoi and Sacnilk.

## License

MIT. Use it, fork it, improve it. If you build on the data, a link back is appreciated.

Built by Jayshil's Analytics.
