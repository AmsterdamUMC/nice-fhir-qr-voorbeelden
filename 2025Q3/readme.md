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
de veldnamen adm_hosp_date en dis_hosp_date zijn verwarrend geworden door de wijziging dat deze velden nu ook de tijd vastleggen. Voor de IC opname en IC ontslag is deze aanpassing al gedaan voor de FHIR (adm_icu, dis_icu). Voor het ziekenhuisopname willen we adm_hosp gebruiken en dis_hosp.  

## Productie informatie
Graag willen we weten met welk productie de informatie is samengesteld en opgestuurd. In de dataset zit dit al in de exportinfo. 
Voor de informatie die met FHIR wordt verstuurd, moet dit per Bundle. Dit kan met een van de twee questionnaires:
* product-admission: bedoeld om mee te sturen met de bundle `BundleAdmission` en heeft dus ook een combinatie van hospno, icno en admno [Datadictionary](https://stichting-nice.nl/dd/#11475)
* product-organization: bedoeld om mee te sturen met de bundle 'BundleOrganization` en heeft hospno, icno en datum. [Datadictionary](https://stichting-nice.nl/dd/#11480)
In beide questionniares dit de volgende velden, welke beschreven staan in de datadictionary
* [EPD](https://stichting-nice.nl/dd/#11476)
* [Producent](https://stichting-nice.nl/dd/#11478) 
* [Product](https://stichting-nice.nl/dd/#11477)
* [Versie](https://stichting-nice.nl/dd/#11479)

## Delirium 
Een nieuwe tabel\questionnaire voor het registreren van delirium



## Verwijderen van groepen die niet meer aangeleverd hoeven worden
De groepen ai_sdd_sod en ai_sedatie zijn verwijderd uit de questionnaire actiegerichte-indicatoren omdat deze vervallen zijn volgens het datadictionary. 

## Veld aangepast naar een codesystem
Het veld: bead_modus is van een integer naar een codesystem veranderd.

## Velden aangepast naar verplicht omdat deze horen bij een primary of foreign key
actiegerichte-indicatoren: mt_bead_inst, pao2_id, ery_id, kweek_id, hb_tijd, toediening_volgnr, pijn_no, plasma_toed_tijd, spiegel_volgnr, trans_trig_tijd, trombo_uit_tijd
capaciteitsregistratie: dienst, scoredatum
complicatie: complicatie_day, dienst, kalenderdag
kiic: beadem_start
kiic-bezetting: dienst, groep
sofa: sofa_day
zz-personeel: groep, dienst
Het veld isgevalideerd is nu ook in ieder questionnaire verplicht gemaakt
