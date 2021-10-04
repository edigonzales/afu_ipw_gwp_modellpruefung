# afu_ipw_gwp_modellpruefung

## Links
- https://github.com/edigonzales/afu_ipw_gwp_datenumbau
- https://github.com/edigonzales-dumpster/afu_ipw_gwp_models_test

## Datenbank
```
docker run -p 54321:5432 -e POSTGRES_DB=edit -e POSTGRES_PASSWORD=mysecretpassword postgis/postgis:13-3.1
```

## Variante 1: Constraints im GWP-Modell bei betroffener Klasse
Exemplarisch "Eigentümer"-Existence-Contraint in das GWP-13.1-Modell bei der betroffenen Klasse (Hydrant) definiert.

### Objekt nicht gefunden
```
java -jar /Users/stefan/apps/ilivalidator-1.11.10/ilivalidator-1.11.10.jar --modeldir modelsv1 gwp_13_1.xtf
```

```
Error: line 99: GWP_Bern_13_1.SIA405_Wasser_GWP.Hydrant: tid ch18tp5x6gVoZrHo: The value of the attribute Eigentuemer of GWP_Bern_13_1.SIA405_Wasser_GWP.Hydrant was not found in the condition class.
```

### Objekt wird in Organisation-Transferfile gefunden
```
java -jar /Users/stefan/apps/ilivalidator-1.11.10/ilivalidator-1.11.10.jar --modeldir modelsv1 organisation.xtf gwp_13_1.xtf
```

## Variante 2: Zusätzliches Modell mit View für ilivalidator

### Kein Fehler (Zusatzmodell nicht bekannt)
```
java -jar /Users/stefan/apps/ilivalidator-1.11.10/ilivalidator-1.11.10.jar --modeldir modelsv2 gwp_13_1.xtf
```

### Fehler (Zusatzmodell ist bekannt)
```
java -jar /Users/stefan/apps/ilivalidator-1.11.10/ilivalidator-1.11.10.jar --modeldir modelsv2 --config modelsv2/config.toml gwp_13_1.xtf
```
Führt zu Fehlermeldung:
```
Error: line 99: GWP_Bern_13_1.SIA405_Wasser_GWP.Hydrant: tid ch18tp5x6gVoZrHo: The value of the attribute Eigentuemer of GWP_Bern_13_1.SIA405_Wasser_GWP.Hydrant was not found in the condition class.
```

### Kein Fehler (Objekt in organisation.xtf gefunden)
```
java -jar /Users/stefan/apps/ilivalidator-1.11.10/ilivalidator-1.11.10.jar --modeldir modelsv2 --config modelsv2/config.toml organisation.xtf gwp_13_1.xtf
```
