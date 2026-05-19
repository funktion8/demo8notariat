# NaC-Datenmodell

Dieses Repository speichert Akten als kleine, stabile JSON-Datensätze mit IDs
und Pointer-Beziehungen. Große oder binäre Inhalte liegen als Dateien neben den
Metadaten.

## Leitidee

- JSON hält die fachliche Struktur lesbar.
- IDs verbinden Akte, Personen, Dokumente und Ereignisse.
- Binärdateien wie PDF, JPG oder Scans bleiben als Dateien erhalten.
- Indizes sind Ableitungen für Webapp, Suche und Codex.
- Ereignisse werden zusätzlich als JSONL journalisiert.

## Kernobjekte

| Objekt | Pfad | Zweck |
| --- | --- | --- |
| Akte | `akten/<jahr>/<akten_id>/akte.json` | Aktenzeichen, Status, Notar, Beteiligte, Dokumente, Pointer. |
| Beteiligte | `personen/<person_id>.json` | Person, Organisation, Rollen und Stammdaten. |
| Dokument | `dokumente/<document_id>/metadata.json` | Titel, Typ, Aktenbezug, Dateipfade, Klassifikation. |
| Binärdatei | `dokumente/<document_id>/original/*` | PDF, JPG, Scan oder andere Originaldatei. |
| Aktenereignis | `akten/<jahr>/<akten_id>/ereignisse.jsonl` | Chronologie innerhalb einer Akte. |
| Journal | `journal/<jahr>/<monat>/<datum>.jsonl` | Repo-weite Ereignisfolge. |
| Index | `index/*.json` | Leselisten für Webapp, Suche und Codex. |

## Pointer

Eine Akte speichert nicht alle Person- oder Dokumentdaten inline. Sie verweist
auf IDs:

```json
{
  "matter_id": "UVZ-2026-0001",
  "participant_person_ids": ["PER-DEMO-VERKAEUFER-ANNA-BERGER"],
  "document_ids": ["DOC-DEMO-2026-0001-GRUNDBUCH"]
}
```

Codex und die Webapp lesen zuerst `akte.json` und laden danach die referenzierten
Personen, Dokumente und Ereignisse.
