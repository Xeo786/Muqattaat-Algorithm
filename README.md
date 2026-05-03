# Muqatta'at Algorithm — Surah Qaf

An interactive visual proof of the recursive branching algorithm hidden in the Muqatta'at (the disjointed letters) of **Surah Qaf** (Chapter 50 of the Qur'an).

**Live demo:** https://xeo786.github.io/Muqattaat-Algorithm/

**Original theory video by Sabri Ben Rommane:** https://www.youtube.com/watch?v=-8P-D_agsdc

---

## What this is

Surah Qaf opens with the single Arabic letter **ق (Qaf)** — one of the 29 chapters of the Qur'an that begin with mysterious "disjointed letters" whose meaning has been debated for over 1,400 years.

This page is an interactive visualizer that walks through a recursive expansion algorithm, starting from that single seed letter, and shows how it produces a tree whose **leaves at Level 4 number exactly 45 — the precise number of verses in Surah Qaf**.

## What it proves

Starting from the seed `ق` and applying a fixed phonetic-spelling rule to each letter at every step:

| Letter | Expands to |
|--------|------------|
| ق (Qaf) | ق + ا + ف |
| ا (Alif) | ا + ل + ف |
| ف (Fa) | ف + ا |
| ل (Lam) | ل + ا + م |
| م (Mim) | م + ي + م |
| ي (Ya) | ي + ا |

…the recursion produces:

- **Level 1** — 3 letters → mapping the **3 major sections** of Surah Qaf
- **Level 2** — 8 letters → mapping the **8 subsections**
- **Level 3** — 17 letters → mapping the **17 thematic verse groups**
- **Level 4** — **45 letters** → mapping the **45 verses one-to-one**

Click any node in the left-hand tree to scroll to the corresponding section, group, or verse on the right. Verses are pulled live from the Qur'an translation API (Asad translation) so the mapping can be inspected in plain English.

## How to read the visualizer

- **Left panel** — the recursive expansion tree (Level 1 → Level 4)
- **Right panel** — Surah Qaf rendered with verses grouped by the algorithm's predicted boundaries
- **Hover / click** — highlights the corresponding group or verse

## What the HTML page actually does

The page is a single self-contained HTML file (no build step, no backend). When opened in a browser:

1. **Builds the tree in JavaScript.** Starting from the seed letter `Qaf`, a recursive function `buildTree()` applies the six phonetic-expansion rules above, four levels deep. Each node remembers its level, its parent group, and — at Level 4 — its assigned verse number (1–45).
2. **Renders the left panel** by walking the tree and emitting nested `<div>` elements with badges for *Major Section*, *Subsection*, *Group*, and *Verse*. Group nodes are made clickable; verse nodes are made hoverable so they highlight their parent group on the right.
3. **Fetches the Qur'an verses live from a public API.** On load, the page calls:

   ```
   GET https://api.alquran.cloud/v1/surah/50/en.asad
   ```

   This returns all 45 verses of Surah Qaf with the Muhammad Asad English translation. No API key is required — the call is made from the browser via `fetch()`.
4. **Aligns the API response with the algorithm's groups.** The 45 returned verses are walked in order, and each Level-3 node from the tree consumes as many verses as it has Level-4 children. The result: the algorithm dictates the group boundaries, and the API supplies the actual verse text that lands inside each group.
5. **Cross-links the two panels.** Clicking a Group node on the left scrolls and highlights the matching block of verses on the right; hovering a verse node on the left highlights its parent group; clicking it scrolls to the exact verse and pulses it.

Because the rules, the mapping, and the API call are all visible in the page source, anyone can verify that nothing is hard-coded — the 45-verse alignment falls out of the recursion, not out of a lookup table.

## Credit

The algorithm and the structural mapping it reveals are the discovery of **Sabri Ben Rommane**. This repository is an interactive visualization of his published theory.

- Theory video: https://www.youtube.com/watch?v=-8P-D_agsdc
- Surah Qaf on Quran.com: https://quran.com/50
