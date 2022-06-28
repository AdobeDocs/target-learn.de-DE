---
title: Abrufen von Recommendations mit der Bereitstellungs-API
description: Dieser Teil des Tutorials führt Entwickler durch die Schritte, die zum Abrufen von Empfehlungsinhalten mit der Adobe Target-Bereitstellungs-API erforderlich sind.
role: Developer
level: Intermediate
topic: Personalization, Administration, Integrations, Development
feature: APIs/SDKs, Recommendations, Administration & Configuration
doc-type: tutorial
kt: 3815
author: Judy Kim
exl-id: 553d1208-647f-479d-acc7-d7760469d642
source-git-commit: cee2618bb92284da1f82d108a0aff0d39340a15b
workflow-type: tm+mt
source-wordcount: '1468'
ht-degree: 1%

---

# Abrufen [!DNL Recommendations] mit der Bereitstellungs-API

Die Adobe Target und Adobe Target [!DNL Recommendations] APIs können verwendet werden, um Antworten auf Web-Seiten bereitzustellen, können aber auch für nicht-HTML-basierte Erlebnisse wie Apps, Bildschirme, Konsolen, E-Mails, Kiosks und andere Anzeigegeräte verwendet werden. Mit anderen Worten, wenn [!DNL Target] -Bibliotheken und JavaScript nicht verwendet werden können, wird die **[!DNL Target]Bereitstellungs-API** ermöglicht uns weiterhin den Zugriff auf die gesamte Bandbreite von [!DNL Target] Funktionen zur Bereitstellung personalisierter Erlebnisse.

>[!NOTE]
>
> Verwenden Sie bei der Anforderung von Inhalten, die tatsächliche Empfehlungen enthalten (empfohlene Produkte oder Artikel), die [!DNL Target] Bereitstellungs-API.

Um Empfehlungen abzurufen, senden Sie einen Adobe Target Delivery API-Aufruf mit den entsprechenden Kontextinformationen, der eine Benutzer-ID (zur Verwendung mit profilspezifischen POST wie den kürzlich angezeigten Artikeln des Benutzers), einen relevanten Mbox-Namen, Mbox-Parameter, Profilparametern oder anderen Attributen enthalten kann. Die Antwort enthält empfohlene entity.ids (und kann andere Entitätsdaten enthalten) im JSON- oder HTML-Format, das dann auf dem Gerät angezeigt werden kann.

