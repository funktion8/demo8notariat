# demo8notariat

Dieses Repository ist ein getrenntes NaC-Datenziel.

## Zweck

- Demo- und Testdaten aus NaC aufnehmen.
- Vorgangsstände getrennt vom Produktrepo `ofunk/NaC` versionieren.
- Den späteren Wechsel auf einen Sovereign-/DSGVO-Git-Anbieter vorbereiten.

## Grenze

Dieses GitHub-Repository ist nur für synthetische Demo-Daten gedacht. Produktive
Notariatsdaten, PINs, Kartenrohdaten, Zugangsdaten, Registerauszüge,
Ausweisdaten und Mandatsdokumente gehören nicht hierher.

## NaC-Bedienung

```bash
python scripts/nac.py tenant status --repo ../demo8notariat
python scripts/nac.py tenant write-demo immobilienkaufvertrag --repo ../demo8notariat
```
