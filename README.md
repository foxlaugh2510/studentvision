# StudentVision — free college welfare tracker

A responsive, dark-mode public website that displays welfare issues from a published Google Sheet. Includes issue search, category/status filters, status totals, progress notes, last-updated dates, and a direct WhatsApp button.

## Files
- `index.html` — complete frontend; no build tools required.
- `sample-data.csv` — fictional examples to help set up the spreadsheet.
- `README.md` — setup and hosting guide.

## Important before sharing publicly
The included issues are **fictional demo data**. Replace them with verified, approved updates before sharing the website with students. Do not publish student names, phone numbers, private complaint details, or unverified allegations.

## 1. Create the Google Sheet
1. Create a Google Sheet named `StudentVision Tracker`.
2. Rename the first tab to `Issues` (optional; just publish the correct tab).
3. Put these exact column headers in row 1:

   `id | title | category | status | updated | summary | progress`

4. Add one issue per row. Allowed status labels used by the site: `Raised`, `Under review`, `In progress`, `Resolved`, `On hold`.
5. Use dates like `2026-10-18` for `updated`. Keep summaries and progress notes factual and concise.
6. Start from `sample-data.csv` if useful, but keep the DEMO labels until you've replaced the fictional content.

## 2. Publish only the tracker tab as CSV
1. In Google Sheets, choose **File → Share → Publish to web** (the wording may vary).
2. Choose only the public `Issues` sheet/tab, not the entire workbook if it contains private notes.
3. Choose **Comma-separated values (.csv)** as the format and publish.
4. Copy the published CSV URL. This makes the selected sheet's contents publicly readable; never put confidential information in that tab.

## 3. Connect the website to the sheet
1. Open `index.html` in a text editor.
2. Find this line near the bottom:

   `const SHEET_CSV_URL = "PASTE_PUBLISHED_GOOGLE_SHEET_CSV_URL_HERE";`

3. Replace the placeholder text with the published CSV URL, keeping the quotation marks.
4. Save the file. The page will now try to load the sheet. If it cannot load the sheet, it deliberately falls back to fictional demo data and shows a warning.
5. Test by opening `index.html` in your browser. For the most reliable testing, use the hosted site after deployment.

## 4. Free hosting with GitHub Pages
1. Sign in to GitHub or create a free account.
2. Create a **public** repository called `studentvision` (or another name).
3. Upload `index.html` to the repository's root. You may also upload this README and the CSV sample, but don't upload private information.
4. Open the repository's **Settings → Pages**.
5. Under build/deployment, select **Deploy from a branch**, choose `main` and `/(root)`, then save.
6. Wait for GitHub Pages to publish. The site URL will look like `https://YOUR-USERNAME.github.io/studentvision/`.
7. Open that URL on your phone and test search, filters, and the WhatsApp button.

GitHub Pages hosting is free for public repositories. Publishing the website does not make your Google Sheet private: the published CSV is public too.

## 5. WhatsApp contact link
The button is currently configured as `https://wa.me/917397380056`, treating the supplied 10-digit number as an Indian mobile number and adding country code `91`. Verify the number is correct before publishing. WhatsApp links require the country code and digits only, with no `+`, spaces, or punctuation.

To change it, search `wa.me/917397380056` in `index.html` and replace the digits.

## Editing and access control
- **Public updates:** edit the Google Sheet; the public page fetches the published CSV when loaded. Google publishing/cache can introduce a delay.
- **Private admin:** this version has no admin login or write access. Only people with edit permission on the Google Sheet can change it. Do not give edit access to the public. A true website admin panel would need a backend/authentication service; a static GitHub Pages site alone cannot safely keep admin credentials secret.
- Keep the public tracker sheet separate from any private internal notes or contact details.
- If a status has not been confirmed, label it accurately (e.g. `Under review`) rather than implying that the college has accepted or resolved it.

## CSV columns
| Column | Purpose |
|---|---|
| `id` | A stable short identifier such as `SV-001` |
| `title` | Short issue title |
| `category` | Facilities, Hostel, Academic facilities, Transport, etc. |
| `status` | Raised, Under review, In progress, Resolved, On hold |
| `updated` | Last-updated date, preferably `YYYY-MM-DD` |
| `summary` | Brief public description of the concern |
| `progress` | Latest factual action, response, or next step |

## Troubleshooting
- **Demo data still appears:** check that you replaced the placeholder with the *published CSV* URL, not the normal Google Sheets editing URL.
- **No issues appear:** verify that row 1 contains the column headers and that each issue has a title.
- **Updates seem delayed:** refresh after a short wait; publishing and caching are not guaranteed to be instantaneous.
- **Google Sheet won't load:** ensure the correct tab is published as CSV and that its URL starts with `https://docs.google.com/`.
