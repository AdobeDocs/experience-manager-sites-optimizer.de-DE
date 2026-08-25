---
source-git-commit: 2a3a02ea04fac7ce37fdc43e836a4832be224e25
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---
# ASO Doc Agent — Lerninhalte überprüfen

Dauerhafte Lektionen, die aus menschlichem PR-Feedback zu den eigenen PRs dieses Agenten extrahiert wurden. Lesen
diese Datei zu Beginn von Schritt 4 (Forschung + Entwurf) in `pipeline.md`, bevor sie erstellt wird
Irgendetwas - Der Punkt ist, dass eine Korrektur, die ein Validierungsverantwortlicher einmal vornimmt, nicht sein muss
Erneut auf einem zukünftigen Ticket erstellt.

## Was hier gehört

Nur **generalisierbares** Feedback - ein Muster, das bei zukünftigen Tickets wiederkehren wird, etwa
Ton, Struktur, fehlende Abschnitte, falsche Dateiplatzierung oder Inhaltsgenauigkeit. Beispiele:

- „Erwähnen Sie immer die Registerkarte Ignoriert für Gelegenheiten, die Ignorieren/Überspringen unterstützen.“
- „Behaupten Sie kein Gating auf Ultimate-Ebene, es sei denn, das Ticket oder eine vorhandene gleichrangige Seite bestätigen dies. Lassen Sie es auskommentiert und markieren Sie es stattdessen als offenes Element.“
- „Für neue Opportunity-Anleitungen sind ein TOC.md-Eintrag und ein Kartenraster-Eintrag auf der Landingpage „Opportunity-Types“ erforderlich, nicht nur der Eintrag selbst.“

## Was nicht hierher gehört

Einmaliges, mechanisches Feedback, das nur für eine einzelne PR gilt: Tippfehler, ein defekter Link, ein
Fehlendes Komma, falscher Dateipfad in dieser spezifischen PR. Korrigieren Sie diese direkt in der PR - sie
Verallgemeinern Sie nicht auf zukünftige Entwürfe, sodass ein dauerhafter Eintrag nur Rauschen wäre.

## Eingabeformat

```markdown
## YYYY-MM-DD — SITES-XXXXX (PR #NN)

**Lesson:** [one or two sentences — the generalizable rule]

**Why:** [what the reviewer actually said, or the specific mistake it corrects]

**Applies to:** [which ticket types / pages this affects — "all opportunity how-to pages", "settings/setup pages", "everything", etc.]
```

Neueste Einträge oben. Wenn eine spätere Lektion eine frühere Lektion ersetzt oder einengt, bearbeiten Sie
Der frühere Eintrag zu beachten, dass anstatt zwei widersprüchliche Regeln in der Datei.

---

Noch keine Einträge - diese Datei erhält ihren ersten Eintrag, wenn ein Mensch zum ersten Mal Änderungen anfordert
in einem der PRs dieses Agenten.
