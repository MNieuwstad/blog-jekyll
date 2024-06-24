---
layout: post
title: Lessons learned na 6 blazor
subtitle:
tags: [testen]
comments: false
mathjax: false
author: Max Nieuwstad
---

# Nerdship bij Infi

Een van de dingen waar Infi trots op is Nerdship. In mijn ogen staat dat voor passie hebben voor het vak en wat je levert. Dit houd ook in dat je de beste programmeur wil worden die je kan zijn. Daarnaast is Nerdship ook grappen kunnen die thuis vaak niet worden begrepen, omdat ze te nerderig zijn. Op kantoor zijn we daar namelijk heel goed in…

Hoe word ik/jij de beste programmeur die we kunnen zijn? Door heel veel code challenges te maken/te doen? Door te presenteren? Of door een retrospective te doen? Toch kan je ook een goede programmeur worden zonder dit te doen. Wat is het dan? Als ik kijk naar mezelf en bij Infi zie ik één eigenschap vaak terugkomen. Namelijk: Het leren van je fouten.

Dit kan inderdaad door die code challenges, presentaties of retrospectives. Een blog lezen over ander mansfouten en ervaringen kan natuurlijk ook. Daarom deze blog. MAAR deze blog is niet alleen voor mijn ontwikkeling, want doordat jij deze blog leest leer je hopelijk ook een klein beetje van mijn ervaringen en fouten.

# Lessons learned

**1. Hoe ik acht uur per dag achter schermen kan zitten**Zelf heb ik wat sneller dan de gemiddelde mens last van hoofdpijn. De hele dag achter een scherm zitten/staan is dan geen pretje. Deze tips kunnen helpen tegen hoofdpijn, vierkante ogen, vermoeidheid en ga zo maar door. Ik begin met deze tips omdat ik vind dat ontwikkelaars soms te weinig aan hun gezondheid denken. Sceptisch? Begrijp ik, maar als een van deze tips een klein beetje helpt, ben ik al tevreden met deze blog. Want dat kleine beetje *keer* 47 weken *keer* 5 dagen *keer* 8 uur is ineens een hele hoop.

