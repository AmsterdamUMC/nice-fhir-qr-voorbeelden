

# mds-2025Q3
`adm_hosp` vervangt de linkId `adm_date_hosp` dit vooral ivm het datatype wijziging van datum (Date) naar DateTime. Voor de datasets in access of csv geldt dat beide velden geaccepteerd worden. Maar in FHIR niet. 
Ditzelfde geldt voor `dis_hosp` welke LinkId `dis_date_hosp` vervangt.
* Item `diag_cat_weight` is verwijderd. Dit een veld om de apache II diagnose op te geven, maar het wordt niet meer gebruikt.


# mds-2025Q1
Het item isGevalideerd stond in 2024Q1 tussen de andere velden, Voor de mds is dit niet echt een probleem. Maar bijvoorbeeld de sofa wel: je zou dan voor elke dag isgevalideerd moeten aangeven. Het is voldoende om aan te geven dat de opname met alle sofa records zijn nagekeken. Vandaar dat het veld isGevalideerd 'boven' de records staan.

# mds-2024Q1 (deprecated)
Eerste opzet.