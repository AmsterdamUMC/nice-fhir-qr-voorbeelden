# 2026Q1

In de release voor 2026Q1 zijn de belangrijkste veranderingen:
*  de toevoeging van de medicatietoediening en labuitslagen. Zie [Actiegerichte Indicatoren Readme](../resources/questionnaires/actiegerichte-indicatoren/readme.md)
*  De aanpassing in de zz_personeel; velden begin leerling verpleegkunidge en eind leerling verpleegkundigen 
worden samengevoegd tot een veld leerling verpleegkundigen. Zie [zz-personeel Readme](../resources/questionnaires/zz-personeel/readme.md)


#### 27 okt 2025
In de questionnaire voor de medicatietoedieningen kwam het id genaamd `toedienings_id` twee keer voor. Dit is logisch
data-technisch gezien als een verwijzing naar elkaar, maar de FHIR standaard staat niet toe dat een linkId twee keer 
voorkomt in een questionnaire. Daartoe wordt in het `toedienings_id` in het farmaceutisch product aangepast naar 
`toedienings_id_ref`. Hierdoor worden de linkid's weer uniek. De betekenis van beide velden blijven onveranderd.


#### 8 juli 2025
De questionnaires en valuesets zijn gemaakt, de voorbeelden in de vorm van de questionnaireResponses moeten nog gemaakt 
worden. Hiervoor moet er aanpassingen worden gemaakt in de software die de voorbeelden maakt, naar verwachting zullen 
deze snel volgen. 
