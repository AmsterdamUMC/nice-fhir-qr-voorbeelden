In de NICE database staat een voorbeeld opname waarmee de fhir voorbeelden worden gegenereerd. Daarmee kan er voor elke 
release opnieuw het bericht worden gemaakt. Vervolgens kunnen we met een diff kijken welke aanpassingen nodig zijn om van 
een release naar een nieuwe release te kunnen komen. 

Let op dat bij het genereren van het voorbeeld, nieuwe UUID's worden gemaakt en dat de timestamp ook anders is. 
Maar dat dit uiteraard volgens verwachting is. De UUID's hebben vooralsng geen betekenings voor NICE maar zijn 
verplicht door de FHIR standaard. De timestamp kan worden gevuld met de huidige tijd. 

Voor de Organizational bundles zijn in 2026Q3 twee mogelijkheden:
- Profile `BundleOrganizational-2026Q3`, met een identifier met een datum. In deze bundle komen 3x de questionnaireResponses van o.a. zz_personeel, namelijk 1 voor elke dienst.
- Profile `BundleOrganizational-d-2026Q3`, met een identifier met een dienst. In deze bundle komen dezelfde questionnaireResponses. Echter nu met 1, namelijk alleen die specifieke dienst. 