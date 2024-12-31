---
title: Verwenden von Datenanbietern zur Integration von Drittanbieterdaten
description: In diesem Tutorial werden Benutzende mit Datenanbietern vertraut gemacht. Erfahren Sie, wie Sie mit der Funktion „Datenanbieter“ Daten von Drittanbietern einfach an Adobe Target weitergeben können.
role: User, Developer
level: Experienced
topic: Personalization, Integrations
feature: Implementation, Integrations, APIs/SDKs
doc-type: feature video
kt: null
author: Daniel Wright
exl-id: 1892136e-14e3-4e52-8b1f-aee806d2f83a
source-git-commit: 80208b3ecbc0d627d2afe72f882e91c9800d2726
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 16%

---

# Verwenden von Datenanbietern zur Integration von Drittanbieterdaten in Adobe Target

[!UICONTROL Data Providers] ist eine Funktion, mit der Sie Daten einfach von Drittanbietern an Target weitergeben können.  Ein Drittanbieter kann ein Wetterdienst, ein DMP oder sogar Ihr eigener Web-Service sein. Anschließend können Sie diese Daten zur Erstellung von Zielgruppen und zielgerichtetem Inhalt und zur Aufwertung des Benutzerprofils verwenden.

>[!VIDEO](https://video.tv.adobe.com/v/22349/?quality=12)

## Verwendung von Datenanbietern

1. Implementierungsexperten fügen Code vor at.js (oder im Bibliothekskopfabschnitt von at.js) hinzu, der den API-Aufruf an den Drittanbieter durchführt, die Antwort analysiert und mit Name/Wert-Paaren aus der Antwort angibt, die an [!DNL Target] gesendet werden soll.
1. at.js verwaltet Flackern und schließt die Name/Wert-Paare als benutzerdefinierte Parameter in die globale Target-Anfrage ein.
1. Marketer erstellt Zielgruppen in der [!DNL Target]-Oberfläche basierend auf diesen benutzerdefinierten Parametern.
1. Der Marketing-Experte verwendet diese Zielgruppen, um Erlebnisse, Aktivitäten und Metriken anzusprechen und um Zielgruppen zu melden.

>[!NOTE]
>
>[!UICONTROL Data Providers] erfordert at.js 1.3 oder höher

## Hilfsmaterialien

* [Implementieren von Datenanbietern in at.js und Adobe Target](implement-data-providers-to-integrate-third-party-data.md)
