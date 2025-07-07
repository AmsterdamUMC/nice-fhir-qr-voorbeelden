
# actiegerichte-indicatoren-2026Q1
## Medicatietoediening
> 2025-06-27: Let op: er worden nog details uitgezocht, verwachting is dat het niet meer veranderd.
> De valusets en de questionnaire zijn gemaakt maar het voorbeeld nog niet. 

Graag willen we alle medicatie ontvangen van de IC opnames. Om dit zo breed mogelijk op te zetten, is er uit gegaan
van de zibs `Farmaceuthisch Product` en `Medicatie Toediening`. De toediening bepaalt o.a. hoeveel, wanneer en de snelheid
terwijl het farmaceuthisch product het wat aangeeft, door dan wel een productcode aan te gegeven of wanneer het om 
een samengesteld product gaat waardoor er geen productcode bestaat, dan kan worden de ingredienten opgegeven inclusief
sterkte. 

Wanneer medicatie aan een patient wordt gegeven, spreken we van een medicatietoediening. Hier wordt vastgelegd wanneer
dit is gebeurt, hoeveel is toegediend, via welke weg en indien van toepassing, de snelheid van toediening. Teven 
wordt hier verwezen naar een medicatieafspraak (of medicatie opdracht). Hiet is mogelijk dat er in een opdracht meerdere
medicaties worden opgenomen. In dat geval krijgen de records dezelfde medicatieafspraak_id, maar wel een eigen toedienings_id. 
Hier is wel de verwachting dat 1 medicatie opdracht met meerdere producten dezelfde toedieningsdatumtijd krijgen. Met andere
woorden dat de medicatie gelijktijdig wordt gegeven.

In het farmaceutisch product wordt opgegeven welke medicatie is gebruikt. Wanneer een enkelvoudig middel is gebruikt, 
kan hier eenvoudig code uit het prk systeem worden opgegeven. Wanneer het om een samengesteld product gaat, dan blijft
de product_code leeg, maar wordt het ingredient opgegven, inclusief de sterkte. 
Net als in de medicatietoediening wordt hier de medicatieafspraak_id opgenomen; indien er meerdere ingredienten nodig 
zijn, dan kunnen we aan de hand van de medicatieafspraak_id zien dat het een samengesteld product is.

## Lab
- moet nog uitgewerkt worden.


# actiegerichte-indicatoren-2025Q4
In deze release zal medicatietoediening en labuitslagen worden toegevoegd. 
> Het toevoegen van medicatietoediening is complexer dat aangenomen, daarom zal deze uitbreiding naar 2026Q1 gaan.


# actiegerichte-indicatoren-2025Q3
De antibiotica indicator en de ai_kweek gaan veranderen naar ai_medicatietoediening en ai_labuitslag. Dit is echter een
grote aanpassing waarvoor meer tijd nodig is. Omdat er nog geen ziekenhuizen zijn die deze indicatoren aanleveren,
is ervoor gekozen om deze indicatoren uit de 2025Q3 te halen en tevens pas in 2025Q4 de nieuwe definitie voor
de medicatie en labuitslagen te introduceren.

* group `ai_kweek` is verwijderd. In de volgende release zal dit als labuitslagen terugkomen.
* group `ai_medicatietoediening` is in deze release verwijderd, en zal in 2025Q4 worden opgenomen.
* groep `ai_spiegel` is verwijder.
* groep `ai_sdd_sod` en de onderliggen items zijn vervallen.

Verder:
* `isGevalideerd` is required gemaakt.
* `beadm_modus` was een integer, maar had een code moeten zijn. Daarom is het type aangepast naar choice met een verwijzing naar nieuwe codesystem https://fhir.stichting-nice.nl/R4/ValueSet/bead-modus-2025Q3
* `pao2_id` is required gemaakt omdat het onderdeel is van de primary key.
* `ery_id` is required gemaakt omdat het onderdeel is van de primary key.
* `hb_tijd` is required gemaakt omdat het onderdeel is van de primary key.
* `pijn_no` is required gemaakt omdat het onderdeel is van de primary key.


# actiegerichte-indicatoren-2025Q1
Het item `isGevalideerd` stond in 2024Q1 tussen de andere velden. Dit veld geeft aan dat de opname is gecontroleerd, ook waarnaar er meerdere records voor opname worden verzameld. In de questionnaire van de actiegerichte-indicatoren zijn meerdere tabellen voor de opname, in totaal zijn er 13 `isGevalideerd` velden nu vervangen door 1 `isGevalideerd` voor de gehele questionnaire.

`toediening_volgnr` stond op de verkeerde plaats. De linkId's worden alfabetisch gesorteerd.


# actiegerichte-indicatoren-2024Q1 (deprecated)
Eerste opzet.