---
title: Wie funktioniert at.js 2.0?
description: '"at.js 2.0"verbessert die Unterstützung von Adobe Target für Einzelseitenanwendungen (SPA) und ermöglicht die Integration mit anderen Experience Cloud-Lösungen. Dieses Video und die zugehörigen Diagramme erklären, wie alles zusammenkommt.'
role: Developer
level: Intermediate
topic: SPA, Architecture, Development
feature: Implementation
doc-type: technical video
kt: null
thumbnail: null
author: Daniel Wright
translation-type: tm+mt
source-git-commit: b89732fcca0be8bffc6e580e4ae0e62df3c3655d
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 21%

---


# Funktionsweise von Adobe Target &quot;at.js 2.0&quot;

`at.js` 2.0 verbessert die Adobe Target-Unterstützung für Einzelseitenanwendungen (SPA) und ermöglicht die Integration mit anderen Experience Cloud-Lösungen. Dieses Video und die zugehörigen Diagramme erklären, wie alles zusammenkommt.

>[!VIDEO](https://video.tv.adobe.com/v/26250?quality=12)

## Architekturdiagramme

![at.js 2.0-Verhalten beim Laden der Seite](assets/pageload.png)

1. Aufruf gibt Experience Cloud-ID (ECID) zurück. Wenn der Benutzer authentifiziert ist, wird bei einem anderen Aufruf die Kunden-ID synchronisiert.

1. `at.js` Bibliothek wird synchron geladen und blendet den Textkörper des Dokuments aus (`at.js` kann auch asynchron mit einem optionalen, auf der Seite implementierten Präausblendeffekt geladen werden).

1. Die Seitenladeanforderung umfasst alle konfigurierten Parameter, ECID, SDID und Kunden-ID.

1. Profil-Skripten werden ausgeführt und in den [!UICONTROL Profil-Store] eingeordnet. Der Store fordert qualifizierte Audiencen aus der [!UICONTROL Audience-Bibliothek] an (z. B. freigegebene Audiencen von [!DNL Analytics], Audience Manager usw.). [!UICONTROL Kundenattribute ] werden an  [!UICONTROL Profil ] Store gesendet.
1. Je nach URL, Anforderungsparametern und Profil-Daten entscheidet [!DNL Target], welche Aktivitäten und Erlebnisse für die aktuelle Seite und zukünftige Ansichten an den Besucher zurückgegeben werden sollen

1. Targeting von Inhalten, die an die Seite zurückgesendet werden, einschließlich optional Profil-Werten für eine zusätzliche Personalisierung.

   Die zielgerichteten Inhalte auf der aktuellen Seite werden so schnell wie möglich bereitgestellt, ohne dass Standardinhalte aufflackern.

   Gezielte Inhalte für zukünftige Ansichten einer Einzelseitenanwendung werden im Browser zwischengespeichert, sodass sie sofort ohne zusätzlichen Serveraufruf angewendet werden können, wenn die Ansichten ausgelöst werden. (Siehe nächstes Diagramm für `triggerView()` Verhalten).

1. [!DNL Analytics] Daten, die von der Seite an die  [!UICONTROL Datenerfassungsserver gesendet ] werden
1. [!DNL Target]-Daten werden über die SDID mit -Daten abgeglichen und im [!DNL Analytics]Analytics-Berichtspeicher abgelegt. [!DNL Analytics] Daten können dann sowohl in A4T-Berichten  [!DNL Analytics] als auch  [!DNL Target] über diese angezeigt werden.

![Verhalten von at.js 2.0 bei Verwendung der Funktion &quot;triggerView()&quot;](assets/triggerview.png)

1. `adobe.target.triggerView()` in der einseitigen Anwendung aufgerufen wird
1. Gezielte Inhalte für die Ansicht werden aus dem Cache gelesen

1. Die zielgerichteten Inhalte werden so schnell wie möglich bereitgestellt, ohne dass Standardinhalte aufflackern

1. Die Benachrichtigungsanfrage wird an den [!DNL Target]-Profilspeicher gesendet, damit der Besucher in der Aktivität erfasst und die Metrik erhöht wird
1. [!DNL Analytics] Daten werden vom SPA an die  [!UICONTROL Datenerfassungsserver ] gesendet

1. [!DNL Target] Daten werden vom  [!DNL Target] Backend an die  [!UICONTROL Data ] CollectionServers gesendet. [!DNL Target]-Daten werden über die SDID mit [!DNL Analytics]-Daten abgeglichen und im [!DNL Analytics]-Berichtspeicher abgelegt. [!DNL Analytics] Daten können dann sowohl in A4T-Berichten  [!DNL Analytics] als auch  [!DNL Target] über diese angezeigt werden.

## Zusätzliche Ressourcen

* [&quot;at.js 2.0&quot;in eine Einzelseitenanwendung implementieren](implement-atjs-20-in-a-single-page-application.md)
* [Verwenden von Adobe Target Visual Experience Composer für Einzelseitenanwendungen (SPA VEC)](../experiences/use-the-visual-experience-composer-for-single-page-applications.md)
* [Funktionsweise von &quot;at.js&quot;](https://docs.adobe.com/content/help/en/target/using/implement-target/client-side/at-js/how-atjs-works.html)