Die [Bereitstellungs-API](https://developer.adobe.com/target/implement/delivery-api/){target=&quot;_blank&quot;} für Adobe Target alle vorhandenen Funktionen verfügbar macht, die eine [!DNL Target] -Anfrage bereitstellt.

>[!NOTE]
>Die Bereitstellungs-API:
>* Ermöglicht es Ihnen, Erlebnisse oder Angebote für einen Ort und eine Zielgruppe in RESTful-Weise abzurufen.
>* Keine Authentifizierung erforderlich.
>* Nur POSTs.
>* Verarbeitet keine Cookies oder Umleitungsaufrufe.
>* erfordert keine Benutzerrollen oder erkennt sie nicht. Ruft einfach Inhalte ab oder meldet Ereignisse zu [!DNL Target] Edge-Server.


So verwenden Sie die Bereitstellungs-API zur Bereitstellung [!DNL Target] Erlebnisse - einschließlich Empfehlungen - führen Sie folgende Schritte aus:

1. Erstellen Sie eine [!DNL Target] Aktivität (A/B, XT, AP oder [!DNL Recommendations]) unter Verwendung des formularbasierten Composers (nicht des Visual Experience Composer).
2. Verwenden Sie die Versand-API, um eine Antwort für die von der [!DNL Target] -Aktivität erstellen.

<!-- Q: Why are BOTH steps necessary for this? If you have a Form-based recommendation defined for an mbox, what's the point/benefit of ALSO having the Delivery API step in to retrieve results? Why can't you just have the Form-based Rec deliver the results in the destination device...?? A: See use case below... it's when you want to "intercept" the pending results in order to do more stuff prior to displaying the results. Things like real-time comparisons to inventory levels. -->

## Erstellen einer Empfehlung mit dem formularbasierten Experience Composer

Um Empfehlungen zu erstellen, die mit der Bereitstellungs-API verwendet werden können, verwenden Sie die [Form-Based Composer](https://experienceleague.adobe.com/docs/target/using/experiences/form-experience-composer.html?lang=en).

1. Erstellen und speichern Sie zunächst ein JSON-basiertes Design, das in Ihrer Empfehlung verwendet werden soll. Beispiel-JSON sowie Hintergrundinformationen dazu, wie JSON-Antworten bei der Konfiguration einer formularbasierten Aktivität zurückgegeben werden können, finden Sie in der Dokumentation unter [Erstellen von Empfehlungsdesigns](https://experienceleague.adobe.com/docs/target/using/recommendations/recommendations-design/create-design.html?lang=en). In diesem Beispiel heißt das Design *Einfache JSON.*

   ![server-side-create-recs-json-design.png](assets/server-side-create-recs-json-design.png)

2. In [!DNL Target], navigieren Sie zu **[!UICONTROL Tätigkeiten] > [!UICONTROL Aktivität erstellen] > [!UICONTROL Recommendations]**, wählen Sie **[!UICONTROL Formular]**.

   ![server-side-create-recs.png](assets/server-side-create-recs.png)

3. Wählen Sie eine Eigenschaft aus und klicken Sie auf **[!UICONTROL Nächste]**.
4. Definieren Sie den Ort, an den Benutzer die Antwort der Empfehlung erhalten sollen. Im folgenden Beispiel wird ein Speicherort mit dem Namen *api_charter*. Wählen Sie Ihren zuvor erstellten JSON-basierten Entwurf mit dem Namen *Einfache JSON.*
   ![server-side-create-recs-form.png](assets/server-side-create-recs-form1.png)
5. Speichern und aktivieren Sie die Empfehlung. Sie generiert Ergebnisse. [Sobald die Ergebnisse fertig sind](https://experienceleague.adobe.com/docs/target/using/recommendations/recommendations-activity/previewing-and-launching-your-recommendations-activity.html?lang=en)können Sie sie mit der Bereitstellungs-API abrufen.

## Verwenden der Bereitstellungs-API

Die Syntax für die [Bereitstellungs-API](https://developer.adobe.com/target/implement/delivery-api/#tag/Delivery-API){target=&quot;_blank&quot;} ist:

`POST https://{{CLIENT_CODE}}.tt.omtrdc.net/rest/v1/delivery`

1. Beachten Sie, dass der Clientcode erforderlich ist. Zur Erinnerung: Ihr Clientcode kann in Adobe Target gefunden werden, indem Sie zu **[!UICONTROL Recommendations] > [!UICONTROL Einstellungen]**. Beachten Sie die **[!UICONTROL Clientcode]** Wert in **[!UICONTROL Recommendations-API-Token]** Abschnitt.
   ![client-code.png](assets/client-code.png)
1. Sobald Sie Ihren Client-Code haben, erstellen Sie Ihren Bereitstellungs-API-Aufruf. Das folgende Beispiel beginnt mit dem **[!UICONTROL API-Aufruf zur Bereitstellung Web-Batch-Mboxes]** im [Postman-Erfassung der Bereitstellungs-API](https://developers.adobetarget.com/api/delivery-api/#section/Getting-Started/Postman-Collection), indem sie entsprechende Änderungen vornehmen. Beispiel:
   * die **browser** und **Adresse** -Objekte wurden aus dem **body**, da sie für Anwendungsfälle ohne HTML nicht erforderlich sind
   * *api_charter* wird in diesem Beispiel als Ortsname aufgeführt
   * die entity.id angegeben wird, da diese Empfehlung auf der Ähnlichkeit von Inhalten basiert, für die ein aktueller Artikelschlüssel an [!DNL Target].
      ![server-side-delivery-API-call.png](assets/server-side-delivery-api-call2.png)
Konfigurieren Sie Ihre Abfrageparameter ordnungsgemäß. Stellen Sie beispielsweise sicher, dass Sie 
`{{CLIENT_CODE}}` nach Bedarf. <!--Q: In the updated call syntax, entity.id is listed as a profileParameter instead of an mboxParameter as in older versions. --> <!--Q: Old image ![server-side-create-recs-post.png](assets/server-side-create-recs-post.png) Old accompanying text: "Note this recommendation is based on Content Similar products based on the entity.id sent via mboxParameters." -->
      ![client-code3](assets/client-code3.png)
1. Senden Sie die Anfrage. Dies wird gegen die *api_charter* -Speicherort, auf dem eine aktive Empfehlung ausgeführt wird, definiert mit Ihrem JSON-Design, das eine Liste empfohlener Entitäten ausgibt.
1. Erhalten Sie eine Antwort basierend auf dem JSON-Design.
   ![server-side-create-recs-json-response2.png](assets/server-side-create-recs-json-response2.png)
Die Antwort enthält die Schlüssel-ID sowie die Entitäts-IDs der empfohlenen Entitäten.

Verwenden der Bereitstellungs-API mit [!DNL Recommendations] auf diese Weise können Sie zusätzliche Schritte ausführen, bevor Sie dem Besucher auf dem Nicht-HTML-Gerät Empfehlungen anzeigen. Beispielsweise können Sie die Antwort der Bereitstellungs-API nutzen, um eine zusätzliche Echtzeitsuche von Entitätsattributdetails (Inventar, Preis, Bewertung usw.) aus einem anderen System (z. B. einer CMS-, PIM- oder E-Commerce-Plattform) durchzuführen, bevor Sie die endgültigen Ergebnisse anzeigen.

Mithilfe des in diesem Tutorial beschriebenen Ansatzes können Sie jede Anwendung aufrufen, um die Antwort von [!DNL Target] um personalisierte Empfehlungen bereitzustellen!

## Beispielimplementierungen

Die folgenden Ressourcen enthalten Beispiele für verschiedene nicht auf HTML fokussierte Implementierungen. Beachten Sie, dass jede Implementierung aufgrund des jeweiligen Systems und der betroffenen Geräte eindeutig sein wird.

| Ressource | Details |
| --- | --- |
| [Adobe Target Überall - Implementieren Sie Server Side oder in das IoT](https://expleague.azureedge.net/labs/L733/index.html) | Adobe Summit 2019 Lab, das praktische Erfahrungen für eine React-Anwendung bietet, die serverseitige APIs von Adobe Target nutzt. |
| [Adobe Target in einer mobilen App ohne Adobe SDK](https://community.tealiumiq.com/t5/Universal-Data-Hub/Adobe-Target-in-a-Mobile-App-Without-the-Adobe-SDK/ta-p/26753) | In diesem Handbuch erfahren Sie, wie Sie Adobe Target in Ihrer App einrichten, ohne das Adobe SDK zu installieren. Diese Lösung verwendet die Tealium SDK-Webansicht und das Remote Commands-Modul, um Anfragen an die Adobe Visitor API (Experience Cloud) und die Adobe Target-API zu senden und zu empfangen. |
| [Funktionsweise von Adobe Target in mobilen Apps](https://experienceleague.adobe.com/docs/target/using/implement-target/mobile-apps/mobile-how-target-works-mobile-apps.html?lang=en) | How [!DNL Target] funktioniert mit dem Mobile SDK |
| [Konfigurieren der [!DNL Target] Erweiterung in Experience Platform Launch und Implementierung [!DNL Target] APIs](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-target) | Schritte zum Konfigurieren der [!DNL Target] Erweiterung in Experience Platform Launch hinzufügen, [!DNL Target] Erweiterung der App und Implementierung [!DNL Target] APIs zum Anfordern von Aktivitäten, Vorabrufen von Angeboten und Wechseln in den visuellen Vorschaumodus. |
| [Adobe Target Node Client](https://www.npmjs.com/package/@adobe/target-nodejs-sdk) | Open-Source [!DNL Target] Node.js-SDK v1.0 |
| [Serverseitige Übersicht](https://experienceleague.adobe.com/docs/target/using/implement-target/server-side/api-and-sdk-overview.html?lang=en) | Informationen zu Server-seitigen Adobe Target-Bereitstellungs-APIs, Server-seitigen Batch-Bereitstellungs-APIs, Node.js-SDK und Adobe Target [!DNL Recommendations] APIs. |
| [Adobe Campaign Content Recommendations in E-Mail](https://medium.com/adobetech/adobe-campaign-content-recommendations-in-email-b51ced771d7f) | Blog, der beschreibt, wie Inhaltsempfehlungen in E-Mails über Adobe Target und Adobe I/O Runtime in Adobe Campaign genutzt werden können. |

## Verwalten [!DNL Recommendations] Einrichtung mit APIs

Meistens werden Empfehlungen in der Benutzeroberfläche von Adobe Target konfiguriert und dann über die [!DNL Target] APIs aus Gründen wie den oben genannten. Diese Koordinierung zwischen Benutzeroberfläche und API ist üblich. Manchmal möchten Benutzer jedoch möglicherweise alle Aktionen über APIs durchführen - sowohl die Einrichtung als auch die Verwendung von Ergebnissen. Weniger häufig kann der Benutzer jedoch absolut konfigurieren, ausführen, *und* die Ergebnisse von Empfehlungen vollständig mithilfe der APIs nutzen.

Wir haben in einer [früherer Abschnitt](https://developer.adobe.com/target/before-administer/recs-api/manage-catalog/){target=&quot;_blank&quot;} wie Adobe Target Recommendations-Entitäten verwaltet und serverseitig bereitgestellt werden. Auf ähnliche Weise ermöglicht Ihnen Adobe I/O die Verwaltung von Kriterien, Promotions, Sammlungen und Designvorlagen, ohne sich bei Adobe Target anmelden zu müssen. Eine vollständige Liste aller [!DNL Recommendations] APIs finden Sie [here](https://developers.adobetarget.com/api/recommendations/), aber hier finden Sie eine Zusammenfassung zur Referenz.

| Ressource | Details |
| --- | --- |
| [Sammlungen](https://developers.adobetarget.com/api/recommendations/#tag/Collections) | Auflisten, Erstellen, Abrufen, Bearbeiten und Löschen von Sammlungen. |
| [Kriterien](https://developers.adobetarget.com/api/recommendations/#tag/Criteria) | Kriterien auflisten und abrufen. |
| [Designs](https://developers.adobetarget.com/api/recommendations/#tag/Designs) | Auflisten, Erstellen, Abrufen, Bearbeiten, Löschen und Überprüfen von Designs. |
| [Entitäten](https://developers.adobetarget.com/api/recommendations/#tag/Entities) | Speichern, löschen und rufen Sie Entitäten ab. |
| [Promotions](https://developers.adobetarget.com/api/recommendations/#tag/Promotions) | Auflisten, Erstellen, Abrufen, Bearbeiten und Löschen von Promotions. |
| [Kategoriekriterien](https://developers.adobetarget.com/api/recommendations/#tag/Category-Criteria) | Kategoriekriterien auflisten, erstellen, abrufen, bearbeiten und löschen. |
| [Benutzerdefinierte Kriterien](https://developers.adobetarget.com/api/recommendations/#tag/Custom-Criteria) | Benutzerdefinierte Kriterien auflisten, erstellen, abrufen, bearbeiten und löschen. |
| [Elementkriterien](https://developers.adobetarget.com/api/recommendations/#tag/Item-Criteria) | Auflisten, Erstellen, Abrufen, Bearbeiten und Löschen von Elementkriterien. |
| [Popularitätskriterien](https://developers.adobetarget.com/api/recommendations/#tag/Popularity-Criteria) | Beliebtheitskriterien auflisten, erstellen, abrufen, bearbeiten und löschen. |
| [Profilattributkriterien](https://developers.adobetarget.com/api/recommendations/#tag/Profile-Attribute-Criteria) | Profilattributkriterien auflisten, erstellen, abrufen, bearbeiten und löschen. |
| [Letzte Kriterien](https://developers.adobetarget.com/api/recommendations/#tag/Recent-Criteria) | Letzte Kriterien auflisten, erstellen, abrufen, bearbeiten und löschen. |
| [Sequenzkriterien](https://developers.adobetarget.com/api/recommendations/#tag/Sequence-Criteria) | Auflisten, Erstellen, Abrufen, Bearbeiten und Löschen von Sequenzkriterien. |

## Referenzdokumentation

* [Dokumentation zur Adobe Target Admin API](https://developer.adobe.com/target/administer/admin-api/){target=&quot;_blank&quot;}
* [Adobe Target-Bereitstellungs-API](https://developer.adobe.com/target/implement/delivery-api/){target=&quot;_blank&quot;}
* [Integration  [!DNL Recommendations]  von in E-Mail](https://experienceleague.adobe.com/docs/target/using/recommendations/recommendations-faq/integrating-recs-email.html)

## Zusammenfassung und Überprüfung

Herzlichen Glückwunsch! Mit diesem Tutorial haben Sie Folgendes gelernt:
* [Verwalten Ihres Katalogs mithilfe der Recommendations-API](https://developer.adobe.com/target/before-administer/recs-api/manage-catalog/){target=&quot;_blank&quot;}
* [Benutzerdefinierte Kriterien mit der Recommendations-API verwalten](https://developer.adobe.com/target/before-administer/recs-api/manage-custom-criteria/){target=&quot;_blank&quot;}
* [Verwenden der Bereitstellungs-API mit Recommendations](https://developer.adobe.com/target/before-administer/recs-api/fetch-recs-server-side-delivery-api/){target=&quot;_blank&quot;}
