# Einspielen (nur aus einem Tag)

Stand 25.09.2026. Das Repo enthält nur Videos (`*.mp4`) und den Veröffentlichungsplan
`upload_plan.json`, keinen Code. Welcher Dienst den Plan abarbeitet: *nicht gefunden* im Repo.

## Regel

- Ein Upload-Lauf darf nur einen getaggten Stand von `upload_plan.json` verwenden (Tag `plan-JJJJ-MM-TT`
  oder `vX.Y`), damit nachvollziehbar ist, welcher Plan veröffentlicht wurde.
- Veröffentlichen ist ein Versand nach außen und braucht Edgars ausdrückliche Freigabe.

## Ablauf

1. Plan-Änderung auf Branch, MR, Pipeline grün (Geheimnis-Sperre, JSON wird von ruff nicht geprüft).
2. Merge nach `main`, Tag setzen.
3. Der Upload-Dienst liest den Plan aus dem Tag, nicht aus einem Branch.

## Rückweg

Vorherigen Tag als Plan-Quelle setzen. Bereits veröffentlichte Videos holt das nicht zurück.

## Offen

- Keine Prüfung des Plans in der CI (Schema, Zeitstempel in der Zukunft, Datei existiert).
