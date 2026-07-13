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
## Pond ecosystem tracker — "Tyosphere" (`pond/`)

- `pond/index.html` is a **password-protected, encrypted** pond ecosystem
  tracker named **Tyosphere** (pots, plants, fish, critters, care log),
  private to the user, served at
  `https://smithtl12.github.io/smith-reunion-2026/pond/`.
- The user's husband owns the `vintnervineyard` repo (vintnersvineyard.com),
  which has a real cloud backend (login + database, entries sync across
  devices). Standing direction from the user (2026-07-03): **if he asks for a
  future app with automatic cloud saving, build it off vintnersvineyard**
  rather than GitHub Pages + localStorage.
- Encrypted exactly like the family + recruiting pages (gzip → AES-256-GCM,
  key from PBKDF2-SHA256 with 150,000 iterations; DATA = ciphertext+tag,
  base64). The gate lowercases + trims the typed password before deriving the
  key.
- **Deliberately unlisted** — do NOT link it from the reunion homepage, the
  recruiting page, or anywhere else. It is for the user only.
- Unlike recruiting, the encrypted payload contains only the **app**, no data:
  the user adds pots/plants/fish and logs dated status entries (thriving,
  struggling, reproducing, died…) right in the browser, and everything is
  stored in `localStorage` on his device under the key `pond_tracker_v1`,
  with Back up / Restore buttons (JSON file). So the inner HTML can be rebuilt
  and re-encrypted at any time without losing his data. If he asks to "bake
  in" his data, have him send a backup JSON (or paste it), seed it as initial
  data in the app, and re-encrypt.
- The password + maintenance instructions live in a Google Doc named
  **"Pond tracker — password & how it works"** in the user's Google Drive.
- To update: rebuild the inner HTML, re-encrypt the same way, commit on a
  feature branch, push, open a PR, and merge it (standing permission).
- **Dates — the user is in California (Pacific time, PST/PDT) and the system
  clock is UTC. ALWAYS log tracker entries under the Pacific date — do the
  conversion, do NOT paste the system date.** The system clock runs 7–8 h
  AHEAD of Pacific, so any Pacific event from **~5 PM onward** ("tonight", "this
  evening", "at sunset", late-night) is already the NEXT day in UTC — which
  means the correct Pacific date is **the system date MINUS ONE**. Subtract it;
  don't trust the system date for anything after Pacific afternoon. This exact
  slip has mis-dated evening entries a day ahead more than once (temp readings,
  the buce gluing, the crystal-clear night view). Anchor to the day the user
  names ("today" / "this morning" / "last night" / "yesterday"); if the local
  day is genuinely ambiguous, ask before writing it.
- **Tank interior footprint:** 65⅜″ wide × 102″ long overall, in two depths —
  a shallow **reef-side upper ledge/terrace** (65⅜″ × 33½″) and the **deep
  side** (65⅜″ × 68½″). The temple/columns + white pool-sand sifter zone go on
  the reef ledge; the black slag floor is the deep bottom.
  - **Water depth (sand in):** deep side **63″**, reef terrace **47½″** (sand
    surface → water surface), so the terrace floor sits ~15½″ higher than the
    deep floor. A **2½″ dry rim** (freeboard) sits above the current water
    level.
  - **Measured water volume ≈ 1,670 gal** gross (above the sand); ≈ 1,550–1,650
    gal effective after the brick/pots/rock displace some. (The old "~2,100
    gal" was a rough full-box estimate.)
- **System / equipment spec lives IN the tracker, not here** (Tyson's request —
  keep this file lean). The encrypted pond page's **About panel** holds the
  full, authoritative spec: System · Water · Filtration & flow · UV · Carbon ·
  Heat · Electrical · Substrate. When Tyson says **"recall"** (a device, a spec,
  or the whole system), unlock + decrypt the pond page and read it from there
  instead of re-deriving. One fact worth keeping loaded so it's never re-guessed
  wrong: the **2 inline heaters are HydroQuip PH301-15UP, 1.5 kW / 120 V, ~13 A
  each — NOT 20 A** (that's the dedicated GFCI circuit, already wired). Heater
  controllers must be **15 A class** (bayite BTC211 or BN-LINK 15 A/1,875 W) —
  never a 10 A unit.
- **This is a TOP-DOWN aquarium — a large in-ground tank (~1,670 gal measured;
  the old "~2,100 gal" was a rough estimate) viewed from above (looking down
  into the water), NOT sideways through glass.** This
  drives all stocking/aesthetic advice, so weigh it in every future chat:
  - The **sand floor is the whole visual background** (there is no back wall
    to view fish against), so substrate color matters more than in a normal
    tank. The user has committed to **black sand** (already bought ~$300) and
    is keeping it; may blend in pool-filter sand to lift contrast.
  - Fish are **countershaded** (dark backs), so from above they camouflage
    against dark sand. What makes a fish pop top-down, in priority order:
    **(1) brightness / color contrast against black** (white, gold, orange,
    red, yellow) — this dominates; **(2) size** — bigger = easier to spot;
    **(3) movement** — slow cruisers that bank and turn flash their color.
    **Shape is a distant fourth.** A bright, large fish breaks the shape
    rule: the red-devil angel (Trinity) is tall and thin yet pops
    magnificently and is very easy to spot, and the bright incoming angels
    should too. So the real thing to avoid is **dark or dull side-view
    fish** — silver/drab torpedo fish whose color lives on the flanks
    (rainbowfish disappointed for exactly this reason) — NOT tall fish per
    se. Fish also get more visible as they grow (more size, and color
    matures in), so a drab juvenile isn't the final verdict.
  - His proven top-down winners: **white cloud minnows, Florida flagfish,
    mollies, platies** (livebearers especially), and the **Bolivian rams**
    — a bold, mid-water cichlid (unlike shy bottom-hugging German blue rams),
    proof that the right cichlids show well top-down. Good future directions:
    more livebearers (swordtails, fancy mollies), killifish, gouramis,
    and gold/white/albino morphs. Rainbowfish have disappointed (side-view
    fish).

- Style note for drafting candidate emails: the user signs informally as just
  "Tyson" (he is a DO, not an MD — never sign him "MD"), keeps a friendly
  peer-to-peer tone, and always closes by asking the candidate to text him
  directly at 415-867-4700 to coordinate a time to talk.
- NEVER use the word "honestly" in drafted text — it's a trigger word for the
  user (implies prior statements weren't honest).
