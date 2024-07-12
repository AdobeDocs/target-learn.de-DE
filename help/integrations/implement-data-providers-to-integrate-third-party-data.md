---
title: Implementieren von Datenanbietern zur Integration von Drittanbieterdaten
description: In diesem Tutorial finden Sie Implementierungsdetails und Beispiele dazu, wie Sie mit der Adobe Target-Datenanbieter-Funktion Daten von Drittanbietern abrufen und in der Target-Anfrage übergeben können.
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

Implementierungsdetails und Beispiele zur Verwendung der Adobe Target-Funktion [!UICONTROL Data Providers] zum Abrufen von Daten von Drittanbietern und zum Übergeben dieser Daten in die Target-Anfrage.

>[!NOTE]
>
>[!UICONTROL Data Providers] erfordert `at.js` 1.3 oder höher

## Implementieren der grundlegenden Komponenten von Datenanbietern

>[!VIDEO](https://video.tv.adobe.com/v/22348/?quality=12)

Ein kurzer Überblick über die grundlegenden Komponenten eines `dataProvider` und wie Sie Ihren Code in der richtigen Reihenfolge abrufen können.\
Ein Arbeitsbeispiel mit dem im Video verwendeten Code finden Sie hier:
[https://target.enablementadobe.com/data-providers/simple.html](https://target.enablementadobe.com/data-providers/simple.html)

## Integration mit einer Drittanbieter-API

>[!VIDEO](https://video.tv.adobe.com/v/22345/)

Ein realistischeres Beispiel: die Integration einer Wetter-API.\
Ein Arbeitsbeispiel mit dem im Video verwendeten Code finden Sie hier:
[https://target.enablementadobe.com/data-providers/3rdparty.html](https://target.enablementadobe.com/data-providers/3rdparty.html)

## Integration mit mehreren Anbietern

>[!VIDEO](https://video.tv.adobe.com/v/22346/)

So integrieren Sie Daten von mehreren Anbietern in Ihre globale [!DNL Target] -Anfrage.\
Ein Arbeitsbeispiel mit dem im Video verwendeten Code finden Sie hier:
[https://target.enablementadobe.com/data-providers/combined.html](https://target.enablementadobe.com/data-providers/combined.html)

## Minimieren der Seitenladeauswirkungen

>[!VIDEO](https://video.tv.adobe.com/v/22347/)

Minimieren Sie die Auswirkungen auf die Seitenladezeit, indem Sie Daten in einem Sitzungsspeicherobjekt speichern. Alternativ können Sie die Werte mithilfe des Präfixes `profile.` als Profilparameter übergeben und in der ersten [!DNL Target] -Anfrage der Sitzung übergeben. Sie sind jedoch auf die Übergabe von fünfzig Profilparametern pro Anfrage beschränkt.

Ein Arbeitsbeispiel mit dem im Video verwendeten Code finden Sie hier: [https://target.enablementadobe.com/data-providers/reducedCalls.html](https://target.enablementadobe.com/data-providers/reducedCalls.html)

## Unterstützende Materialien

* [Verwenden von Datenanbietern mit Adobe Target](use-data-providers-to-integrate-third-party-data.md)
