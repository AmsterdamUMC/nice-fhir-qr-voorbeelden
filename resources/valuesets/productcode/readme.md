| Codelijst (ZIB) | URI | OID |
|-----------------|-----|-----|
| PRK (Productcode) | http://www.gstandaard.nl/codesystem/prk | 2.16.840.1.113883.2.4.4.15.32.1.2 |
| GPK (Generieke Productcode) | http://www.gstandaard.nl/codesystem/gpk | 2.16.840.1.113883.2.4.4.15.32.1.3 |
| HPK (Handels Productcode) | http://www.gstandaard.nl/codesystem/hpk | 2.16.840.1.113883.2.4.4.15.32.1.4 |
| ATKODE (Artikelen/KNMP-nummer) | http://www.gstandaard.nl/codesystem/atk | 2.16.840.1.113883.2.4.4.8 |
| SNK (Stofnaamcode) | http://www.gstandaard.nl/codesystem/snk | 2.16.840.1.113883.2.4.4.15.32.1.5 |
| SSK (Stofnaamcode + toedieningsweg) | http://www.gstandaard.nl/codesystem/ssk | 2.16.840.1.113883.2.4.4.15.32.1.6 |
| GTIN | http://www.gs1.org/gtin | 2.16.840.1.113883.2.4.4.15.32.1.7 |
| ATC | http://www.whocc.no/atc | 2.16.840.1.113883.6.73 |
| NullFlavor | http://terminology.hl7.org/CodeSystem/v3-NullFlavor | 2.16.840.1.113883.5.1008 |

## Allowed Concepts in productcode-2026Q1

- **ATK, GPK, HPK, PRK, SNK, SSK, GTIN, ATC:**  
  All concepts from these code systems are allowed.

- **SNOMED CT:**  
  All concepts that are descendants of `373873005` ("Farmaceutisch/biologisch product") are allowed.

- **NullFlavor:**  
  Only the concept `OTH` ("other (specify)") from `http://terminology.hl7.org/CodeSystem/v3-NullFlavor` is allowed.

Refer to the ValueSet JSON for the exact technical definition.
