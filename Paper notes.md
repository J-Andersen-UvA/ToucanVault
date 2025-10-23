
HaMeR als markerless system voor motion capture?
Is het beter dan freemocap bijv?
Kunnen we de focus leggen op alleen de handen en het dan combineren met markerbased system? - Alleen is hier de meerwaarde moeilijk van in te ze zien. Niet veel mensen hebben markerbased systemen die ze willen aanvullen met markerless systemen lijkt mij.


MANO heeft full body capture, we zouden dat kunnen vergelijken met Mediapipe omdat die op een andere methode animaties vergaart. MANO houdt rekening met hoe iemand eruit ziet, dus ik vraag mij ook af hoeveel retargeting dat in de weg zit.


LLM -> NGT
Al papers. Methodologie is hetzelfde in andere talen.
Kost te veel tijd om het te evalueren. Daarnaast moeten we veel werk steken in de andere papers voortbouwen, niet zelf vanaf scratch.
Het is wel een mooi project, toegevoegde waarde is dat animaties er al zijn van hoge kwaliteit wat we zouden kunnen toepassen.

Context verplaatsen van gebarentaal is niet altijd genoeg.
Er moet echt een andere methodologie zijn.

Focus moet liggen op data verbeteren (+methodologie).
Is onderdeel van ons project, maar _nog_ niet een nieuwe paper. Als er in onze development iets nieuws uitkomt dan wel.


- Post-processing pipeline is misschien meer interesant voor een paper.
LREC workshop voor gebarentaal zouden we dat kunnen toepassen.
Is er nog geld voor LREC?

Dataset paper zininngt en healthholland moet nog komen. Met dat in het achterhoofd willen we misschien post processing paper hebben?

prio is niet post processing paper, maar dat de dataset afkomt.

Bang voor dataset die heeft echt prio, als dat goed gaat dan zouden we meer papers kunnen doen.


MANO idee, student aan laten werken zou kunnen.

extra persoon regelen voor dataset vergaren.


post processing pipeline is meest geschikt voor LREC, mits het voor iedereen bruikbaar is.


Belangrijkste punt uit het gesprek is dat de focus moet liggen op de dataset. Daar gaan we een paper over maken, maar dat kan alleen als we alle data hebben en ook ge-post-processed. Floris is, net als wij, nerveus dat die dataset niet afkomt. Daarom zegt hij dat dat prioriteit heeft.

Over de papers specifiek:
**1) LLM -> NGT + animaties paper** werkt niet echt als een paper vanwege de volgende redenen:
- De LLM route is aan onze kant vanaf scratch gebouwd terwijl daar al binnen andere gebarentalen papers over geschreven zijn. Die papers hebben al meer werk hierin gestoken dus dat zouden we dan over moeten nemen.
- Het verplaatsen van de context van een andere gebarentaal naar NGT is niet genoeg binnen dit veld om het een goede paper te maken (dit wist ik ook niet, maar daarom goed om het met Floris over te hebben). Wat wel waardevol zou zijn is als de methodologie verbeterd zou worden.
- Het kost teveel tijd om te evalueren.
Hij heeft wel gezegd dat het project zelf mooi is. Onder andere is de toegevoegde waarde dat animaties er al zijn van hoge kwaliteit wat we zouden kunnen toepassen. Maar het kost te veel tijd. De focus moet echt op de dataset liggen nu.

**2) MANO/HaMeR retarget naar animaties paper** is een interessant idee. Het heeft echter niet met onze dataset op dit moment te maken. Wellicht voor later? En we zouden bijvoorbeeld kunnen beginnen met een student erop zetten.

**3) Midi controller post-processing paper**, dit heeft direct met onze dataset te maken daarom heeft dit de hoogste kans. Er is alleen 1 grote caveat (waar ik mij ook bij aansluit): het moet bruikbaar zijn voor andere labs.
Wat ik denk dat dat inhoudt is dat de tool voor andere avatars en andere animaties bruikbaar moet zijn, maar ook voor andere midi controllers. Dat laatste ben ik momenteel al aan het oplossen in Unreal Engine. Dat het voor andere avatars moet kunnen is het lastigste, omdat je dan een nieuwe rig moet bouwen. Wellicht is de rig die ik nu heb te vertalen naar alle skeletons die dezelfde structuur hebben, maar dat weet ik nog niet.

Het werd mij tijdens het gesprek heel duidelijk dat Floris liever heeft dat we ons focussen op de dataset en dat er weinig ruimte is voor nieuwe papers op dit moment. Alleen als we meer zekerheid hebben over de dataset, dan zouden we opnieuw kunnen overwegen de post-processing paper te kunnen doen. Hij heeft liever dat we de MANO/HaMeR paper naar voren schuiven. En hij maakte ook duidelijk dat ik aangenomen ben voor het maken van de dataset, en niet voor het produceren van papers.

Ik ben gematigd positief over de post processing paper, maar dat kan dus alleen als we meer zekerheid hebben over de dataset.
Daarnaast denk ik ook dat een student zou kunnen beginnen met MANO/HaMeR, maar dat wordt dan pas aan het eind van het studiejaar. De thesis submission period voor de studenten die halverwege het jaar willen afstuderen is al voorbij helaas.
En ik denk ook dat als we het mooie project willen uitbreiden van LLM -> NGT dat we daar een student op zouden kunnen zetten. Maar dan moeten we met concrete ideeën komen om het te verbeteren.