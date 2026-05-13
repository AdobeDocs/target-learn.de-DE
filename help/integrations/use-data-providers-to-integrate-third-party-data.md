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
TQID: https://experienceleague.adobe.com/XiUlJGHSFVxAMqdl6Y7hK9PoXOgiiUI43vrFeAj2Rpo
product_v2: id: e43347a8-f2c5-4aa4-8623-6f13875d7e3a
feature_v2: id: adee20bd-51f4-461d-b9db-d215f8756eebid: c93393a4-e558-47e1-992e-c91ed4d480ceid: f7c7de77-382f-4f48-8b36-61a170f06d3d
subfeature_v2: id: fd0ff162-b6d3-4a11-8aeb-e165a01c0f0a
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: e0eb8757-182f-49f3-94a4-1587d16f5094
source-git-commit: c0b4abf2d4ead4d58a8db6e8970857b7b50dbe5c
workflow-type: tm+mt
source-wordcount: 195
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
