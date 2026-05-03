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

## Credit

The algorithm and the structural mapping it reveals are the discovery of **Sabri Ben Rommane**. This repository is an interactive visualization of his published theory.

- Theory video: https://www.youtube.com/watch?v=-8P-D_agsdc
- Surah Qaf on Quran.com: https://quran.com/50
