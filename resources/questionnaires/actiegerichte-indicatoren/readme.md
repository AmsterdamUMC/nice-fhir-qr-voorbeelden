

# actiegerichte-indicatoren-2025Q3
* `isGevalideerd` is required gemaakt.
* `beadm_modus` was een integer, maar had een code moeten zijn. Daarom is het type aangepast naar choice met een verwijzing naar nieuwe codesystem https://fhir.stichting-nice.nl/R4/ValueSet/bead-modus-2023Q3
* `pao2_id` is required gemaakt omdat het onderdeel is van de primary key.
* `ery_id` is required gemaakt omdat het onderdeel is van de primary key.
* `hb_tijd` is required gemaakt omdat het onderdeel is van de primary key.
* `kweek_id` is required gemaakt omdat het onderdeel is van de primary key.
* `toediening_volgnr` is required gemaakt omdat het onderdeel is van de primary key.
* `pijn_no` is required gemaakt omdat het onderdeel is van de primary key.
* `spiegel_volgnr` is required gemaakt omdat het onderdeel is van de primary key.
* `trans_trig_tijd` is required gemaakt omdat het onderdeel is van de primary key.
* `trombo_uit_tijd` is required gemaakt omdat het onderdeel is van de primary key.
* Het item `ai_sdd_sod` en de onderliggen items zijn vervallen.


# actiegerichte-indicatoren-2025Q1
Het item `isGevalideerd` stond in 2024Q1 tussen de andere velden. Dit veld geeft aan dat de opname is gecontroleerd, ook waarnaar er meerdere records voor opname worden verzameld. In de questionnaire van de actiegerichte-indicatoren zijn meerdere tabellen voor de opname, in totaal zijn er 13 `isGevalideerd` velden nu vervangen door 1 `isGevalideerd` voor de gehele questionnaire.

`toediening_volgnr` stond op de verkeerde plaats. De linkId's worden alfabetisch gesorteerd.


# actiegerichte-indicatoren-2024Q1 (deprecated)
Eerste opzet.