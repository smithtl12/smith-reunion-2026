# Working with this repo's owner (smithtl12)

These are standing preferences for Claude when helping this user.

- **The user is not a programmer.** Use plain, non-technical language. Avoid
  jargon (or briefly define it). Don't hand manual Git/GitHub steps back to the
  user when you're able to do them yourself.

- **Standing permission granted (by the user, on 2026-06-10):** Claude is
  authorized to carry out **deploy / push / pull-request / merge** actions on
  GitHub on the user's behalf, autonomously, without requiring the user to click
  through GitHub themselves. Proceed with these without asking each time.

  The only exceptions — pause and confirm first — are genuinely destructive or
  irreversible actions, e.g. deleting a repository, force-pushing over shared
  history, or removing live/published content.

## Anesthesia recruiting tracker (`recruiting/`)

- `recruiting/index.html` is a **password-protected, encrypted** candidate
  tracker for the user's anesthesia group (ACAMG), served by GitHub Pages at
  `https://smithtl12.github.io/smith-reunion-2026/recruiting/`.
- **This repo is PUBLIC. Never commit candidate names, phone numbers, emails,
  or any other recruiting data in plaintext.** The page payload is encrypted
  exactly like the family page in `index.html` (gzip → AES-256-GCM, key from
  PBKDF2-SHA256 with 150,000 iterations; DATA = ciphertext+tag, base64).
- The tracker password and maintenance instructions live in a Google Doc named
  "Recruiting tracker — password & how it works" inside the user's Google
  Drive folder **"2027 ACAMG recruitment"**.
- **The encrypted page is the single live source of truth.** The hiring
  "inner circle" (the user + 3 colleagues) all have the password and read the
  page directly. Do NOT regenerate Google Sheet snapshots on every update —
  the Drive folder is only used as a year-end historical archive (the user
  will ask for an export around the end of the year). Old sheets in the Drive
  folder are stale; ignore them.
- To update the tracker: get the password from that Drive doc, decrypt the
  current page payload (or rebuild the inner HTML), edit the `CANDIDATES`
  array, re-encrypt, commit on a feature branch, push, open a PR, and merge it
  (covered by the standing permission above).
- Style note for drafting candidate emails: the user signs informally as just
  "Tyson" (he is a DO, not an MD — never sign him "MD"), keeps a friendly
  peer-to-peer tone, and always closes by asking the candidate to text him
  directly at 415-867-4700 to coordinate a time to talk.
