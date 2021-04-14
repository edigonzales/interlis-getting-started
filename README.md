# INTERLIS: Getting started 

```
docker-compose build
docker-compose up edit-db
```

Leere Tabellen in DB erstellen:
```
java -jar /Users/stefan/apps/ili2pg-4.4.5/ili2pg-4.4.5.jar --dbhost localhost --dbport 54321 --dbdatabase edit --dbschema grundbuch_v1 --dbusr admin --dbpwd admin --nameByTopic --defaultSrsCode 2056 --createGeomIdx --createFk --createFkIdx --createUnique --createEnumTabs --beautifyEnumDispName --createMetaInfo --createNumChecks --nameByTopic --strokeArcs --modeldir ".;http://models.geo.admin.ch" --models SO_AGI_Grundbuch_20210413 --schemaimport
```

Andere Vererbungsregeln:
```
java -jar /Users/stefan/apps/ili2pg-4.4.5/ili2pg-4.4.5.jar --dbhost localhost --dbport 54321 --dbdatabase edit --dbschema grundbuch_v2 --dbusr admin --dbpwd admin --nameByTopic --defaultSrsCode 2056 --createGeomIdx --createFk --createFkIdx --createUnique --createEnumTabs --beautifyEnumDispName --createMetaInfo --createNumChecks --nameByTopic --strokeArcs --smart2Inheritance --modeldir ".;http://models.geo.admin.ch" --models SO_AGI_Grundbuch_20210413 --schemaimport
```

Datenerfassung z.B. mit QGIS (Desktop-GIS). 

Export ebenfalls mit ili2pg / ili2db.
```
java -jar /Users/stefan/apps/ili2pg-4.4.5/ili2pg-4.4.5.jar --dbhost localhost --dbport 54321 --dbdatabase edit --dbschema grundbuch_v2 --dbusr admin --dbpwd admin --nameByTopic --defaultSrsCode 2056 --createGeomIdx --createFk --createFkIdx --createUnique --createEnumTabs --beautifyEnumDispName --createMetaInfo --createNumChecks --nameByTopic --strokeArcs --smart2Inheritance --disableValidation --modeldir ".;http://models.geo.admin.ch" --models SO_AGI_Grundbuch_20210413 --export grundbuch_20210419.xtf

xmllint --format grundbuch_20210419.xtf -o grundbuch_20210419.xtf
```

Datenprüfung:
```
java -jar /Users/stefan/apps/ilivalidator-1.11.9/ilivalidator-1.11.9.jar --modeldir ".;http://models.geo.admin.ch" grundbuch_20210419.xtf
```

Prüfung schlägt fehl, weil E-GRID falsch ist: Startet mit "DE" anstatt "CH".

