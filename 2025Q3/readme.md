# 2025Q3

In de 2025Q3 hebben we de volgende aanpassingen ten aanzien van 2025Q1 gemaakt.

LET OP: Deze voorbeelden zijn nog niet definitief

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
