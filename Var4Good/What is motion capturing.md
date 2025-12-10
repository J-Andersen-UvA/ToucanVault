#MotionCapture #var4good 
- What is motion capturing?
- Why motion capture?
- How does motion capturing markers work?
	- Active - versus passivetracking, marker versus markerless
	- Retro-Reflective markers (show marker, show flash, explain infrared)
	- Infrared cameras, no location data yet
	- Triangulation for cameras during calibration
	- Marker tracking available, but no identification yet.
- How does motion capturing humans work?
	- Labelling passive markers
	- Solving into a skeleton
	- Motion capturing a face

--- 
*Deze punten vertellen als verhaal setup*

Het <span class="blue">doel</span> is om bewegingen van het lichaam op te nemen. In mijn geval was het specifiek voor gebarentaal, daardoor lag er een extra focus op vingers en gezicht.
Motion capturing kan op meerdere <span class="blue">methodes</span>, en die hebben we grondig onderzocht. De drie methodes die we hebben bekeken binnen het visualisatielab zijn marker-based, markerless, en inertia based motion capture. <span class="green">Markers-based</span> vergt dat er meerdere cameras aanwezig zijn om bolletjes op het lichaam te tracken. Het voordeel is dat je heel dicht tot de waarheid kan zien waar deze zich begeven. Maar er is ook <span class="green">markerless</span> motion capture. Bij deze methode worden er vaak AI modellen getrained op videos van mensen om zo key features van het lichaam te krijgen. Het voordeel is dat je hier niet veel geld aan kwijt bent, je hebt alleen 1 camera nodig om dit te bereiken. Maar de modellen zijn niet perfect waardoor het niet nauw de werkelheid benaderd. Ook is vaak diepte een probleem bij het gebruik van een enkele camera. Deze twee methodes zijn optisch, er is dus een camera nodig. Een derde optie heeft geen camera nodig, namelijk <span class="green">inertia based</span> motion capturing. Met een combinatie van accelerometers, gyroscopes, en magnetometers in een pak, worden de bewegingen berekend.
In het visualisatielab hadden we getest met Vicon voor markerbased motion capture. Mediapipe, freemocap, en recentelijk sam3d voor markerless motioncapture. En we hebben geexperimenteerd met een XSens pak voor inertia based. Buiten deze methodes bestaan er nog wel meer, maar dit zijn de grootste. In het lab hebben we ook nog StretchSense handschoenen, die gebruiken stretchsensors om de bewegingen van handen te meten.

Tot nu toe blijven we nog hangen aan een markerbased systeem omdat dat het beste resultaten heeft opgeleverd, dus leer ik iedereen over ons Vicon motion capture systeem.
Het systeem bestaat uit 21 infrarood cameras, 73 passive-markers als je de vingers ook wilt opnemen, en een IPhone om je gezichtsexpresies te tracken.
Binnen markerbased motion capture systemen heb je <span class="blue">passive-</span> en <span class="blue">active markers</span>. Active markers zijn vaak gemaakt van LEDs. Deze gaan aan en uit in bepaalde patronen waardoor het systeem makkelijk kan zien welke marker welke is. Het Vicon systeem gebruikt passive markers. Hiervoor is een andere slimme truc om alsnog te kunnen berekenen welke marker welke is. Dat leg ik straks verder uit. Voor nu hoef je alleen te weten dat een passive marker gebruik maakt van een speciaal <span class="blue">retro-reflectief materiaal</span>. Dit materiaal kaatst licht af in dezelfde hoek dat het binnenkomt. De <span class="blue">infrarood cameras</span> schieten infrarood af, en omdat het retro-reflectieve materiaal het in dezelfde richting terugkaatst, krijgt de camera te weten waar markers zijn binnen hun eigen beeld. Als meerdere cameras een marker zien dan wordt de marker in de virtuele scene geplaatst.

De infrarood cameras weten echter niet gelijk af van hun eigen positie af. Hierom moeten we ze calibreren door middel van <span class="blue">triangulation</span>. Als de cameras dan weten waar ze zijn, weten ze ook samen waar de markers zijn in het beeld. 
Voordat we daar aan kunnen beginnen moeten we zorgen dat de cameras elkaar niet vergissen voor markers. Elke camera stuurt infrarood, en dat willen we niet van elkaar oppakken. Hiervoor gebruiken we een <span class="blue">mask</span> over het beeld dat we gaan opnemen. Daarna kunnen we beginnen met het localiseren van de cameras. Vicon heeft hiervoor een fase in de callibratie genaamd de "<span class="blue">wand wave</span>". Bij deze fase gebruik je een set aan actieve markers genaamd een "wand" en zwaai je die set rond in de scene. Zo pakken de cameras verschillende hoeken en locaties op van de wand. Die data wordt gebruikt om de uiteindelijke relatieve locatie en rotaties te berekenen van elke camera.
Klaar zijn we nog niet, nu weten de cameras af van elkaar, maar ze hebben geen idee waar de vloer is en welke richting omhoog wijst. Als we de wand op de grond leggen en de "<span class="blue">origin setten</span>", kan het systeem deze laatste informatie overnemen.

Nu hebben we in totaal:
- locatie en orientatie van elke camera
- locatie en orientatie van de grond
- een manier om markers te zien en te tracken in 3 dimensies

Om een <span class="blue">persoon te tracken</span> moeten we een constelatie hebben