# afu_ipw_gwp_modellpruefung

## Links
- https://github.com/edigonzales/afu_ipw_gwp_datenumbau
- https://github.com/edigonzales-dumpster/afu_ipw_gwp_models_test

## Datenbank
```
docker run -p 54321:5432 -e POSTGRES_DB=edit -e POSTGRES_PASSWORD=mysecretpassword postgis/postgis:13-3.1
```

## GWP-Daten importieren (13.1)
```
java -jar /Users/stefan/apps/ili2pg-4.5.0/ili2pg-4.5.0.jar --dbhost localhost --dbport 54321 --dbdatabase edit --dbusr gretl --dbpwd gretl --dbschema gwp --smart2Inheritance --createNumChecks --createUnique --createFk --createFkIdx --sqlEnableNull --createGeomIdx --createMetaInfo  --createTidCol --importTid --strokeArcs --defaultSrsCode 2056 --modeldir models/ --models "GWP_Bern_13_1" --schemaimport

```


java -jar /Users/stefan/apps/ili2pg-4.5.0/ili2pg-4.5.0.jar --dbhost localhost --dbport 54321 --dbdatabase edit --dbusr postgres --dbpwd mysecretpassword --dbschema wasser --smart2Inheritance --createNumChecks --createUnique --createFk --createFkIdx --sqlEnableNull --createGeomIdx --createMetaInfo  --createTidCol --importTid --strokeArcs --defaultSrsCode 2056  --models "SIA405_WASSER_2015_LV95" --disableValidation --doSchemaImport --import Biberist_Wasser_SIA405_orig.xtf