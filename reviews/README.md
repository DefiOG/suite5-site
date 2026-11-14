# Suite 5 Review Link Studio
Merging this branch makes the staff page available at https://suite5management.com/reviews/ through the existing GitHub Pages configuration. It does not modify the homepage.

## Working after merge
Manual input of a verified Google Place ID, copyable Google review link, QR download, browser-local saved clients, and CSV export. Test every Google URL before writing or locking an NFC card.

## Enable automatic business search
1. In Google Cloud, enable Places API (New), connect billing, and configure quotas/alerts.
2. Create a Google Places API key. Never add it to GitHub or browser code.
3. Deploy reviews/worker.js as a separate Cloudflare Worker.
4. In Cloudflare Worker secrets, set GOOGLE_PLACES_API_KEY.
5. Replace https://REPLACE-WITH-YOUR-WORKER.workers.dev/api/search in reviews/index.html with the deployed Worker URL ending in /api/search, and commit.
6. Test the query and verify business addresses.

## Security / limitations
The public GitHub Pages staff page has no login yet. The Worker origin restriction is NOT authentication. Before production, add proper staff authentication and server-side rate limiting. Client records are saved to each employee's browser, NOT synchronized across staff. Export client CSV backups. Google Places Text Search including displayName and formattedAddress is billed at Text Search Pro tier; check current allowances. QR library loads from cdnjs.
