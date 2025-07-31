# NICE FHIR QR Voorbeelden

Met het NICE FHIR QR verzamelt NICE haar data op basis van FHIR R4 met behulp van Questionnaire en QuestionnaireResponses (QR). In deze git repo zetten we de voorbeelden neer.


De NICE-FHIR documentatie kan hier worden gevonden:
[https://edge.stichting-nice.nl/fhir-doc](https://edge.stichting-nice.nl/fhir-doc/voorbeelden/index.html)


# FHIR-Endpoints
2025-07-31
Een FHIR endpoint is een url waar je volgens het FHIR protocol mee kan communiceren. De NICE is bezig om 
haar endpoints op ten duur te verhuizen naar een nieuwe infrastructuur. Hierdoor kan er wat verwarring 
ontstaan. De hudige productie server kan op dit moment maar een beperkt aantal resources aan, terwijl de
nieuwe server (project chiba) alle fhir resources aan kan. Dit maakt dat de nieuwe server future-proof is.
De nieuwe server bestaan al, maar kan nog niet officieel gebruikt worden voor de aanlevering van de NICE
data.

FHIR Validatie op basis van profiles is mogelijk op de nieuwe server. Dit maakt dat de nieuwe server 
beter kan controleren of de resources voldoen aan het meegestuurde profiel en of dat profiel ook door onze
server wordt geaccepteerd. Dit komt de kwaliteit van de data ten goede. Deze functionaliteit, het valideren 
op basis van de profiles, is reeds beschikbaar in een test omgeving. 

Vanaf release 2025Q3 zijn de definities voor questionnaires, valuesets, queestionnaireresponses etc en de 
voorbeelden ook op de nieuwe server getest. Dit maakt dat als de nieuwe server in productie gaat, er alleen
de endpoint hoeft te wijzigen. Het betekent ook dat bundles met oudere profielen dan 2025Q3 ***niet*** 
worden geaccepteerd op de nieuwe server.

Hieronder het overzicht van onze fhir-endpoints op dit moment:

| FHIR-endpoint | functie | validatie | Data verwerken |
|---|---|---|---|
| https://fhir.stichting-nice.nl/R4 | Huidige productie fhir endpoint | beperkt | ontvangt en verwerkt  data |
| https://beta.stichting-nice.nl/R4 | Huidige acceptatie fhir endpont | beperkt | ontvangt en verwerkt data, maar deze worden wekelijks weggegooit. Alleen voor tests te gebruiken. |
| https://fhir-edge.stichting-nice.nl/R4 | Toekomstige productie fhir endpoint | Op basis van profiles | NIET GEBRUIKEN |
| https://fhir-edge.stichting-nice.nl/beta/R4 | Toekomstige acceptatie fhir endpoint | Op basis van profiles | Kan gebruikt worden om te valideren, maar verwerkt (nog) geen data |

Wanneer de NICE volledig overgaat zullen de urls van fhir-edge vervallen dat wil zeggen: 
| was | gaat worden |
|---|---|
| https://fhir-edge.stichting-nice.nl/R4 | https://fhir.stichting-nice.nl/R4 |
| https://fhir-edge.stichting-nice.nl/beta/R4 | https://beta.stichting-nice.nl/R4 |

> De wijzigingen van de url's kunnen pas plaatsvinden als alle ziekenhuizen in nederland over zijn op tenminste
2025Q3 en op de nieuwe server aanleveren. Op dat moment kunnen we oude server stop zetten en de url's verhuizen.

# Planning

Het is onze bedoeling dit jaar (2025) de migratie te kunnen doen. Hierbij willen we rekening houden dat niet
al onze deelnemers gelijk over willen/kunnen. Daarom zal er na de migratie zowel de oude als de nieuwe nog 
even een periode naast elkaar blijven bestaan. Dit vooral om zeker te zijn dat de data aangeleverd kan blijven 
worden.

# FAQ
* Welke endpoint moet ik nu gebruiken om echte data aan te leveren: https://fhir.stichting-nice.nl/R4
* Welke endpoint kan ik gebruiken om de bundles te controlleren (valideren): 
   * Vanaf 2025Q3 : bijvoorkeur de https:/fhir-edge.stichting-nice.nl/beta/R4, dit geeft de meeste informatie of de bundles correct 
   zijn. https://beta.stichting-nice.nl kan ook gebruikt worden vooral voor het verwerken van de data. Deze laatste is dezelfde software
   als die we voor https://fhir.stichting-nice.nl/R4 gebruiken
   * ouder dan 2025Q3 : https://beta.stichting-nice.nl/R4 (de nieuwe server vindt deze bundles niet geheel volgens de FHIR regels.

