# 2025Q3


#### 14 maart 2025
Deze release is gemaakt en getest op de huidige FHIR server en op de nieuwe Fhir server, genaamd Chiba. Dit maakt dat als deze release
gebruikt wordt, er geen veranderingen nodig zijn wanneer de nieuwe server in gebruikt wordt genomen. Alleen de Server URL zal dan veranderen,
niet de inhoud (en dus ook de url's in de berichten) zullen veranderen.

Ook zijn de resources in dit project opgenomen. Dit zijn de codesystemen, valuesets en de questionnaires.  Met behulp van een voorbeeld
patient en de questionnaires zijn de voorbeeld questionnaireResponses gemaakt en vier voorbeelden van Bundles met questionnaireResponses.
Hierbij is gecontroleerd of het voorbeeld voor elke veld een waarde heeft. Dit verzekert dat in de questionnaireReponse het veld wordt 
opgenomen. Bijv het veld `numgraft` was null in 2025Q1, en viel daardoor weg in het voorbeeld. Dit terwijl het wel in de questionnaire
gedefinieerd.

Voor de aanpassingen in de questionnaires, kijk in de readme van de folder van de questionnaires. Bijvoorbeeld voor de questionnaire 
van de mds: [readme.md](https://github.com/AmsterdamUMC/nice-fhir-qr-voorbeelden/blob/master/resources/questionnaires/mds/readme.md#mds-2025q3)

Hieronder is een overzicht gemaakt van de veranderingen in de release 2025Q3 ten aanzien van 2025Q1.


## Ziekenhuisopname en ziekenhuis ontslag 
de veldnamen `adm_hosp_date` en `dis_hosp_date` zijn verwarrend geworden door de wijziging dat deze velden nu ook de tijd vastleggen. 
Voor de IC opname en IC ontslag is deze aanpassing al gedaan voor de FHIR (adm_icu, dis_icu). 
De aanpassingen:
* het veld `adm_date_hosp` wordt hernoemt naar `adm_hosp`.
* het veld `dis_date_hosp` wordt hernoemt naar `dis_hosp`.

Note: zowel de oude als nieuwe veldnaam wordt geacceptaard wanneer de dat niet met FHIR maar met een msAccess of een zip met csv's 
worden verstuurd.


## Productie informatie
Graag willen we weten met welk productie de informatie is samengesteld en opgestuurd. In de dataset zit dit al in de exportinfo. 
Voor de informatie die met FHIR wordt verstuurd, moet dit per Bundle. Dit kan met een van de twee questionnaires:
* [product-admission](https://stichting-nice.nl/dd/#11475): bedoeld om mee te sturen met de bundle `BundleAdmission` en heeft dus ook een combinatie van hospno, icno en admno.
* [product-organization](https://stichting-nice.nl/dd/#11480): bedoeld om mee te sturen met de bundle 'BundleOrganization` en heeft hospno, icno en datum. 
In beide questionniares dit de volgende velden, welke beschreven staan in de datadictionary
* [EPD](https://stichting-nice.nl/dd/#11476)
* [Producent](https://stichting-nice.nl/dd/#11478) 
* [Product](https://stichting-nice.nl/dd/#11477)
* [Versie](https://stichting-nice.nl/dd/#11479)

> De linkId van de product informatie was een geschreven met een min-teken. Dit gaf echter problemen, vandaar dat
> deze zijn vervangen door underscore. 


## Delirium 
In de ***actiegerichte-indicatoren*** questionnaire is delirium toegevoegd en kan meegestuurd worden met de BundleAdmission. Voor de delirium zijn 
de volgende velden toegevoegd: 
* [delier_id](https://stichting-nice.nl/dd/#11465)
* [delier_datumtijd](https://stichting-nice.nl/dd/#11462)
* [delier_instrument](https://stichting-nice.nl/dd/#11461)
* [delier_score](https://stichting-nice.nl/dd/#11464)

## actiegerichte-indicatoren
Naast de toevoeging van delirium, zijn er ook items verwijderd uit de questionnaire. Er wordt gewerkt aan de mogelijkheid om 
***mediciatietoediening*** en ***labuitslag*** toe te voegen aan de questionnaire. Hiervoor moeten er nog dingen worden uitgezocht
en daarom is besloten deze uitbreiding te verschuiven naar 2025Q4. In voorbereiding hiervan zijn de volgende aanpassingen  
gemaakt:
* group `ai_kweek` is verwijderd. In de volgende release zal dit als labuitslagen terugkomen.
* group `ai_medicatietoediening` is in deze release verwijderd, en zal in 2025Q4 worden opgenomen.
* groep `ai_spiegel` is verwijder.

Verder:
* `isGevalideerd` is required gemaakt.
* `beadm_modus` was een integer, maar had een code moeten zijn. Daarom is het type aangepast naar choice met een verwijzing naar nieuwe codesystem https://fhir.stichting-nice.nl/R4/ValueSet/bead-modus-2025Q3
* `pao2_id` is required gemaakt omdat het onderdeel is van de primary key.
* `ery_id` is required gemaakt omdat het onderdeel is van de primary key.
* `hb_tijd` is required gemaakt omdat het onderdeel is van de primary key.
* `pijn_no` is required gemaakt omdat het onderdeel is van de primary key.
* groep `ai_sdd_sod` is verwijderd omdat deze is vervallen volgens de datadictionary.
* groep `ai_sedatie` is verwijderd omdat deze is vervallen volgens de datadictionary.

## BundleOrganization
Voor de informatie die niet direct aan een opname is gerelateerd, is de BundleOrganization gemaakt. In deze bundle kan de volgende
informatie worden gestuurd:
* `kiic_bezetting`
* `zz_personeel`


## Velden aangepast naar verplicht omdat deze horen bij een primary of foreign key
actiegerichte-indicatoren: mt_bead_inst, pao2_id, ery_id, kweek_id, hb_tijd, toediening_volgnr, pijn_no, plasma_toed_tijd, spiegel_volgnr, trans_trig_tijd, trombo_uit_tijd
capaciteitsregistratie: dienst, scoredatum
complicatie: complicatie_day, dienst, kalenderdag
kiic: beadem_start
kiic-bezetting: dienst, groep
sofa: sofa_day
zz-personeel: groep, dienst
Het veld `isgevalideerd` is nu ook in ieder questionnaire verplicht gemaakt
