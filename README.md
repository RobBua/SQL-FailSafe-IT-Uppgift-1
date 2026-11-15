Normalisering (1NF-3NF)

1NF: Varje kolumn i mina tabeller innehåller bara ett värde. Till exempel har en kund ett telefonnummer och en konsult en specialitet. Om en kund hyr flera konsulter lägger jag in flera rader i tabellen Uppdrag. Jag har alltså inga listor i samma ruta. Varje tabell har också en primärnyckel.

2NF: Alla mina tabeller har en enkel primärnyckel, till exempel KundID och KonsultID, som är ett ensamt ID-nummer. Därför kan ingen kolumn bero på bara en del av nyckeln. Allt i tabellen beror på hela nyckeln. Informationen om uppdraget, som datum och roll, ligger i Uppdrag och inte hos kunden eller konsulten.

3NF: I mina tabeller beror ingen kolumn på en annan kolumn som inte är nyckel. Kundens information finns bara i Kund och konsultens bara i Konsult. I Uppdrag sparar jag bara KundID och KonsultID, så jag skriver inte företagsnamnet eller timpriset flera gånger. Specialiteten ligger i en egen tabell, Specialitet. Då skrivs namnet bara en gång och kan inte stavas på olika sätt. Därför uppfyller databasen 3NF.

============================================================================================

DevSecOps-reflektion

Sec: För att skydda mot SQL injection ska man använda parametriserade frågor (prepared statements). Då behandlas det användaren skriver som vanlig text och aldrig som SQL-kod, så en angripare kan inte radera databasen med sitt inmatningsfält.

Ops: Jag skulle lägga ett index på kolumnen Organisationsnummer. Då kan databasen hitta rätt kund direkt i stället för att leta igenom alla rader, vilket gör sökningarna snabba även när det finns tusentals kunder.
