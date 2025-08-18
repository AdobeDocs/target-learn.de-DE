---
title: Implementieren von Datenanbietern zur Integration von Drittanbieterdaten
description: In diesem Tutorial finden Sie Implementierungsdetails und Beispiele für die Verwendung der Adobe Target-Funktion für Datenanbieter , um Daten von Drittanbietern abzurufen und in der Target-Anfrage zu übergeben.
role: Developer
level: Experienced
topic: Personalization, Integrations
feature: Implementation, Integrations, APIs/SDKs
doc-type: technical video
kt: null
author: Daniel Wright
exl-id: fcf6d1a8-e2a7-41ce-9c1c-02985b7afb5a
source-git-commit: 80208b3ecbc0d627d2afe72f882e91c9800d2726
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# Implementieren von [!UICONTROL Data Providers] zur Integration von Drittanbieterdaten in Adobe Target

Implementierungsdetails und Beispiele für die Verwendung der [!UICONTROL Data Providers]-Funktion von Adobe Target zum Abrufen von Daten von Drittanbietern und zum Übergeben in die Target-Anfrage.

>[!NOTE]
>
>[!UICONTROL Data Providers] erfordert `at.js` 1.3 oder höher

## Implementieren der grundlegenden Komponenten von Datenanbietern

>[!VIDEO](https://video.tv.adobe.com/v/33821/?quality=12&captions=ger)

Ein kurzer Überblick über die grundlegenden Komponenten einer `dataProvider` und wie Sie Ihren Code in der richtigen Reihenfolge anordnen können.\
Ein Anwendungsbeispiel für den im Video verwendeten Code finden Sie hier:
[https://target.enablementadobe.com/data-providers/simple.html](https://target.enablementadobe.com/data-providers/simple.html)

## Integration mit einer Drittanbieter-API

>[!VIDEO](https://video.tv.adobe.com/v/33822?captions=ger)

Ein realistischeres Beispiel für die Integration einer Wetter-API.\
Ein Anwendungsbeispiel für den im Video verwendeten Code finden Sie hier:
[https://target.enablementadobe.com/data-providers/3rdparty.html](https://target.enablementadobe.com/data-providers/3rdparty.html)

## Integration mit mehreren Anbietern

>[!VIDEO](https://video.tv.adobe.com/v/36751?captions=ger)

Integrieren von Daten mehrerer Anbieter in Ihre globale [!DNL Target].\
Ein Anwendungsbeispiel für den im Video verwendeten Code finden Sie hier:
[https://target.enablementadobe.com/data-providers/combined.html](https://target.enablementadobe.com/data-providers/combined.html)

## Auswirkungen auf das Laden der Seite minimieren

>[!VIDEO](https://video.tv.adobe.com/v/36753?captions=ger)

Minimieren Sie die Auswirkungen auf die Seitenladezeit, indem Sie Daten in einem Sitzungsspeicherobjekt speichern. Alternativ können Sie die Werte als Profilparameter mithilfe des `profile.` Präfixes übergeben und sie einfach in der ersten [!DNL Target] der Sitzung übergeben. Pro Anfrage können jedoch nur 50 Profilparameter übergeben werden.

Ein Anwendungsbeispiel für den im Video verwendeten Code finden Sie hier: [https://target.enablementadobe.com/data-providers/reducedCalls.html](https://target.enablementadobe.com/data-providers/reducedCalls.html)

## Hilfsmaterialien

* [Verwenden von Datenanbietern mit Adobe Target](use-data-providers-to-integrate-third-party-data.md)
