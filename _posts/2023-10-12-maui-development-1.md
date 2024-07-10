---
layout: post
title: MAUI Development nr 1 - Intro en Environment Setup
subtitle:
tags: [MAUI]
comments: false
mathjax: false
author: Max Nieuwstad
---

Wil je een app maken die werkt op verschillende platforms? Heb je ervaring met .NET? Dan kan je nu die app maken met de bakken aan .NET ervaring die je hebt opgedaan! In deze blog geef ik je alle informatie die je nodig hebt om met MAUI te beginnen, zonder dat je urenlang forums of Google hoeft af te struinen.

![Test pilaren en type testen]({{ '/assets/img/mauidev1/image.png' | relative_url }})

**Je vindt in deze blog informatie over MAUI, welke versie van .NET je moet gebruiken, welke IDE het beste voor jou is en hoe je MAUI met je gekozen IDE kunt installeren.**

1. [MAUI in het kort](#maui-in-het-kort)
2. [Welke versie van .NET hoort bij MAUI?](#welke-versie-van-net-hoort-bij-maui)
3. [Rider of Visual Studio?](#rider-of-visual-studio)
4. [Visual Studio installatie](#visual-studio-installatie)
5. [Rider installatie](#rider-installatie)

# MAUI in het kort

MAUI wil het voor ontwikkelaars makkelijker maken om **native apps** te bouwen die werken op Android, iOS, macOS, Windows en Tizen. Dit kan allemaal vanuit **één** codebase. Het MAUI-team zegt dat MAUI veel waarde kan bieden, omdat het productiever zou moeten zijn dan andere al bestaande (cross platform) opties. Ze overdrijven misschien een beetje, maar het is wel een **flinke vooruitgang** op hun eerdere cross platform versie/voorganger Xamarin.

# Tweede poging

MAUI is dus de opvolger van Xamarin en daarmee de tweede poging van Microsoft om grip te krijgen op de cross-platform markt. Persoonlijk vond ik het werken met Xamarin oke, maar in 2019 had Xamarin maar weinig documentatie en het was ook nog eens moeilijk te vinden. Het bouwen verliep niet altijd soepel. Bijvoorbeeld door consistente run-time foutmeldingen in plaats van waarschuwingen vanuit de IDE of compile-time foutmeldingen. XAML als opmaaktaal vond ik ook wat minder intuïtief.

**Gelukkig biedt .NET MAUI nieuwe kansen**. Tot nu toe werkt MAUI niet slecht! De documentatie is ook beter te vinden, maar nog wel schaars. Vandaar deze blog! Omdat MAUI door werkt op het al bestaande Xamarin kan je soms hiervoor ook nog documentatie vinden. Al maakt dit het zoeken naar de juiste oplossing wel ingewikkelder. Ach ja, dat moeten we dan maar voor lief nemen… Ook zijn er nu ook meer opties voor opmaaktalen! Fijn! Wil je nu al meer weten? Deze **talk** gaat over de basics van MAUI en waarvoor je het kan gebruiken: https://youtu.be/AlwmkatOUf4

**TL;DR:** MAUI is een cross-platform framework van Microsoft dat het makkelijker maakt voor ontwikkelaars om native apps te bouwen vanuit één codebase. MAUI biedt nieuwe kansen en werkt tot nu toe goed, maar de documentatie is nog schaars.

---

# Welke versie van .NET hoort bij MAUI?

Welke versie van .NET gebruik je voor MAUI? Tot nu is de laatste grote release van .NET elke keer alleen onder support. Er is dus nog geen LTS versie van MAUI beschikbaar, en met de laatste release heb je meteen alle nieuwe features. **Als je een oude tutorial volgt, houd dit dan in je achterhoofd.** De laatste informatie kun je altijd hier vinden: https://dotnet.microsoft.com/en-us/platform/support/policy/maui#

---

# Rider of Visual Studio?

Het gebruik van MAUI in Visual Studio is goed gedocumenteerd en werkt goed. De installatie is makkelijk, waar je één vinkje aanklikt in de installer en al kan beginnen. Helaas is het nog niet zo makkelijk in Rider. Dus als je twijfelt tussen Rider of Visual Studio **raad ik Visual Studio aan**. Het is makkelijker te installeren en heeft veel meer functies die het bouwen van apps (zowel hybride als native) makkelijker en sneller maken.

In mijn geval gebruik ik Rider als dagelijkse IDE in combinatie met een hybride MAUI-app plus een webapplicatie met gedeelde pagina’s en componenten. Hierdoor hoef ik geen gebruik te maken van hot reload of XAML-preview. Vooral als je meerdere applicaties moet starten, vind ik Rider fijner werken. In Rider heb ik al mijn sneltoetsen ingesteld. In Visual Studio helaas nog niet. Ik hoef dus alleen op zijn tijd de MAUI app te bouwen en een Android- of iOS-emulator draaien in Rider. Als dit kan zonder foutmeldingen te krijgen zou dit wel fijn zijn.

**TL;DR:** Ik raad je aan om Visual Studio te gebruiken voor MAUI development. Omdat je anders veel features mist, zoals hot reload en XAML-preview. Als je, net als ik, een reden hebt om Rider te gebruiken, lees dan [hieronder](https://infi.nl/nieuws/maui-development-1-environment-setup/#riderinstall) hoe je dit kunt doen.

---

# Visual Studio installatie

Als je MAUI wilt gebruiken met Visual Studio kan je deze tutorial volgen. https://learn.microsoft.com/en-us/dotnet/maui/get-started/installation

---

# Rider installatie

Voor de installatie op MacOS bestaat er al een blog, maar die is wat ouder. Voor de windows installatie is de informatie wat verstrooid over het internet, in deze blog staat een uitgeschreven stappen plan hoe je deze installatie uitvoert.

# MacOS installatie

In plaats van de release van 2022.2 EAP kun je gewoon de nieuwste versie van Rider, non EAP, downloaden. Hetzelfde geldt voor de .NET versie zoals [hierboven](https://infi.nl/nieuws/maui-development-1-environment-setup/#versievandotnet) genoemd. Verder is de blog goed te volgen:https://blog.jetbrains.com/dotnet/2022/05/25/macos-environment-setup-for-maui-development/

# Windows installatie

Informatie voor de windows installatie was moeilijk te vinden. Hier is een samenvatting hoe ik mijn werkende omgeving heb op gezet.

# Vereisten:

- Rider (getest met 2023.2)
- De ondersteunde versie van .NET https://dotnet.microsoft.com/en-us/platform/support/policy/maui#
- Geïnstalleerd Android-emulatorapparaat
- Installatie van OpenJDK (minimaal 11)
- Android SDK (minimaal 31)

Als je één van deze onderdelen nog niet hebt, kun je altijd opzoeken hoe je het moet installeren, want dat is goed gedocumenteerd. In deze blog zal ik dit dus niet behandelen.

# Android Plugin voor Rider

Installeer de Rider Xamarin Android-ondersteuning. Dit geeft je uitvoerconfiguraties in de run window voor je android emulator [https://plugins.jetbrains.com/plugin/12056-rider-xamarin-android-support.](https://plugins.jetbrains.com/plugin/12056-rider-xamarin-android-support)

Als Rider je emulator niet kan vinden, kun je de emulator handmatig starten en het nog een keer proberen. Vergeet ook niet om even te controleren of je SDK goed is gekoppeld met Rider. Dat kan hier:

![Test pilaren en type testen]({{ '/assets/img/mauidev1/image4.png' | relative_url }})

# Installeren van Xamarin

Om MAUI te gebruiken, moeten we ook nog Xamarin Android en iOS & Mac installeren. Zorg dat je deze installeert. Je kunt op de groene knop drukken beide te installeren. Is de knop niet groen? Dan is het al geïnstalleerd. De Android SDK hebben we in de vorige stap al gekoppeld, dus dat hoeft niet meer.

![Test pilaren en type testen]({{ '/assets/img/mauidev1/image5.png' | relative_url }})

# Installeren van MAUI

Voer deze commando’s uit in PowerShell om MAUI te installeren. Herstart hierna je Rider om de MAUI-sjablonen in je Rider te zien:

dotnet workload install maui

dotnet workload install wasm-tools

# Het project maken

- Maak een nieuw project aan.
- Onder .NET staat nu “MAUI”. Klik daarop.
- Geef je project een naam.
- Selecteer het type “.NET MAUI Blazor app”. Deze template is voor een hybride app waardoor je direct je bestaande Blazor componenten kan gebruiken. De andere “.NET MAUI app” is voor een native MAUI app.
- Klik hierna op “create”!

![Test pilaren en type testen]({{ '/assets/img/mauidev1/image6.png' | relative_url }})

Run het project. Je moet nu in staat zijn om een MAUI-app te runnen op meerdere devices. Test dit ook even voordat je verder gaat!

![Test pilaren en type testen]({{ '/assets/img/mauidev1/image7.png' | relative_url }})

Je hebt nu een hybride app van Blazor + MAUI! Als je iets anders ziet dan de afbeelding hieronder, heb je waarschijnlijk een “native MAUI app”. Dit betekent dat in plaats van een webview waarin de blazor componenten zich bevinden, je een xaml-pagina hebt met MAUI-componenten.

![Test pilaren en type testen]({{ '/assets/img/mauidev1/image8.png' | relative_url }})

Nu kan je aan de slag, veel plezier!

[*err*](https://maxnieuwstad.com/aboutme/)  
[*and err*](https://maxnieuwstad.com/aboutme/)  
[*and err again,*](https://maxnieuwstad.com/aboutme/)   
[*but less*](https://maxnieuwstad.com/aboutme/)     
[*and less*](https://maxnieuwstad.com/aboutme/)     
[*and less.*](https://maxnieuwstad.com/aboutme/)
