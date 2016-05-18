# Reactive Manifesto woordenlijst

## Asynchronous (Asynchroon)
Het verwerken van een opdracht op een willekeurig moment in de tijd, soms nadat de opdracht verstuurd is vanaf de client naar service. De client kan niet direct de uitvoering van de opdracht op service observeren of hier mee synchroniseren. 
Dit is het tegenovergestelde van synchrone uitvoering, wat impliceert dat de client pas verder gaat met het uitvoeren van zijn eigen taak, nadat de service de opdracht heeft verwerkt.

## Back-pressure (tegendruk)
Als één component in het systeem moeite heeft met het bijhouden van de snelheid, moet het gehele systeem hier op een goede manier op reageren. Het is onacceptabel als een component faalt of berichten ongecontroleerd laat vallen onder een hoge workload.
Omdat het component het niet kan bijhouden, maar ook niet mag falen, moet deze dit door communiceren naar de componenten die hem aanspreken. Om deze reden moeten de componenten de workload samen verlagen.
Back-pressure is een belangrijk feedback mechanisme dat systemen in staat stelt om goed te reageren op de werkdruk en hierdoor niet in te storten. Deze back-pressure kan terug stromen richten de gebruiker. Op dit punt zal de responsiveness degraderen, maar dit garandeert wel dat het systeem resilient is onder de workload en informatie zal geven waardoor het systeem zichzelf meer resources kan toevoegen om de workload te distribueren.

## Bounded-latency (begrensde wachttijd)
Om te herkennen wanneer een request gefaald is, hebben we bounded-latency nodig. Dit houdt in dat er een harde tijdsgrens moet worden geformuleerd waarbinnen een request afgehandeld moet zijn. Als een request er langer over doet, zal dit resulteren in een fout.
Het bepalen van de tijdsgrens kan gedaan worden met behulp van metingen. Zo kan ervoor gekozen worden om een request automatisch te laten resulteren in een fout als deze er langer over doet dan 99% van requesten (bron).

## Component
Het Reactive Manifesto beschrijft een modulaire software architectuur. Dit is een heel oud idee (Parnas, 1972). De term ‘component’ wordt gebruikt omdat het impliceert dat ieder component self-containt, encapsulated en geïsoleerd is van andere componenten.
Deze gedachte wordt vooral toepast op de runtime, maar zal normaalgesproken ook terug te zien zijn in de source code. Verschillende componenten kunnen gebruik maken van dezelfde software modules voor herhalende taken. Echter zal de programma code die een component vormt ook zelf een losse module zijn.
De component boundaries komen vaak overeen met de bounded contexts (Fowler, 2012) van het domein. Dit betekend dat het systeem ernaar neigt om het domein te reflecteren. Hierdoor zijn de componenten makkelijk te evalueren, terwijl ze de isolation behouden.
Message protocols verzorgen een natuurlijke brug en communicatie laag tussen de components (Boner et al., 2013).

## Elasticity (elasticiteit)
Elasticity (in contrast met scalability) betekend dat de throughut van een systeem automatisch verhoogd of verlaagd wordt om de vraag aan te kunnen op het moment dat resources evenredig worden toegevoegd of verwijderd. Het systeem moet scalable zijn zodat het gebruik kan maken van de dynamische toevoeging en verwijdering van resources op runtime. 
Elasticity bouwt om deze reden voort op scalability en bereidt het uit door automatische resource management toe te voegen (Boner et al., 2013).

## Failure (storing)
Een failure is een onverwachte gebeurtenis in een component, waardoor deze niet meer verder kan functioneren. Meestal kan het component hierdoor niet meer reageren op het request en mogelijk alle opvolgende requests.
In tegenstelling tot een error is het bestaan van deze gebeurtenis niet van te voren bedacht. Er is een ingrijp nodig voordat het component verder kan functioneren.
Dit betekend niet dat een storing altijd fataal is. Het is wel zo dat de capaciteit van het systeem beïnvloed wordt (Boner et al., 2013).

## Isolation (isolatie)
Isolatie van systemen is het loskoppelen van zowel tijd als locatie tussen de systemen. 
Loskoppelen van de tijd houdt in dat de zender en ontvanger onafhankelijke life-cycles kunnen hebben. Dit gebeurt door asynchrone grenzen tussen de componenten te bouwen, communicatie verloopt via message-passing.
Loskoppelen van de locatie (location transparency) betekend dat de zender en ontvanger niet altijd in het zelfde proces leven. De runtime bepaald wat het best is voor het component op dat moment (Boner et al., 2013).

## Location-transparency (locatietransparantie)
Om scalibility te realiseren is het belangrijk om te beseffen dat we altijd distributed computing toepassen. Het maakt hierbij niet uit of het systeem op een enkele node of op een cluster van nodes draait. Als we ons dit realiseren zit er geen verschil meer in tussen horizontaal en verticaal schalen (Boner et al., 2013).

## Replication (replicatie)
Replication is het simultaan uitvoeren een eenzelfde component op verschillende locaties. Hierbij kan een locatie een verschillende thread, thread pool, proces, netwerk node of computer centrum zijn.
Replication zorgt ervoor dat een systeem schaalbaar is. Binnenkomende workload wordt verdeelt over verschillende instanties van het component. Ook zorgt replication voor resiliency. Binnenkomende workload wordt gedupliceert over verschillende instanties die het request parallel verwerken.
Deze twee aanpakken kunnen samen gebruikt worden. Bijvoorbeeld door ervoor te zorgen dat alle request worden uitgevoerd door tenminste twee instanties terwijl de totale hoeveelheid instanties mee schaalt met de binnenkomende workload (Boner et al., 2013).

## Resources
Alles waarop een component leunt om zijn taak uit te voeren is een resource. Al deze resources moeten worden geprovisioneerd in overeenstemming met de vraag van het component.
Denk hierbij aan CPU, geheugen ,opslag capaciteit, netwerk bandbreedte, CPU caches, internet sockets, timers, task schedulers en andere input en output systemen zoals database en network file systems.
Er moet rekening worden gehouden met de elasticity en resiliency van al deze resources. Als een resources niet beschikbaar is zal het component namelijk niet goed functioneren op het moment dat dit nodig is (Boner et al., 2013).

## Scalability (schaalbaarheid)
De mogelijkheid van een systeem om meer resources te gebruiken om de performance te verhogen. De schaalbaarheid wordt gemeten met de ratio tussen de throughput winst en het aantal toegevoegde resources. Een perfect schaalbaar systeem is herkenbaar aan het feit dat beide nummers evenredig zijn.
Scalability wordt typisch gelimiteerd door bottlenecks en synchronisatie punten binnen het systeem. Hierdoor wordt de scalability verminderd.

## System (systeem)
Een systeem biedt services aan zijn gebruikers. Een systeem kan opgebouwd zijn uit losse componenten. Al deze componenten werken samen om de taken uit te voeren.
Een systeem deelt eenzelfde resiliency model. Dit betekend dat fouten binnen het systeem afgehandeld worden. Deze afhandeling wordt gedelegeerd tussen de componenten
