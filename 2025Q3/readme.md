# 2025Q3

In de 2025Q3 hebben we de volgende aanpassingen ten aanzien van 2025Q1 gemaakt.

LET OP: Deze voorbeelden zijn nog niet definitief

## Ziekenhuisopname en ziekenhuis ontslag
de veldnamen adm_hosp_date en dis_hosp_date zijn verwarrend geworden door de wijziging dat deze velden nu ook de tijd vastleggen. Voor de IC opname en IC ontslag is deze aanpassing al gedaan voor de FHIR (adm_icu, dis_icu). Voor het ziekenhuisopname willen we adm_hosp gebruiken en dis_hosp.  

## Productie informatie
Graag willen we weten met welk productie de informatie is samengesteld en opgestuurd. In de dataset zit dit al in de exportinfo. Hier willen we het ook opnemen in de FHIR aanlevering. 
* Producent (Chipsoft, Itemedical, EPIC, Philips, etc)
* Product
* Versie

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
