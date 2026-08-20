# organizational-2026Q3
Er is een alternatief profiel gemaakt waarmee elke dienst apart kan worden aangeleverd. 
* default profile `https://fhir.stichting-nice.nl/R4/StructureDefinition/BundleOrganization-2026Q3` waarmee in 1 questionnaire 3 diensten kan worden meegestuurd en heeft als identifier `https://fhir.stichting-nice.nl/R4/identifier/88/1/datum` (een datum).
* per dienst profile `https://fhir.stichting-nice.nl/R4/StructureDefinition/BundleOrganization-d-2026Q3` waarmee in 1 questionnaire 1 dienst kan worden meegestuurd. Deze heeft een aangepaste identifier  `https://fhir.stichting-nice.nl/R4/identifier/88/1/dienst`: een datum met een dienst (bijv 2024-01-28-d1 voor dienst 1, 2024-01-28-2 voor dienst 2, 2024-01-28-d3 voor dienst 3).

Een van de twee bundles moet gebruikt worden. 