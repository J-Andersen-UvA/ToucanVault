#3dopname #pineapplepipeline
Momenteel hebben we issues op de server dat we niet altijd weten of files echt opgenomen zijn ja of nee. Deze problemen kunnen komen door de volgende punten, ik neem hier de privilege om namen te geven aan de problemen:
- **Gloss name mismatch**
	Naam komt niet overeen van een geuploade file en de daadwerkelijke gloss 
- **Send Gloss dropped**
	De file is niet goed aangekomen toen het verstuurd was over naar de websocket
- **Recording failure**
	Een opname is mislukt en we zijn verder gegaan met opnemen.

In dit document introduceren wij voor elk probleem een protocol om het te voorkomen of om achteraf af te handelen.

---
## Geen opnames in de db?

Meeste issues kunnen achteraf opgelost worden door nog een keer op te nemen. Maar hoe moeten we weten wat we nogmaals moeten opnemen als de server denkt dat iets is opgenomen, maar er nog niet is? Omdat volgende problemen unieke oplossingen kunnen hebben, is het daarbuiten nog fijn om 1 oplossing te hebben voor alle problemen tegelijkertijd. Een **catch all**.

Hieronder volgt een voorbeeld van een opname die we niet ontvangen door wat voor een reden dan ook en een catch all om het op te lossen:

#### Probleem
3dopname laat gloss zien -> opname start door actor -> actor klikt op opslaan -> om 1 van de gedefinieerde problemen is de opname niet aanwezig in de server

#### Catch all
Als de website van de actor ontvangt opslaan dan zet de website in de database voor dat specifiek glos een *timer*. Als de timer voorbij is dan zet de server de glos op terug op *niet opgenomen*. 
De timer kan in de vorm van datum, en de server kan bijvoorbeeld elke dag een script draaien waar hij kijkt of de datums al een paar dagen achterlopen. Mocht de datum overschreden zijn dan is het dus niet opgenomen.
Dus beknopt:
- **Opslaan**  
    Zodra de acteur op “opslaan” klikt, slaat de front‑end voor die gloss een uiterste verwachte datum (timer) in de database op.
- **Controle**  
    Elke dag draait een script dat alle glosses met een verlopen timer nakijkt. 
- **Status terugzetten**  
    Is de timer voorbij en is er nog geen opnamebestand? Dan zet het script de gloss automatisch terug op **“niet-opgenomen.”**
	- _(Optioneel)_ De gloss kan dan in een her-opnamelijst komen of er kan een notificatie worden gestuurd zodat duidelijk is wat opnieuw opgenomen moet worden.

### Gloss name Mismatch

### Send Gloss Dropped

### Recording Failure