**De eerste tip:** Zet je “night light” aan. Een wattes? Dit is een blauwe licht filter ingebouwd in windows. [Zo](https://support.microsoft.com/en-us/windows/set-your-display-for-night-time-in-windows-18fe903a-e0a1-8326-4c68-fd23d7aaf136https://support.microsoft.com/en-us/windows/set-your-display-for-night-time-in-windows-18fe903a-e0a1-8326-4c68-fd23d7aaf136) zet je hem aan. Hierdoor hoef je niet je helderheid aan te passen, maar worden je ogen wel minder moe. In het begin is de oranje gloed even wennen, maar ik garandeer je dat je na een paar uurtjes allang bent vergeten dat je de filter aan hebt. Pas als je op werk je laptop aan zet zal je worden herinnerd met de vraag: “Wat is er met jouw scherm gebeurd?”.

![image0]({{ '/assets/img/lessonslearned/image0.png' | relative_url }})

**De tweede tip:** Gebruik een font gemaakt voor development. Deze lettertypes zijn speciaal hiervoor ontworpen en hebben dus speciale features. Lees [deze](https://medium.com/@anthonyjdella/why-you-should-use-a-developer-font-b19d5269d767) blog als je nog niet overtuigd bent. Zelf begreep ik niet toen ik geswitcht van Visual Studio naar Rider waardoor ik de code fijner vond lezen. Dit komt onder andere door het **Jetbrians Mono** lettertype die ik fijner vind lezen. Indirect heeft dit gezorgd voor minder “eye strain” en dus minder hoofdpijn. Daarom de tip: vind een development font die jij fijn vind om te lezen. Je leest namelijk veel code op een dag…

**De derde tip:** Kijk soms even uit het raam of weg van je scherm. Want als je midden in een probleem zit is het moeilijk om weg te lopen. Dan is even wegkijken een goede tweede optie. De vuistregel is vaak 20 minuten werken en dan 20 seconden naar buiten kijken. Voor meer info Google dit: “[20-20-20 rule](https://www.google.com/search?q=20-20-20)”. Er zijn ook genoeg apps om je hiermee te helpen. Zelf gebruik ik een fysieke timer om dit bij te houden. Even een blokje om lopen moet je natuurlijk ook niet vergeten. Zorg dan wel dat je niet alleen naar je voeten, maar verder kijkt! Helpt ook met tegemoetkomend verkeer trouwens.

**2. Blazor pages en components managen**Als je een Blazor project start krijg je de folders Pages en Components te zien. Op het eerste gezicht niets mis mee en je begint aan je project te werken. Maar naar mate er steeds meer domeinen bij komen begint het te lijken op:

![image1]({{ '/assets/img/lessonslearned/image1.png' | relative_url }})


Hoe meer domeinen, hoe meer je heen en weer moet klikken naar verschillende mapjes. De tip? In plaats van het gebruiken van de default mappen van components en pages kun je een map per domein aanmaken. Daarna gebruiken we de default mappen, components en pages, weer.

![image2]({{ '/assets/img/lessonslearned/image2.png' | relative_url }})

Stuk overzichtelijker vind je niet? Persoonlijk vind ik dit mooier en gemakkelijker in gebruik. Vooral als je verschillende domeinen hebt. Alles staat bij elkaar en is gemakkelijker te vinden.

We hebben veel verschillende kleine domeinen met weinig pagina’s en componenten. Als ik het project opnieuw zou doen zou ik het zoals hierboven indelen. Maar om heel eerlijk te zijn gebruiken wij dit niet. Dit komt omdat de `ctrl + p` zoekfunctie prima werkt en we eigenlijk nooit rond klikken. Het voordeel van de refactor zal niet groter zal zijn dan de tijd besteed aan het zoeken van de documenten. Mijn doel is vooral om je na te laten denken over hoe je de (Blazor) componenten en pagina’s zal indelen. Hopelijk is dat gelukt!

**3. Je code moet een goed boek zijn**In het begin probeerde ik mijn code zo leesbaar mogelijk te houden. Op een puntje na. Aan mijn test code besteedde ik namelijk iets minder tijd dan aan de rest van mijn feature. Het verbeteren hiervan was misschien 5 minuten extra werk per test. In de merge was het vaak te begrijpen met de context van het ticket. Maar na een paar sprints, was dit niet zo en moest ik even op mijn hoofd krabben wat er nou precies werd getest. Laat staan wat anderen hierover dachten.

Dit gebeurde te vaak en ik was te vaak een test aan het refactoren die al was geschreven. De oplossing? Ten eerste moet ik even veel energie stoppen in mijn test code. Want de tests worden misschien wel vaker gelezen/herschreven dan de code in onze aggregrates en controllers. Ten tweede, als ik een vraag krijg in mijn merge waaruit blijkt dat de code niet duidelijk genoeg is moet ik in plaats van die vraag beantwoorden de code opnieuw schrijven. Als ik dit niet doe dan wordt het later veel typen op Slack… Wat is de tip Max? Nou, zorg dat je code leest als een boek. Dan zit je meestal goed.

**4. Van boven naar beneden**Dit was een van de dingen die ik op school had moeten leren. De theorie wist ik. Helaas werd op school weinig naar de code gekeken. Dus kon ik de connectie met de theorie en code nog niet maken. Gelukkig heb ik nu teamgenoten bij Infi die mij hierin kunnen helpen. Mijn probleem waar ik de fout in ging: Ik wilde een pagina refactoren naar verschillende components.

*Components:*

`MeerdereFormulierenPagina → Formulier1Component → AccepteerButtonComponent`

De `AcepteerButtonComponent` had de logica om de accept waardes naar de backend te sturen. Alleen maakte ik de fout om de data die eigenlijk bij de `FormulierComponent` hoorde in de `AccepteerButtonComponent` te zetten. Waardoor een child eigenlijk moest letten op zijn (overgroot) ouders. Meestal gaat dit ook niet zo in het echte leven. Misschien had dat een kleine tip moeten zijn?

Helaas niet en ik ging stoïcijns door een donker en duister pad met allemaal callbacks en rare Blazor “truckjes”. Waar ik trouwens wel dingen van heb geleerd, zoals [too-way-binding](https://blazor-university.com/components/two-way-binding/). Na twee dagen werkte het. Terwijl het ticket 3 punten (een dag) was. Gelukkig kreeg ik in mijn merge request subtiel op mijn kop. Want de data hoorde bij de formulieren dus daar moest het ook leven. Met een simpele `Func<AcceptDto, Task>` kon de `AcceptButtonComponent` de data versturen.

Conclusie / Tip: Dingen van boven naar beneden aansturen dus parent weet van de child en niet andersom. Tuurlijk kan dit wel, er zijn genoeg algoritmes/patterns op gebaseerd. Maar in dit geval was het niet nodig en moesten er veel hacks in de code komen om het te laten werken.

# Conclusie

Na 6 maanden werken bij Infi heb ik heel veel geleerd. Sommige informatie staat wel in boeken of kreeg ik geleerd op school. Zoals het gebruiken van `Func<T>` die ik in java als `Predicate<T>`, `Consumer<T>` en `Supplier<T>` heb geleerd door dit [boek](https://www.google.com/search?q=modern+java+in+action). Trouwens een geweldig boek voor beginnende developers die wat diepere duiken willen nemen in de waarom’s en hoe’s van code schrijven. Helaas heb ik, en ik denk meer mensen, toch iemand nodig die de informatie verbindt met de praktijk of je even herinnert hoe het moet. Daarom ben ik blij met de mensen en de cultuur in het team van Infi!

Hoe nu verder?

[*errand errand erragainbut lessand lessand less*](https://maxnieuwstad.com/aboutme/)
