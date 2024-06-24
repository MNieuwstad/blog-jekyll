---
layout: post
title: Laat tests voor je werken
subtitle:
tags: [testen]
comments: false
mathjax: false
author: Max Nieuwstad
cover-img: /assets/img/20230525/5640.webp
thumbnail-img: /assets/img/20230525/5640.webp
share-img: /assets/img/20230525/5640.webp
---

### Deze blog biedt een aantal handige tips en handvatten over hoe je tests (beter) kunt laten werken in jouw project of team. Dus voor ontwikkelaars die betere tests willen schrijven, maar ook voor teams die nog effectiever willen samenwerken bij het schrijven van tests. Je hoeft deze blog niet op de letter te volgen, maar ik bied graag wat inspiratie!

*In deze blog bedoel ik met “test” een automatische test die wordt uitgevoerd om een stuk code te testen. Dit kan een unit-, integratie- of end-to-end test zijn.*

# De goede test is waardevol

Wat is nou een goede test? Bij het schrijven komen verschillende vragen naar boven. Bijvoorbeeld over het wel of niet mocken, wanneer of wat te testen en naming. Tijdens mijn zoektocht naar het schrijven van betere tests ben ik begonnen met het lezen van het boek “Unit Testing Principles, Practices, and Patterns” om antwoorden te vinden op de vragen die ik had. In het boek leert je hoe je een effectieve test schrijft. Want wanneer je een “goede” test hebt die niet een waardevol stuk code test, voegt de test geen waarde toe. Denk aan het testen van een stukje buisness logica versus het testen van een getter/setter. Het boek doet dit met pilaren voor het schrijven van een goede test. Lees hoofdstuk 1 van het boek [hier](https://livebook.manning.com/book/unit-testing/chapter-1) gratis. Deze blog is geïnspireerd door het boek en is een vervolg van mijn presentatie op de “INFI-CON 2022”.

# Betere tests schrijven als een team

Na mijn INFI-CON presentatie zei iemand: “Dat je een presentatie over testen durft te geven voor een groep developers vind ik dapper!”. Dit zegt wel iets over de softwarewereld en dus ook meningen binnen een team. Namelijk dat veel mensen een mening hebben over tests. Daar hoor ik nu ook bij… Eén van de dingen waar ik in geloof, is dat een goede en efficiënte test in elke codebase anders eruit zal zien. Dit maakt natuurlijk niets uit en zorgt altijd voor goede en leuke discussies. Daarom is het belangrijk om vooraf afspraken te maken binnen het team. Zodat de codebase een geheel blijft en de discussies in een merge request minimaal blijven.

**Afspraken**

Hoe zorg je ervoor dat jouw team tests krijgt die voor je werken? Ten eerste moet het team voldoende technische kennis hebben over het schrijven van “goede tests”. Maar vergeet niet de andere helft. Namelijk: afspraken maken binnen het team over (test)code. Zodat je samen een goede test suite kan neerzetten waardoor je uiteindelijk robuuste tests hebt en makkelijker op elkaars werk kunt voortbouwen.

Dat afspraken maken binnen een team, vooral in grijs gebied, belangrijk is heb ik geleerd uit de topsportwereld. Op deze manier kun je als team goed samenwerken, ook in stressvolle situaties. Want als er **geen** afspraken worden gemaakt wordt het pad naar een effectieve test suite een stuk zwaarder. Zelfs met al het talent in de wereld. Als je deze afspraken **wel** maakt, wordt deze wedstrijd makkelijker. Zelfs als de afspraken niet werken, kun je als team iteratief naar verbetering werken. Want deze afspraken geven ook houvast om te verbeteren. Uiteindelijk kan het team sneller die nieuwe features implementeren of bugs fixen, omdat de tests voor je werken.

Zonder al te veel in detail te treden, geef ik voorbeelden van punten waarover je afspraken kan maken binnen jouw team. Vergeet niet: ze zijn niet in steen geschreven! Zelfs het tegendeel; je wilt juist iteratief steeds betere afspraken maken. Toch is een goed startpunt geen slecht idee.

**Een goed startpunt**Om te starten met het maken van afspraken voor jouw team kan je beginnen met de volgende punten te bespreken en/of besluiten binnen het team:

- Wat is een unit(test)?
- Wanneer gebruik je een unit, integratie- of end-to-end-test?
- Hoe gaan we om met out-of-process dependencies? (Dit zijn bijvoorbeeld een file system of een database.)
- Opbouw van tests? (Naming, hiërarchie, AAA enz.)
- Anti-patterns

**Wat is een unit(test)?**Als je niet bespreekt wat een unit is heeft dat veel impact op je tests. Dit beïnvloedt vooral je unit tests, en daardoor de rest van je test suite. Want wat is een “unit” nou precies? Een stuk code of een stuk van een implementatie? Als je dat hebt besloten, hoe groot is dat stuk dan? Wanneer je bijvoorbeeld een robot moet testen en je besluit dat een unit “**een stuk code**” is, dan test je bijvoorbeeld de volgende dingen:

- Bewegen de benen
- Kan het hoofd bewegen
- Kunnen de ogen knipperen

Als je besluit dat een unit “**een stuk implementatie/gedrag**” is, dan test je de volgende dingen:

- Kan de robot lopen?
- Kan de robot ja knikken?
- Kan de robot de eend zien?

Wanneer je “een stuk code” test, zul je vaker afhankelijkheden moeten vervangen, bijvoorbeeld met mocks. Als je “een stuk gedrag” test, hoef je minder te mocken. Echter, als de test faalt, weet je niet meteen waar het in de binnenlaag fout is gegaan. In Hoofdstuk 2 gaat het boek hier dieper in. Op de voordelen en nadelen van beide gedachtengangen. Lees dit grondig door voordat je deze keuze maakt!

Als je deze keuze **niet** maakt besluit elke ontwikkelaar voor zichzelf wat “een stuk” is en geeft een eigen definitie aan een “unit”. Door duidelijke en generieke afspraken te maken over deze begrippen, wordt het verschil tussen tests van verschillende developers al een stuk kleiner. Zonder deze afspraken zal je per unit test makkelijker kunnen zien welke developer wat heeft gemaakt. Ook worden de verschillend tussen de verschillende types tests moeilijker te spotten.

**Wanneer gebruik je een unit-, integratie- of end-to-end test?**Je kunt ook bespreken welke onderdelen je wilt testen met welk type test. Als voorbeeld: welk type test gebruik je voor een controller? Dit zal al snel een integratie- of end-to-end-test zijn. Voor een mapper met minder afhankelijkheden zal dit eerder een unit-test zijn. Zorg ervoor dat je goede afspraken maakt over de onderdelen die in jouw stack voorkomen. Vergeet ook niet de sterktes van elk type test mee te nemen in de keuze. Hoe dit moet lees je [later](#) in deze blog.

Door deze afspraken kan bijvoorbeeld een nieuwe developer ook eerder een code smell herkennen. Als je hebt afgesproken om een unit-test te maken van een mapper. Wanneer de developer dan een groot aantal afhankelijkheden moet vervangen, kan dit wijzen op een code smell. De developer, met de afspraken in zijn achterhoofd, heeft zijn fout daardoor zelf sneller in de gaten. Dit komt niet meer te laat boven water bij bijvoorbeeld een code review en hoeft achteraf dus niet meer worden aangepast.

**Hoe gaan we om met out-of-process dependencies?**Het omgaan met deze dependencies hangt grotendeels af van de beslissing in wat een “unit” inhoudt. Het vervangen van deze dependencies kan op verschillende manieren. Bijvoorbeeld door gebruik te maken van een “mock class” (ook wel stub genoemd) die de implementatie nabootst. Als je dit doet, kost dit wel veel tijd als alleen die test hem gebruikt. Maar het geeft ook veel voordelen. Het aanmaken van een testcontext class kan ook, zodat je daar de services uit kunt mocken. Voor dit probleem zijn er oplossingen genoeg. Wederom is consistentie de sleutel, zodat iedereen hetzelfde doet en er geen werk dubbel word gedaan.

**Opbouw van tests (Naming, hiërarchie, AAA enz.)**

Hier worden vaak al afspraken over gemaakt, maar het is zeker niet onbelangrijk. Je kunt bijvoorbeeld de volgende punten bespreken:

- Gebruik je in elke test het Arrange, Act en Assert (AAA) patroon? Of een andere variant hierop?
- Hoe noem je de tests? Gebruiken wij een patroon?
- Hoe is de folder hiërarchie? Bijvoorbeeld:
  - End-to-end → Controllers → HondController → DoeEenStapMethodeTest
  - End-to-end → Controllers → HondControllerTest
- Afspraken over leesbaarheid, zoals:
  - Hoeveel regels de actie in de Act-regel mag zijn
  - Het gebruik van een assertion library.

**Anti-patterns**Wat willen we echt niet in onze tests? Wat willen we voorkomen in de tests en wat duidt misschien op een code smell? Deze afspraken zijn niet het allerbelangrijkst, maar misschien wel fijn om te hebben. Hieronder staan voorbeelden van test smells:

- Code aanpassen zodat het kan worden getest (bijvoorbeeld: privémethodes publiek maken)
- Gebruik van static fields in plaats van dependency injection
- Testen van interacties met subs en/of mocks
- Mocken van hele klassen
- Tests die gekoppeld zijn aan de implementatie en/of domeinlogica (dus geen [black-box](https://en.wikipedia.org/wiki/Black-box_testing#:~:text=Black-box%20testing%20is%20a,%2C%20integration%2C%20system%20and%20acceptance) tests)

# Betere tests schrijven als developer

Als developers willen we problemen oplossen, daarvoor schrijven we code. Om te controleren of de code daadwerkelijk werkt, schrijven we tests. Hierna kan je refactoren terwijl je zeker weet dat je niks kapot hebt gemaakt. Als tijdens de refactoring een test omvalt, is het lastig te achterhalen of het door actie of de test komt. Daarom wil je robuuste tests schrijven om dit probleem te voorkomen. Dit is één van de factoren die een test effectief maakt.

**Laat tests voor je werken**Om tests voor je te laten werken probeer je de juiste balans te vinden. Het boek doet dit met 4 pilaren. Deze pilaren worden eerst goed uitgelegd. Daarna worden ze gebruikt om een effectieve test te maken. Deze pilaren wil je balanceren, anders zijn de tests niet nuttig of vallen ze om. Want **als je geen balans vindt**, werken de tests tegen je en worden nieuwe features implementeren trager. Dit kan komen doordat tests continu kapot gaan. Voordat je door kan gaan moet je dit eerst repareren. Als dit vaak gebeurt, bijvoorbeeld bij het refactoren, raak je dit stukje code minder snel aan. Daardoor blijft de “tech dept” opstapelen en kom je al snel in een neerwaartse “tech dept” spiraal met alle nadelige gevolgen van dien.

**Als je de balans wel vindt** en de tests voor je laat werken, hoef je tijdens het maken van nieuwe features alleen nieuwe tests te schrijven. Refactoring en verder ontwikkelen wordt hierdoor makkelijker en sneller, want de tests vallen niet (meer) om. Dit betekent dat de groei van het project minder snel stagneert. Uiteindelijk happy stakeholders en een happy team.

**Pilaren voor een effectieve test**

Voordat je waardevolle tests kunt schrijven moet je weten waar en wanneer je de juiste pilaren moet toepassen en welke je niet kan missen. Het eerdere voorbeeld van tests die omvallen als je code aanpast is dus maar één van de vier pilaren om een effectieve test te schrijven. Laten we de pilaren kort bespreken:

1. Biedt weerstand tegen bugs
  - De hoeveelheid code die wordt gechecked
  - De geteste complexiteit
  - Connecties met externe systemen (hoeveelheid geteste samenwerking)
2. Biedt weerstand tegen het refactoren van de code
  - Om bijvoorbeeld “False negatives” tegen te gaan
3. De test heeft een lage uitvoertijd
  - Ligt aan de uitvoertijd(Hierdoor kan je een bug eerder opmerken)
4. De test is onderhoudbaar
  - Gemakkelijk te begrijpen(Grootte en leesbaarheid)
  - Gemakkelijk uit te voeren(out-of-process dependencies)

Sommige punten zijn zwart-wit, zoals “weerstand tegen refactoring”. Want een test faalt of faalt niet en kan dus niet half kapot zijn. We willen namelijk niet dat tests zomaar kapot gaan zoals in het eerdere voorbeeld. Sommige punten willen we maximaliseren, maar helaas gaat dat ten koste van andere punten. Bijvoorbeeld hoe hoger “weerstand tegen bugs” is, hoe lager de uitvoertijd zal zijn. Denk aan een end-to-end test versus een unit test.

Er zijn nog meer voorbeelden die ik later wil bespreken in een aparte blog, anders wordt deze blog te lang. Wanneer je niet kunt wachten om meer te weten te komen over deze pilaren, lees dan hoofdstuk 4 van het boek. De afbeelding hieronder laat zien hoe “bescherming tegen bugs” en “snelle feedback” per type test anders kan zijn.

![Test pilaren en type testen]({{ '/assets/img/20230525/image-5.png' | relative_url }})

**Vergeet niet wat belangrijk is**Er bestaat veel literatuur over test frameworks, mocking libraries en andere technische tools. Maar antwoord op de vraag “wat is een goede test?” wordt maar weinig gegeven. Raak niet verdwaald in de technische tools en vergeet niet om jezelf af te vragen wat een goede test is. Want als je tests telkens om vallen, zijn frameworks en mocking libraries in eens een stuk minder nuttig.

**DUS AFSPRAKEN!**Heeft jouw team afspraken over deze anti-patterns? Kun jij de vier pilaren als meetpaal toepassen? Dan zitten jij en je team op de goede weg. Vergeet niet om iteratief te blijven verbeteren op deze afspraken! Vergeet nooit meer dat testcode ook onderhoudbaar, robuust en effectief moet zijn. Dus behandel het met de zelfde liefde als de rest van de code base.

Dank voor het lezen van deze blog! – [**Max Nieuwstad**](https://maxnieuwstad.com/aboutme/)Vond je het een leuke blog? Lees een vorige blog van mij: [**“Lessons learned”**](https://maxnieuwstad.com/blogs/lessons-learned-blazor/)
