Het Reactive Manifesto
----------------------

Om een systeem reactive te mogen noemen moet het systeem voldoen aan vier kernvoorwaarden. Het systeem moet responsive, resilient, elastic en message-driven zijn.

Reactive systemen zijn flexibeler, bestaan uit losgekoppelde componenten en zijn schaalbaar. Dit heeft als gevolg dat de systemen eenvoudiger te maken zijn. Ook kunnen deze systemen beter omgaan met veranderingen. De systemen zijn significant toleranter tegenover storingen. En op het moment dat zich een storing voordoet, zal het systeem hier elegant op reageren waardoor rampzalige fouten voorkomen worden. Reactive systemen geven de gebruikers effectieve en interactieve feedback doordat ze erg responsive zijn. 

Door message-driven te zijn wordt het mogelijk om elastic en resilient te zijn. Message driven ligt dus aan de basis van een reactive application. Om te allen tijde responsive te zijn moet een systeem elastic en resilient zijn. Op deze manier hangen de vier kernvoorwaarden samen, zie Figuur 1.

*Reactive Systemen zijn:*

* <a name="Responsive"></a>**Responsive**: Deze eis stelt dat het systeem snel reageert als dit mogelijk is. Responsiveness is de sleutel voor een gebruikersvriendelijk en nuttig systeem. Dit betekent echter ook dat problemen snel gedetecteerd  worden, en effectief afgehandeld worden door het systeem. Responsive systemen focussen zich op snelle en constante response-times, ze behouden betrouwbare upper-boundary door middel van een bounded-latency. Hierdoor leveren de services een consistente kwaliteit. Deze consistente kwaliteit vereenvoudigt foutafhandeling, vergroot het gebruikersvertrouwen en moedigt verdere interactie aan.
* <a name="Resilient"></a>**Resilient**: Resiliency houdt in dat het systeem responsive blijft op het moment dat er een storing optreedt. Dit geldt niet alleen voor highly-available, mission-critical systemen. Ieder systeem dat niet resilient is zal unresponsive zijn na een storing. Resiliency wordt bereikt door replicatie, containment, isolatie en delegatie. Storingen worden binnen het component gehouden. Door deze isolatie van de componenten kunnen delen van het systeem falen en herstellen zonder dat het systeem als geheel hier last van heeft. Het herstellen van componenten wordt gedelegeerd naar een ander (extern) component. Replicatie wordt toegepast op het moment dat het component gegarandeerd highly-available moet zijn. De gebruiker van een component wordt niet lastig gevallen met het afhandelen van de storingen. 
* <a name="Elastic"></a>**Elastic**: Met elastic wordt bedoeld dat het systeem responsive blijft onder een wisselende workload. Reactive systemen kunnen reageren op veranderingen in de invoersnelheid door meer of minder resources toe te wijzen aan het systeem. Dit impliceert dat er gebruik moet worden gemaakt van ontwerpen die geen contention points en centrale bottlenecks bevatten. Dit resulteert in de mogelijkheid om de invoer over de componenten te fragmenteren, repliceren en distribueren. Door relevante live performance metingen uit te voeren ondersteunen reactive systemen zowel voorspellende als Reactive scaling algoritmes. Ze behalen elasticity in een kosteneffectieve manier op normale hardware en software platformen.
* <a name="Message-Driven"></a>**Message Driven**: Reactive systemen vertrouwen op asynchrone message-passing om een grens te creëren tussen de componenten. Deze grens waarborgt loose coupling, isolatie, locatietransparantie en zorgt voor een manier om fouten als berichten te delegeren. Door gebruik te maken van expliciete massage-passing wordt load management, elasticity, en flow control mogelijk gemaakt. Dit gebeurt door message queues in het systeem vorm te geven en te monitoren. Ook wordt back-pressure toegepast op het moment dat dit nodig is. Berichten locatietransparant versturen maakt het mogelijk voor degene die de storingen afhandelt om met eenzelfde constructie en semantiek te communiceren binnen een cluster of een enkele host. Non-blocking communicatie staat de ontvangers in staat om alleen resources te consumeren wanneer deze actief is. Dit resulteert in een systeem met minder overhead.  
  
Grote systemen zijn samengesteld uit kleinere systemen en zijn hierdoor afhankelijk van de reactive eigenschappen van zijn componenten. Dit betekent dat reactive systems de ontwerp principes toepassen op alle niveaus. Dit maakt de systemen composable.

[Onderteken het manifest](http://www.reactivemanifesto.org/#sign-button)