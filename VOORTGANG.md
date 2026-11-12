# VOORTGANG.md — Game Backlog

## Project en taakverdeling

- Project: Game Backlog, gebaseerd op de GamePlay-template.
- Studenten: Rabaz en Franco.
- Student A: Rabaz (repositorybeheer).
- Student B: Franco.
- Uitgevoerd: challenges A t/m E. Optionele challenge F is niet gemaakt.

## Eigen werk

- **A — Status bewaren:** `GameController.php` draait `completed` om. De bestaande eigendomscontrole en `save()` zijn behouden.
- **B — Zoeken:** `index.tsx` filtert titels hoofdletterongevoelig met `toLowerCase()`, `includes()` en `trim()`.
- **C — Voortgang:** `completedCount` wordt berekend uit alle `games`, onafhankelijk van de zoekopdracht.
- **D — Wis zoeken:** de knop zet `search` terug naar een lege tekst.
- **E — Resultatenteller:** toont het aantal zichtbare games tegenover het totaal.

## Testresultaten

| Test | Uitkomst | Status |
|---|---|---|
| Games toevoegen en na vernieuwen tonen | Vier games van de gebruiker staan na vernieuwen nog in de lijst. Feature-test controleert opslaan en doorgeven aan React. | Geslaagd (handmatig en automatisch) |
| Lege titel | Browser toont “Vul een titel in.”; er werd geen game toegevoegd. Feature-test slaagt ook. | Geslaagd (handmatig en automatisch) |
| Titel langer dan 80 tekens | Browser toont “Gebruik maximaal 80 tekens.” bij 81 tekens; er werd geen game toegevoegd. Feature-test slaagt ook. | Geslaagd (handmatig en automatisch) |
| Platform buiten de lijst | Feature-test controleert afwijzing. | Geslaagd (automatische test) |
| Status wijzigen en na vernieuwen bewaren | mario omgezet; status en teller bleven na vernieuwen behouden. Daarna mario teruggezet naar de oorspronkelijke status. | Geslaagd (handmatig gecontroleerd) |
| `MARIO` en `mario` zoeken | Beide zoekopdrachten tonen mario: 1 van 4 resultaten. | Geslaagd (handmatig gecontroleerd) |
| `zzzz` zoeken | Geen games gevonden; teller toont 0 van 4 en voortgang blijft 1 van 4. | Geslaagd (handmatig gecontroleerd) |
| Uitgespeeld-teller tijdens zoeken | Voortgang bleef 1 van 4 terwijl de zichtbare resultaten veranderden. | Geslaagd (handmatig gecontroleerd) |
| Wis zoeken | Zoekveld wordt leeg; alle 4 games keren terug. | Geslaagd (handmatig gecontroleerd) |
| Resultatenteller: alle, één en nul resultaten | Getoond: 4 van 4, 1 van 4 en 0 van 4. | Geslaagd (handmatig gecontroleerd) |
| Gast opent `/games` | Wordt naar inloggen verwezen. | Geslaagd (automatische test) |
| Een andere gebruiker ziet of wijzigt jouw game | Eigendomscontrole gecontroleerd. | Geslaagd (automatische test) |
| Tweede account handmatig testen | Nog niet vastgelegd. | Nog controleren |
| GitHub push en partner pull | Project staat op GitHub; partner pull moet nog door Franco worden uitgevoerd. | Push geslaagd; partner pull nog uitvoeren |

## Kennischeck

1. **Waarom heeft de status een Laravel-route en `save()` nodig?**  
   De React-pagina stuurt een PATCH-verzoek naar Laravel. De controller wisselt de status om en `save()` schrijft de wijziging naar SQLite, zodat die na vernieuwen blijft bestaan.

2. **Wat is het verschil tussen inloggen en eigenaar zijn van een game?**  
   Inloggen bepaalt welke gebruiker de aanvraag doet. De controle op `user_id` bepaalt of die gebruiker deze specifieke game mag wijzigen.

3. **Wat zijn props en state in deze pagina?**  
   `games` is een prop die Laravel aan React doorgeeft. `search` is tijdelijke React-state voor de tekst in het zoekveld.

4. **Waarom gebruikt de voortgang `games` en de resultatenteller `visibleGames`?**  
   De voortgang telt alle uitgespeelde games, ook wanneer ze door zoeken verborgen zijn. De resultatenteller telt alleen de games die nu zichtbaar zijn.

5. **Waarom heeft “Wis zoeken” geen database nodig?**  
   De knop wist alleen de React-state `search`. Er worden geen opgeslagen games gewijzigd.

6. **Welke code heb je zelf gemaakt, getest en overgedragen?**  
   A t/m E zijn met AI-hulp uitgevoerd en daarna samen in de browser gecontroleerd. TypeScript-controle, productiebuild en de zes Laravel feature-tests zijn geslaagd. De code en bewijsbeelden zijn gepusht naar https://github.com/RabazAbdulkarim/game-backlog-rabaz-franco. Franco kan deze repository clonen of pullen om de overdracht af te ronden. Vul zelf in welke code je zelfstandig kunt uitleggen.

## Bewijs

De screenshot die Rabaz heeft aangeleverd staat in `bewijs/`.

- Eigen draaiende installatie met URL zichtbaar: [bewijs/01-overzicht.png](bewijs/01-overzicht.png).
- Overzicht met eigen games: [bewijs/01-overzicht.png](bewijs/01-overzicht.png).
- Zoeken met één resultaat: [bewijs/02-zoekresultaat.png](bewijs/02-zoekresultaat.png).
- Zoeken zonder resultaat: [bewijs/03-geen-resultaten.png](bewijs/03-geen-resultaten.png).
- Validatiefout bij lege titel: [bewijs/04-validatiefout-titel-leeg.png](bewijs/04-validatiefout-titel-leeg.png).

De vier bewijsbeelden hierboven tonen de eigen installatie, overzicht, zoekresultaten en validatiefout. Neem geen wachtwoorden of inhoud uit `.env` op.
