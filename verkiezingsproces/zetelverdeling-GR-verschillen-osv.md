# Verschillen in de zetelverdeling tussen OSV2020 en Abacus

differential_osv2020.rs
2 verschillen
3 plekken in de code van de fuzzer

https://github.com/kiesraad/abacus/blob/d90d075c1a23181b11774c3e54809a1a80b8b679/backend/apportionment/fuzz/fuzz_targets/differential_osv2020.rs

https://github.com/kiesraad/abacus/blob/main/backend/apportionment/fuzz/fuzz_targets/differential_osv2020.rs


## Verdeling van restzetels bij minder dan 19 zetels en toepassing van zowel P 9 als P 10

Bij een zetelverdeling voor minder dan 19 zetels worden de restzetels verdeeld over drie stappen: (1) grootste overschotten; (2) grootste gemiddelden met maximaal één restzetel per lijst; (3) grootste gemiddelden waarbij een lijst meerdere restzetels kan krijgen.

Na het verdelen van de restzetels wordt artikel P 9 toegepast: als een lijst een volstrekte meerderheid aan stemmen heeft maar niet aan zetels, dan wordt de laatste restzetel her-toegekend aan deze lijst.

Hierna wordt artikel P 10, lijstuitputting, toegepast. Van lijsten met meer zetels dan kandidaten, gaan de zetels over naar andere lijsten door voortgezette toepassing van de regels voor het toewijzen van restzetel.

Waar OSV2020 en Abacus in verschillen is hoe ze een zetel toegekend o.b.v. artikel P 9 beschouwen tijdens die voortgezette toepassing, meer specifiek de hierboven vernoemde stappen (1) en (2). In beide van die stappen kan een lijst namelijk maar één restzetel per stap toegekend krijgen. Bij stap (1) omdat dit altijd zo is bij grootste overschotten. Bij stap (2) door de expliciet toegevoegde conditie.

OSV2020 beschouwt de zetel toegekend o.b.v. artikel P 9 als een toegekende restzetel. Als na lijstuitputting verder wordt gegaan met stap (1) of stap (2) komt bij OSV2020 de lijst met die P 9-zetel niet in aanmerking voor een restzetel in die stap.

Abacus beschouwt de zetel toegekend o.b.v. artikel P 9 niet als vallende onder die beperking van maximaal één toegekende restzetel per lijst.

Zowel het behalen van een volstrekte meerderheid (laat staan: een volstrekte meerderheid van stemmen, maar niet van zetels) als lijstuitputting zijn uiterst zeldzaam.

Abacus toont een melding om contact op te nemen met de Kiesraad in dit geval.



=> OSV considers a P 9 seat assignment as part of the "max one seat" condition, Abacus doesn't #3219

// Skip cases where there are fewer than 19 seats and both art. P 9 (absolute majority) and art. P 10 (list exhaustion) are applied.
// Reason is that Abacus does not include the P 9-seat for the max. one seat requirement when assiging residual seats.
// related issue: #3219

OSV considers a P 9 seat assignment as part of the "max one seat" condition, Abacus doesn't #3219

## Toewijzing restzetels na lijstuitputting

geen verschil in uitkomst, alleen in hoe je er komt

=> OSV includes exhausted lists when assigning remaining seats #3214


// OSV2020 can require a drawing lots (P 7) for a residual seat while
// Abacus assigns it directly.
//
// This is because OSV2020 does not enforce list exhaustion (P 10) during
// its residual seat assignment, it only retracts seats after assigning.
// Abacus will not assign a residual seat to a list that is already
// exhausted, so it never sees the same drawing lots.
//
// Related issues: #3214, #3219

OSV considers a P 9 seat assignment as part of the "max one seat" condition, Abacus doesn't #3219
OSV includes exhausted lists when assigning remaining seats #3214

## Toewijzing restzetels na lijstuitputting bij gelijk gemiddelde?
=> zelfde als hierboven, want gaat over wanneer toepassen lijstuitputting

// OSV2020 assigns residual seats to exhausted lists via drawing of lots,
// so accept if Abacus also applied list exhaustion.
//
// Related issues: #3214, #3367

OSV includes exhausted lists when assigning remaining seats #3214
OSV always draws lots for equal highest averages after exhaustion, Abacus does not #3367

> During highest averages residual seat assignment when multiple lists have the same highest average, Abacus assigns the seats without drawing lots when there are enough remaining seats. However OSV2020 draws lots.

> I think this happens only after list exhaustion. OSV2020 then only assigns one seat at a time, so there is a lot draw for a single seat and only after that draw is resolved will OSV2020 free another seat from an exhausted list and reassign it.

> I don't think this is true. Based on OSV2020 output from the fuzzer it looks like OSV2020 only applies list exhaustion after assigning all seats, even after a previous list exhaustion.