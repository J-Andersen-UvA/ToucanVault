#3dopname #pineapplepipeline


# 08-10-2025

*Notities na het overleg:*
We hebben besproken wat verder gedaan moet worden qua gloss safety. Gomer en ik praten elkaar voorbij, maar we bedoelen uiteindelijk wel hetzelfde. We willen weten waar de verantwoordelijkheden liggen qua lokaal en server. In mijn ogen is het log bestand (waar de  opnames die lokaal aanwezig zijn in staan) de hoofdverantwoordelijkheid van lokaal. Alle files worden al verstuurd naar de server direct na opnames, maar er zijn situaties waar "drops" voorkomen ookal is er een ack naar lokaal gestuurd. Daarom vraag ik mij af, wat aan de kant van de server er in die gevallen moet gebeuren? Gaat de server checken of de bestanden in het log bestand ook aanwezig zijn op de server? Wat als er 1 file mist? Gaan we dan automatisch vragen aan de Vicon computer of hij het weer op kan sturen? Of gaan we voor die opnames het weer op "niet opgenmomen" zetten voor de missende files ookal zijn de opnames lokaal wel aanwezig? Of willen we bijvoorbeeld, wanneer het log bestand kompleet gevuld wordt (inclusief shogun post), het hele pakket met opnames nogmaals naar de server sturen? Zijn we dan bang voor dubbele files of opslag?
Voor de rest is het wat mij betreft aan de kant van lokaal afgebakend, ik probeer alleen te kijken hoe we hiermee verder willen.

*Chatgpt versie:*
**Situatie:**  
Lokaal wordt na elke opname een logbestand bijgehouden van wat er is opgenomen. Alle bestanden worden direct doorgestuurd naar de server, maar er zijn situaties waarin de server wel een ACK terugstuurt terwijl er uiteindelijk één of meer bestanden ontbreken (“drops”).

**Vraagstuk:**  
Wat is in die gevallen de verantwoordelijkheid van de server?

- Moet de server checken of de bestanden in het logbestand ook daadwerkelijk aanwezig zijn?
- En als er iets mist:
    - Probeert de server de file opnieuw op te vragen bij de Vicon-computer?
    - Of zet de server die opname op “niet opgenomen” ondanks dat lokaal alles er wel is?
- Of kiezen we ervoor dat lokaal, zodra het log compleet is (inclusief Shogun Post), het hele pakket nogmaals naar de server stuurt als een back-up?
    - In dat geval: hoe gaan we om met dubbele bestanden en opslag?

**Mijn standpunt:**  
Aan de lokale kant is het proces al goed afgebakend. De open vraag is vooral:

> Hoe willen we aan de serverkant omgaan met de validatie en eventuele herstelactie bij ontbrekende bestanden?

# 29-09-2025

Idpv één json file met alle opname paden en statusen, kiezen we ervoor om alles lokaal in een enkele folder op te slaan. Die folder ziet er als volgt uit:
```
root folder (datum)
└── subfolder (glossname of ID)
     ├── metadata
	 |    └── status file (overzicht van alle aanwezige bestanden)
     ├── shogun_live
     |    ├── mcp        
     |    └── flir   
     ├── shogun_post
     |    ├── fbx      
     |    └── csv     
     ├── unreal     
	 |    ├── retargeted fbx     
	 |    └── live link face csv
	 └── obs          
		 ├── camera_hoek1.mkv
		 ├── camera_hoek2.mkv
		 └── ...
```
Op die manier weten we gelijk wat er bij een bepaalde gloss hoort omdat het in dezelfde folder zit. Daarnaast kunnen we de metadata file ook sturen naar de server zodat die weet of namen anders zijn geworden bij een gloss. Lastly, kunnen we ook dit soort folders makkelijker zippen en sturen. Moet er achteraf nog iets opnieuw opgestuurd worden, dan kan dat als kompleet pakket.

# 25-07-2025

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

Hieronder volgt een voorbeeld van een opname die we niet ontvangen door wat voor reden dan ook en een catch all om het op te lossen:

