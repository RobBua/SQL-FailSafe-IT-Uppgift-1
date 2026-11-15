Normalisering (1NF–3NF)

1NF: Alla kolumner innehåller atomära värden, till exempel ett telefonnummer per kund och en specialitet per konsult. Det finns inga upprepade kolumngrupper (som Konsult1, Konsult2) eftersom flera konsulter hanteras som flera rader i Uppdrag. Varje tabell har en primärnyckel.

2NF: Alla tabeller har enkla surrogatnycklar (KundID, KonsultID, UppdragID och så vidare), så det finns inga partiella beroenden. Varje icke-nyckelattribut beror på hela primärnyckeln. Uppdragets egna uppgifter (datum, rollbeskrivning) ligger i Uppdrag och inte hos kund eller konsult.

3NF: Det finns inga transitiva beroenden, eftersom inga icke-nyckelattribut bestäms av andra icke-nyckelattribut. Kundens uppgifter lagras bara i Kund och konsultens bara i Konsult. Uppdrag lagrar enbart KundID och KonsultID, inte företagsnamn eller timpris. Specialiteten ligger i en egen tabell, så texten inte upprepas och inte kan stavas olika på olika rader. Organisationsnummer och personnummer är UNIQUE men är inte PK, så de kan inte ge upphov till inkonsekvens.

============================================================================================
DevSecOps-reflektion

Sec: Jag använder parametriserade frågor (prepared statements) eller en ORM, så att användarinmatning aldrig slås ihop med SQL-texten. Då tolkas inmatningen alltid som data och aldrig som kod. Dessutom ger jag applikationens databasanvändare minsta möjliga behörighet (till exempel inte DROP eller DELETE där det inte behövs) och validerar inmatningen.

Ops: Jag lägger ett index på kolumnen Organisationsnummer, och UNIQUE-villkoret ger redan ett unikt index. Då använder SQL Server en snabb index-seek (B-träd) i stället för att läsa igenom hela tabellen. På mycket stora tabeller som Uppdrag kan man även överväga partitionering.
