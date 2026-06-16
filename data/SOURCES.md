# Sources and method

## Where the numbers come from

Indian box office data is famously messy. Budgets and grosses are rarely audited, trade outlets disagree with each other, and "official" figures are sometimes closer to marketing than accounting. Everything here should be read as a careful estimate, not a final ledger.

**Annual box office (Chart 1)**
Gross collection figures come from the Ormax Box Office year end reports, which are the most credible public source for the Indian market. The all India totals for every year are taken directly from those reports. The Hindi cinema values for 2023, 2024 and 2025 are stated by Ormax. 

For 2019 and 2022, Ormax published precise language market share percentages (44% and 33% respectively) rather than absolute figures. The absolute Hindi box office values (₹4,800cr and ₹3,510cr) were derived by applying these percentages to the total All-India box office of those respective years (`All-India Total * Language Share / 100`).

The 2020 and 2021 Hindi values are estimates that sit inside the sourced All-India totals for those two pandemic years, where theatre closures and partial runs make a clean, audited language split hard to compile from trade records.


**Per film budgets and grosses (Charts 2 and 3)**
These are pulled from the most widely cited public figures for each title, cross checked across Wikipedia, Box Office India, Koimoi and Sacnilk where possible. Worldwide gross is used throughout, not net India collections.

## How the metrics are defined

- **Percent of budget recovered** = worldwide gross divided by production budget, times 100.
- **Estimated loss** = production budget minus worldwide gross.

## The honest caveats

1. **Gross is not profit.** Theatres, taxes and distributors take roughly half of a ticket before any money reaches the producer. A film can show more than 100 percent "recovered" on this simple gross over budget measure and still have lost money in reality. Thugs of Hindostan is the classic example and is left out of the losers chart for exactly this reason.
2. **Budgets exclude marketing.** Promotion and prints can cost as much again as the film itself. Real break even points are higher than the budgets shown, and real losses are deeper.
3. **China inflates a few outliers.** Dangal, Secret Superstar and Andhadhun earned enormous sums in China, which is why their recovery rates tower over everything else.
4. **Pan India titles.** Adipurush is marked separately because it was a multi language release led by a Telugu star, not a pure Hindi production.

## CSV Data Schema

To make onboarding and reuse simple, here is a description of the columns in each CSV file inside the `data/` folder:

### 1. `box_office_by_year.csv`
- `year`: The calendar year of release (e.g., `2019` to `2025`).
- `hindi_cinema_cr`: Total box office gross for original and dubbed Hindi releases in India (₹ crore).
- `all_india_cr`: Total domestic box office gross across all languages in India (₹ crore).
- `hindi_share_pct`: The percentage share of Hindi cinema gross out of the All-India gross total.
- `biggest_hindi_film`: The highest-grossing Hindi film worldwide of that year.
- `film_worldwide_gross_cr`: Worldwide gross of the biggest Hindi film of that year (₹ crore).
- `note`: Contextual notes on language share estimations.

### 2. `budget_recovered.csv`
- `film`: The title of the movie.
- `year`: The release year.
- `budget_cr`: Production budget in ₹ crore.
- `worldwide_gross_cr`: Worldwide gross box office in ₹ crore.
- `genre`: Primary genre (e.g., `Action`, `Comedy`, `Romance`, `Drama`, `Thriller`, `Horror-Comedy`).
- `pct_recovered`: Recovery percentage (calculated as `worldwide_gross_cr / budget_cr * 100`).

### 3. `biggest_losers.csv`
- `film`: The title of the movie.
- `year`: The release year.
- `budget_cr`: Production budget in ₹ crore.
- `worldwide_gross_cr`: Worldwide gross box office in ₹ crore.
- `est_loss_cr`: Production budget minus worldwide gross (₹ crore).
- `pct_recovered`: Percentage of budget recovered.
- `pan_india`: Whether the film was a multi-lingual pan-India release (`yes`/`no`).

---

If you spot a figure you can source more precisely, corrections are welcome.