#### Probleem
3dopname laat gloss zien -> opname start door actor -> actor klikt op opslaan -> om 1 van de gedefinieerde problemen is de opname niet aanwezig in de server

#### Catch all
Als de website van de actor het commando ontvangt **opslaan** dan zet de website in de database voor dat specifiek glos een *timer*. Als de timer voorbij is dan zet de server de glos op terug op *niet opgenomen*. 
De timer kan in de vorm van datum, en de server kan bijvoorbeeld elke dag een script draaien waar hij kijkt of de datums al een paar dagen achterlopen. Mocht de datum overschreden zijn dan is het dus niet opgenomen.
Dus beknopt:
- **Opslaan**  
    Zodra de acteur op “opslaan” klikt, slaat de website voor die gloss een uiterste verwachte datum (timer) in de database op.
- **Controle**  
    Elke dag draait een script dat alle glosses met een verlopen timer nakijkt. 
- **Status terugzetten**  
    Is de timer voorbij en is er nog geen opnamebestand? Dan zet het script de gloss automatisch terug op **“niet-opgenomen.”**
	- _(Optioneel)_ De gloss kan dan in een her-opnamelijst komen of er kan een notificatie worden gestuurd zodat duidelijk is wat opnieuw opgenomen moet worden.

---
## Specifieke problemen
Hieronder volgen specifieke problemen en hoe we die moeten oplossen.
### Gloss name Mismatch
**Probleem**
*De naam van het geuploade bestand komt niet overeen met de naam in de database.*

**Oplossing**
De oplossing is tweevoudig.
1. Aan de kant van de website moet de naam zonder speciale karakters en geen hoofdletters in de database staan (alleen alfabet en underscores).
2. Aan de lokale kant moet elk opname software de naam letterlijk overnemen zoals die door de website wordt doorgegeven. Op die manier komt de naam altijd overeen.
Het is belangrijk om te noteren dat de iPhone graag extra karakters append aan het einde van de opname naam. Dit valt aan de kant van de server op te lossen door te kijken of de naam in de database binnen de naam van de binnenkomende files staan.

**Fail-safe**
Wanneer de server een bestand ontvangt dat niet met een gloss in de database kan worden gekoppeld, registreren we de bestandsnaam om te onderzoeken wat er is misgegaan. Zo hebben we een compleet overzicht van alle uploads—zowel de correct in de database opgenomen bestanden als de niet-gematchte—en weten we in ieder geval dat de opname daadwerkelijk heeft plaatsgevonden.
### Send Gloss Dropped
**Probleem**
*De gloss is verstuurd lokaal naar de server, maar wordt gedropped door wat voor reden dan ook*

**Oplossing**
Naast het **catch‑all**-mechanisme houden we lokaal via de ACK‑berichten bij of een bestand correct is aangekomen. Hiervoor:
- **Overzicht mislukte verzendpogingen**  
    Lokaal bewaren van een lijst van alle ‘failed sends’.
- **Dagelijkse retry**  
    Aan het einde van elke dag worden alle ontbrekende bestanden automatisch opnieuw verzonden.
Het is belangrijk om aan te geven dat het volgende al in plaats zit lokaal:
- **Live feedback in de GUI**  
    In de nieuwe PineapplePipeline‑interface zie je via de _health checks_ direct of er tijdens een opname iets mis is gegaan. 
- **On‑the‑spot heropname**  
    Zodra de operator een fout ziet, kan hij of zij direct vanuit de GUI een nieuwe opname starten.
### Recording Failure
**Probleem**
*De opname is fout gegaan en de actor gaat door naar de volgende gloss*

**Oplossing**
- **Directe feedback**  
    Bij uitblijven van bestand of ACK verschijnt er meteen een foutmelding in de website door een pop-up en pauzeert de workflow.
- **Actie**  
    De actor krijgt twee keuzemogelijkheden:
    1. **Opnieuw opnemen**
    2. **Overslaan en toevoegen aan retry‑lijst**
