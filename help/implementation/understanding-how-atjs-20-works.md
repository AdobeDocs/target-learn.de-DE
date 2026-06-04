---
title: Wie funktioniert at.js 2.0?
description: Erfahren Sie, wie at.js 2.0 die Adobe Target-Unterstützung für Single Page Applications (SPA) erweitert und mit anderen Experience Cloud-Lösungen integriert.
role: Developer
level: Intermediate
topic: SPA, Architecture, Development
feature: Implementation
doc-type: technical video
kt: null
author: Daniel Wright
exl-id: 7f037665-88a7-469c-8df5-c82cb0f65382
TQID: https://experienceleague.adobe.com/yi78hasak-rtlhpCG4-UnewWXAwMfPZJSpw9sFzRenU
product_v2: id: e43347a8-f2c5-4aa4-8623-6f13875d7e3a
feature_v2: id: adee20bd-51f4-461d-b9db-d215f8756eebid: c93393a4-e558-47e1-992e-c91ed4d480ce
subfeature_v2: id: fd0ff162-b6d3-4a11-8aeb-e165a01c0f0a
role_v2: id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: d3cdead0-685a-4489-9250-4bb709942f66id: e0eb8757-182f-49f3-94a4-1587d16f5094
source-git-commit: c0b4abf2d4ead4d58a8db6e8970857b7b50dbe5c
workflow-type: tm+mt
source-wordcount: 412
ht-degree: 0%

---

# Funktionsweise von at.js 2.0 in Adobe Target

`at.js` 2.0 erweitert die Adobe Target-Unterstützung für Single Page Applications (SPA) und integriert diese in andere Experience Cloud-Lösungen. In diesem Video und den zugehörigen Diagrammen wird erklärt, wie alles zusammenkommt.

>[!VIDEO](https://video.tv.adobe.com/v/26250?quality=12)

## Architekturdiagramme

![Verhalten von at.js 2.0 beim Laden der Seite](assets/pageload.png)

1. Der Aufruf gibt die Experience Cloud-ID (ECID) zurück. Wenn der Benutzer authentifiziert ist, wird die Kunden-ID durch einen weiteren Aufruf synchronisiert.

1. `at.js` Bibliothek wird synchron geladen und blendet den Hauptteil des Dokuments aus (`at.js` kann auch asynchron geladen werden, wobei ein optionales pre-hiding-Snippet auf der Seite implementiert ist).

1. Seitenladeanforderung erfolgt, einschließlich aller konfigurierten Parameter, ECID, SDID und Kunden-ID.

1. Profilskripte werden ausgeführt und in den [!UICONTROL Profilspeicher“ ]. Der Store fordert qualifizierte Zielgruppen aus der [!UICONTROL Zielgruppenbibliothek] an (z. B. aus [!DNL Analytics], Audience Manager freigegebene Zielgruppen usw.). [!UICONTROL Kundenattribute] werden in einem Batch-Prozess an [!UICONTROL Profilspeicher] gesendet.
1. Basierend auf URL, Anfrageparametern und Profildaten entscheidet [!DNL Target], welche Aktivitäten und Erlebnisse für die aktuelle Seite und zukünftige Ansichten an den Besucher zurückgegeben werden sollen

1. Zielgerichteter Inhalt, der an die Seite zurückgesendet wird, optional einschließlich Profilwerten für eine zusätzliche Personalisierung.

   Zielgerichtete Inhalte auf der aktuellen Seite werden so schnell wie möglich angezeigt, ohne dass der Standardinhalt flackert.

   Zielgerichtete Inhalte für zukünftige Ansichten einer Einzelseitenanwendung werden im Browser zwischengespeichert, sodass sie sofort ohne zusätzlichen Server-Aufruf angewendet werden können, wenn die Ansichten ausgelöst werden. (Das `triggerView()` Verhalten finden Sie im nächsten Diagramm.)

1. [!DNL Analytics] von Daten, die von der Seite an die [!UICONTROL Datenerfassungs-Server] gesendet werden
1. [!DNL Target] Daten werden über die SDID mit Analytics-Daten abgeglichen und in den [!DNL Analytics]-Reporting-Speicher verarbeitet. [!DNL Analytics] Daten können dann sowohl in [!DNL Analytics] als auch [!DNL Target] über A4T-Berichte angezeigt werden.

![at.js 2.0-Verhalten, wenn die Funktion triggerView() verwendet wird](assets/triggerview.png)

1. `adobe.target.triggerView()` wird in der Einzelseitenanwendung aufgerufen
1. Zielgerichtete Inhalte für die Ansicht werden aus dem Cache gelesen

1. Zielgerichtete Inhalte werden so schnell wie möglich ohne Flimmern des Standardinhalts angezeigt

1. Eine Benachrichtigungsanfrage wird an den [!DNL Target]Profilspeicher[!UICONTROL  gesendet] um den Besucher in der Aktivitäts- und Inkrementmetrik zu zählen
1. [!DNL Analytics] Daten werden von der SPA an die [!UICONTROL Datenerfassungs“-] gesendet

1. [!DNL Target] Daten werden vom [!DNL Target]-Backend an die [!UICONTROL Datenerfassungs-Server] gesendet. [!DNL Target] Daten werden über die SDID mit [!DNL Analytics] Daten abgeglichen und in den [!DNL Analytics]-Reporting-Speicher verarbeitet. [!DNL Analytics] Daten können dann sowohl in [!DNL Analytics] als auch [!DNL Target] über A4T-Berichte angezeigt werden.

## Zusätzliche Ressourcen

* [Implementieren von at.js 2.0 in einer Einzelseitenanwendung](implement-atjs-20-in-a-single-page-application.md)
* [Verwenden des Visual Experience Composer von Adobe Target für Einzelseitenanwendungen (SPA VEC)](../experiences/use-the-visual-experience-composer-for-single-page-applications.md)
