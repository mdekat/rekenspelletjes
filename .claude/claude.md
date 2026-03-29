# Project: Rekenspelletjes

## Stack
- Statische HTML/CSS/JS website (alles in losse bestanden per spel)
- Gehost op GitHub Pages via `main` branch
- Geen frameworks, geen build-stap

## Structuur
```
index.html              → startpagina met spellenkaarten
splitsen/               → spel: getallenparen zoeken
optellen/               → spel: optelsommen (meerkeuze)
aftrekken/              → spel: minsommen (meerkeuze)
img/vierkant/           → vierkante afbeeldingen voor kaarten/achtergronden
CHANGELOG.md            → versieoverzicht
```

## Git-conventies
- Commitberichten in het **Nederlands**
- Tag elke release: `git tag vX.Y.0`
- Push commits én tags: `git push origin main && git push origin --tags`
- SSH-remote via alias `github-mdekat` (sleutel: `~/.ssh/id_ed25519_mdekat`)

## Workflow vóór het beginnen
Voer altijd eerst dit uit voordat je iets wijzigt:
```bash
git fetch origin && git status
```
Als de remote nieuwe commits heeft: `git pull origin main` vóór je verder gaat.

## Workflow na wijzigingen
1. Test lokaal in browser
2. `git add <bestanden>` (nooit `.claude/` committen)
3. `git commit -m "vX.Y.0: omschrijving"`
4. `git tag vX.Y.0`
5. `git push origin main && git push origin --tags`
6. CHANGELOG.md bijwerken

## Viewport / Responsive design

Alle pagina's hebben `<meta name="viewport" content="width=device-width, initial-scale=1.0">`.

### Breakpoints (in alle spelbestanden én index.html)

| Scherm        | Breedte        | Aanpassingen                                              |
|---------------|----------------|-----------------------------------------------------------|
| Smartphone    | ≤ 600px        | kleinere padding, kleinere fonts, score-bar wraps         |
| Tablet / iPad | 601 – 1024px   | iets bredere game-box (420px)                             |
| Laptop 16"    | ≥ 1025px       | standaard ontwerp (game-box 360px, max-width: 100%)       |

### Aandachtspunten bij nieuwe spellen
- Gebruik **nooit** een vaste `width` zonder `max-width: 100%` ernaast
- Game-box altijd: `width: 360px; max-width: 100%;`
- Voortgangsbalk altijd: `width: 340px; max-width: 100%;`
- Back-link: `position: absolute` is ok, maar verklein op ≤ 600px
- Antwoordknoppen: minimaal `padding: 14px` voor touch-gebruik op mobiel
- Font-sizes in `em` (schaalt mee), geen vaste `px` voor tekst

## Beloningssysteem (optellen & aftrekken)
Na `reeksDoelwit` goede antwoorden op rij wordt willekeurig één van zes
animaties getoond: confetti, ballonnen (SVG), vuurwerk, rollende emoji's,
explosie vanuit midden, dierenparade.

**Let op:** `reeksDoelwit = 3` is de testwaarde. Zet terug op `10` voor productie.
