# Woolworths Price Trends

A pure frontend app for exploring 18 months of Woolworths grocery price history. No server required — works entirely in the browser and deploys directly to GitHub Pages.

## Project Structure

```
├── index.html        # The entire app — HTML, CSS, JS in one file
├── prices.xlsx       # Your price data (Excel file, loaded client-side)
└── README.md
```

## Replacing the dummy data

The included `prices.xlsx` is placeholder data. To use your real data:

1. Make sure your Excel sheet has these **exact column headers** in row 1:
   - `Product`
   - `Old Price`
   - `New Price`
   - `Date` (any parseable date format works, e.g. `2024-10-01`)
2. Replace `prices.xlsx` in the repo root with your file, keeping the same filename.
3. Commit and push — GitHub Pages will serve the new file automatically.

## Deploy to GitHub Pages

1. **Create a new repo** on GitHub (can be public or private with Pages enabled).

2. **Push the files:**
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO.git
   git push -u origin main
   ```

3. **Enable GitHub Pages:**
   - Go to your repo → **Settings** → **Pages**
   - Under *Source*, select **Deploy from a branch**
   - Choose `main` branch, `/ (root)` folder
   - Click **Save**

4. Your site will be live at:
   `https://YOUR_USERNAME.github.io/YOUR_REPO/`

## How it works

- `prices.xlsx` is fetched as a static asset using a relative URL (`./prices.xlsx`)
- [SheetJS](https://sheetjs.com/) parses the Excel file entirely in the browser
- [Chart.js](https://www.chartjs.org/) renders the price trend charts
- No build step, no npm, no backend — just two files

## Column name customisation

If your column headers differ, update the `COL` config near the top of `index.html`:

```js
const COL = {
  product:  'Product',    // ← change to match your header
  oldPrice: 'Old Price',
  newPrice: 'New Price',
  date:     'Date',
};
```
