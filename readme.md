# NICE FHIR QR Voorbeelden

Met het NICE FHIR QR verzamelt NICE haar data op basis van FHIR R4 met behulp van Questionnaire en QuestionnaireResponses (QR). In deze git repo zetten we de voorbeelden neer.


De NICE-FHIR documentatie kan hier worden gevonden:
[https://edge.stichting-nice.nl/fhir-doc](https://edge.stichting-nice.nl/fhir-doc/voorbeelden/index.html)

# Conditonal updates en Identifiers


# Bundle-Profiles
In een bundle moet in de meta een profile worden meegestuurd. Dit wordt gebruikt om de bundle te valideren
en om deze op de juiste maneer verder te verwerken. Een bundle krijgt een nieuwe profile wanneer een of
meer entrys (o.a. de questionnaires) een nieuwe profile krijgen. De versies van de questionaires moeten 
dus overeenkomen met de definitie van de bundle.

Hieronder een tabel met daarin de bundle-profielen en de ondersteunde questionnaireResponses.
https://fhir.stichting-nice.nl/R4/StructureDefinition/<id>

|Id | Questionnaire | Questionnaire  | Questionnaire |
|---|---|---|---|
| BundleOrganization-2026Q1 | zz-personeel-2026Q1 | kiic-bezetting-2025Q3 | product-organization-2025Q3

Uitleg: Indien er een bundle wordt verstuurd met profile https://fhir.stichting-nice.nl/R4/StructureDefinition/BundleOrganization-2026Q1,
dan mag er een questionnaireResponse inzitten met een reference naar https://fhir.stichting-nice.nl/R4/Questionnaire/zz-personeel-2026Q1. 
Bijv. 

~~~diff
<Bundle xmlns="http://hl7.org/fhir">
  <meta>
+    <profile value="https://fhir.stichting-nice.nl/R4/StructureDefinition/BundleOrganization-206Q1" />
  </meta>
  <identifier>
    <system value="https://fhir.stichting-nice.nl/R4/identifier/1/1/dienst" />
    <value value="2026-08-05" />
  </identifier>
  <type value="collection" />
  <timestamp value="2026-08-05T16:08:45+02:00" />
  <entry>
    <fullUrl value="urn:uuid:ec59f6b1-6692-4ceb-be79-765e65395ded" />
    <resource>
      <QuestionnaireResponse xmlns="http://hl7.org/fhir">
        <text>
          <status value="empty" />
          <div xmlns="http://www.w3.org/1999/xhtml">Update2 - QR ten behoeve van de NICE</div>
        </text>
+        <questionnaire value="https://fhir.stichting-nice.nl/R4/Questionnaire/kiic-bezetting-2025Q3" />
        <status value="completed" />
        <item>
  ... de rest is weggelaten ...
  
~~~


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

