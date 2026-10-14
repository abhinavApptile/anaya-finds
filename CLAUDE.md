# Anaya's Amazon Finds: link-in-bio site

## What this is
A single-page link-in-bio site for "Anaya", an AI-generated Instagram fashion creator who posts Amazon India finds under ₹999. Viewers see a "find number" (e.g. #003) in a reel, open this page from her Instagram bio, type the number, and tap through to Amazon. Income comes from Amazon Associates affiliate links. Hosted on GitHub Pages from the `main` branch root.

## Files
- `index.html`: the entire site (HTML, CSS and JS in one file). No build step, no framework, no dependencies besides Google Fonts.
- `avatar.jpg`: optional profile photo. The page falls back to the letter "A" if it's missing.

## Where data lives
All content is in the block between `EDIT THIS SECTION ONLY` and `END OF EDITABLE SECTION` inside the <script> tag:
- `INSTAGRAM_HANDLE`: her handle without the @.
- `REELS`: an array of reels, NEWEST FIRST. Each reel has `title`, `when` (e.g. "October 2026") and `finds`.
- Each find has: `id` (3-digit string like "005"), `name`, `brand`, `category`, `note` (one short line in Anaya's practical voice), `link`, and optionally `gone: true` when out of stock.

For routine content changes, edit only this block. Do not touch the CSS or rendering code unless I explicitly ask for a design or feature change.

## Rules (always follow)
1. Find IDs are permanent. Never renumber, reuse or delete an ID, even for out-of-stock items. New finds get the next number after the highest existing ID across ALL reels.
2. Out of stock means `gone: true`, never deletion.
3. Affiliate links must be my Amazon Associates short links (amzn.to/...) or amazon.in links containing my associate tag. If I give you a plain amazon.in product link, add it but warn me clearly that it won't earn commission until I replace it.
4. Never add prices anywhere on the site. Amazon prices change constantly and the Associates rules restrict showing them.
5. Never add or hotlink Amazon product images.
6. Never remove or reword the footer line "As an Amazon Associate I earn from qualifying purchases." Amazon requires it.
7. Never remove the "I'm an AI-generated creator" label in the header.
8. Every product link must keep `rel="sponsored nofollow noopener"` (the render code handles this; don't bypass it).
9. Keep `category` values consistent with existing ones (currently "Kurta sets" and "Dresses"). Only create a new category if nothing existing fits, and tell me when you do. Filter chips are generated from categories automatically.
10. Notes stay honest: only describe fabric, fit or quality based on what the listing or reviews actually say, never invented claims.

## Common tasks
- "Add a new reel": I'll give a reel title and products (name, brand, category, link). Insert the new reel at the TOP of REELS, assign the next IDs in order, and write a short note per product if I don't supply one.
- "Replace links": I'll paste find IDs with new amzn.to links. Update only those `link` values.
- "Mark #XXX out of stock" / "back in stock": add or remove `gone: true`.
- "Which links aren't affiliate links yet?": list every find whose link is not an amzn.to link or lacks my associate tag.

## After every change
1. Extract the <script> content and run `node --check` on it to catch syntax errors.
2. Check for duplicate IDs and that IDs are sequential with no reuse.
3. Show me a short summary of what changed (IDs added or edited, links replaced, warnings).
4. Commit with a clear message, e.g. "Add reel: Office week, finds #005–#008" or "Swap affiliate links for #001–#004".
5. Push to `main` right after committing (`git push`); I don't need to be asked. Pushing publishes the change live.

## Style
Keep explanations short. If a request would break one of the rules above, say which rule and suggest the closest compliant option instead of doing it.
