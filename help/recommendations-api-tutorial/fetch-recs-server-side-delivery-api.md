---
title: Abrufen von Recommendations mit der Versand-API
keywords: recommendations;adobe recommendations;premium;api;apis
description: Adobe Target Recommendations verfügt über eine dedizierte Reihe von APIs, mit denen Sie Ihren Katalog mit empfohlbaren Produkten und/oder Inhalten verwalten können. Ihre Empfehlungsalgorithmen und -Kampagnen zu verwalten; und geben Empfehlungen in JSON-, HTML- oder XML-Objekten für die Anzeige in Web-, Mobil-, E-Mail-, IOT- und anderen Kanälen ab.
kt: 3815
audience: developer
doc-type: tutorial
activity: use
feature: api
topics: recommendations;adobe recommendations;premium;api;apis
solution: Target
author: Judy Kim
translation-type: tm+mt
source-git-commit: c221f434ce9daec03dbb4d897343775b40b14462
workflow-type: tm+mt
source-wordcount: '1473'
ht-degree: 0%

---


# Abrufen [!DNL Recommendations] mit der Versand-API

Die Adobe Target- und Adobe Target- [!DNL Recommendations] APIs können verwendet werden, um Antworten auf Webseiten zu liefern, können aber auch in Nicht-HTML-basierten Erlebnissen wie Apps, Bildschirmen, Konsolen, E-Mails, Kiosks und anderen Anzeigegeräten verwendet werden. Mit anderen Worten, wenn [!DNL Target] Bibliotheken und JavaScript nicht verwendet werden können, ermöglicht uns die **[!DNL Target]Versand-API** weiterhin den Zugriff auf die gesamte Bandbreite der [!DNL Target] Funktionen, um personalisierte Erlebnisse bereitzustellen.

>[!NOTE]
>
> Verwenden Sie beim Anfordern von Inhalten, die tatsächliche Empfehlungen enthalten (empfohlene Produkte oder Artikel), die [!DNL Target] Versand-API.

Um Empfehlungen abzurufen, senden Sie einen Adobe Target Versand API-POST-Aufruf mit den entsprechenden Kontextinformationen, die eine Benutzer-ID (zur Verwendung mit Profil-spezifischen Empfehlungen wie den zuletzt angezeigten Artikeln des Benutzers), einen relevanten Mbox-Namen, Mbox-Parameter, Profil-Parameter oder andere Attribute enthalten können. Die Antwort umfasst empfohlene entity.ids (und kann andere Entitätsdaten enthalten) im JSON- oder HTML-Format, das dann auf dem Gerät angezeigt werden kann.

Die [Versand-API](https://developers.adobetarget.com/api/delivery-api/) für Adobe Target stellt alle vorhandenen Funktionen bereit, die eine Standard- [!DNL Target] Anforderung bietet.

>[!NOTE]
>Die Versand-API:
>* Ermöglicht das Abrufen von Erlebnissen oder Angeboten für einen Ort und eine Audience in REST-voller Weise.
>* Erfordert keine Authentifizierung.
>* Nur POSTs.
>* Verarbeitet keine Cookies oder führt keine Umleitungsanrufe durch.
>* erfordert oder erkennt keine &quot;Benutzerrollen&quot;. Ruft einfach Inhalte ab oder meldet Ereignis an [!DNL Target] Edge-Server.


Gehen Sie wie folgt vor, um mit der Versand-API [!DNL Target] Erlebnisse einschließlich Empfehlungen bereitzustellen:

1. Erstellen Sie eine [!DNL Target] Aktivität (A/B, XT, AP oder [!DNL Recommendations]) mit dem formularbasierten Composer (nicht mit dem Visual Experience Composer).
2. Verwenden Sie die Versand-API, um eine Antwort für die Anfragen zu erhalten, die von der soeben erstellten [!DNL Target] Aktivität generiert wurden.

<!-- Q: Why are BOTH steps necessary for this? If you have a Form-based recommendation defined for an mbox, what's the point/benefit of ALSO having the Delivery API step in to retrieve results? Why can't you just have the Form-based Rec deliver the results in the destination device...?? A: See use case below... it's when you want to "intercept" the pending results in order to do more stuff prior to displaying the results. Things like real-time comparisons to inventory levels. -->

## Erstellen einer Empfehlung mit dem formularbasierten Experience Composer

Um Empfehlungen zu erstellen, die mit der Versand-API verwendet werden können, verwenden Sie den [formularbasierten Composer](https://docs.adobe.com/content/help/en/target/using/experiences/form-experience-composer.html).

1. Erstellen und speichern Sie zunächst einen JSON-basierten Entwurf, der in Ihrer Empfehlung verwendet werden soll. Beispiel-JSON sowie Hintergrundinformationen darüber, wie JSON-Antworten beim Konfigurieren einer formularbasierten Aktivität zurückgegeben werden können, finden Sie in der Dokumentation zum [Erstellen von Empfehlungsentwürfen](https://docs.adobe.com/content/help/en/target/using/recommendations/recommendations-design/create-design.html). In diesem Beispiel heißt der Entwurf *Simple JSON.*

   ![server-side-create-recs-json-design.png](assets/server-side-create-recs-json-design.png)

2. Navigieren Sie [!DNL Target]zu **[!UICONTROL Aktivitäten]> Aktivität[!UICONTROL erstellen]>[!UICONTROL Recommendations]** und wählen Sie dann **[!UICONTROL Formular]**.

   ![server-side-create-recs.png](assets/server-side-create-recs.png)

3. Wählen Sie eine Eigenschaft und klicken Sie auf **[!UICONTROL Weiter]**.
4. Definieren Sie den Ort, an den die Benutzer die Antwort der Empfehlung erhalten sollen. Im folgenden Beispiel wird der Speicherort *api_charter* verwendet. Wählen Sie den zuvor erstellten JSON-basierten Entwurf mit dem Namen *Simple JSON aus.*
   ![server-side-create-recs-form.png](assets/server-side-create-recs-form1.png)
5. Speichern und aktivieren Sie die Empfehlung. Es werden Ergebnisse generiert. [Sobald die Ergebnisse vorliegen](https://docs.adobe.com/content/help/en/target/using/recommendations/recommendations-activity/previewing-and-launching-your-recommendations-activity.html), können Sie sie mit der Versand-API abrufen.

## Verwenden der Versand-API

The syntax for the [Delivery API](https://developers.adobetarget.com/api/delivery-api/#tag/Delivery-API) is:

`POST https://{{CLIENT_CODE}}.tt.omtrdc.net/rest/v1/delivery`

1. Beachten Sie, dass der Clientcode erforderlich ist. Zur Erinnerung: Ihr Clientcode befindet sich in Adobe Target, indem Sie zu **[!UICONTROL Recommendations]>[!UICONTROL Einstellungen]** navigieren. Beachten Sie den Wert **[!UICONTROL Clientcode]** im Abschnitt **[!UICONTROL Recommendations-API-Token]** .
   ![client-code.png](assets/client-code.png)
1. Sobald Sie Ihren Clientcode haben, erstellen Sie Ihren Versand-API-Aufruf. Das folgende Beispiel beginnt mit dem **[!UICONTROL Web Batched Mboxes Versand API-Aufruf]** , der in der Postman-Auflistung [der](https://developers.adobetarget.com/api/delivery-api/#section/Getting-Started/Postman-Collection)Versand-API bereitgestellt wird, und nimmt die erforderlichen Änderungen vor. Beispiel:
   * Die **Browser** - und **Adressobjekte** wurden aus dem **Körper** entfernt, da sie für Anwendungsfälle ohne HTML nicht erforderlich sind.
   * *api_charter* wird in diesem Beispiel als Ortsname aufgeführt
   * die entity.id angegeben wird, da diese Empfehlung auf der Ähnlichkeit von Inhalten basiert, an die ein aktueller Elementschlüssel übergeben werden muss [!DNL Target].
      ![server-side-Versand-API-call.png](assets/server-side-delivery-api-call2.png)Denken Sie daran, Ihre Abfrage-Parameter korrekt zu konfigurieren. Achten Sie beispielsweise darauf,`{{CLIENT_CODE}}` die erforderlichen Angaben zu machen. <!--Q: In the updated call syntax, entity.id is listed as a profileParameter instead of an mboxParameter as in older versions. --> <!--Q: Old image ![server-side-create-recs-post.png](assets/server-side-create-recs-post.png) Old accompanying text: "Note this recommendation is based on Content Similar products based on the entity.id sent via mboxParameters." -->
      ![client-code3](assets/client-code3.png)
1. Senden Sie die Anforderung. Dies wird gegen den Speicherort *api_charter* ausgeführt, auf dem eine aktive Empfehlung ausgeführt wird, die mit Ihrem JSON-Entwurf definiert wird, der eine Liste empfohlener Entitäten ausgibt.
1. Erhalten Sie eine Antwort auf Basis des JSON-Entwurfs.
   ![server-side-create-recs-json-response2.png](assets/server-side-create-recs-json-response2.png)Die Antwort enthält die Schlüssel-ID sowie die Entitäts-IDs der empfohlenen Entitäten.

Durch die Verwendung der Versand-API mit [!DNL Recommendations] dieser Methode können Sie zusätzliche Schritte ausführen, bevor Sie Empfehlungen für den Besucher auf einem Nicht-HTML-Gerät anzeigen. Beispielsweise können Sie die Antwort der Versand-API verwenden, um eine zusätzliche Echtzeitsuche von Entitätsattributdetails (Bestand, Preis, Bewertung usw.) aus einem anderen System (z. B. einer CMS-, PIM- oder E-Commerce-Plattform) durchzuführen, bevor die Endergebnisse angezeigt werden.

Mithilfe des in diesem Lernprogramm beschriebenen Ansatzes können Sie jede Anwendung nutzen, um die Antwort zu nutzen und personalisierte Empfehlungen [!DNL Target] bereitzustellen!

## Beispielimplementierungen

Die folgenden Ressourcen bieten Beispiele für verschiedene Implementierungen ohne HTML-Fokus. Denken Sie daran, dass jede Implementierung aufgrund des jeweiligen Systems und der verwendeten Geräte einzigartig ist.

| Ressource | Details |
| --- | --- |
| [RESTful-APIs in AEM](https://helpx.adobe.com/experience-manager/using/restful-services.html) | Erstellen und Bereitstellen eines Adobe Experience Manager OSGi-Bundles, das Daten von einem RESTful-Webdienst eines Drittanbieters nutzt. |
| [Adobe Target Überall - Implementieren der Serverseite oder im IoT](https://expleague.azureedge.net/labs/L733/index.html) | Adobe Summit 2019 Lab, das praktische Erfahrungen mit einer React-Anwendung bietet, die Adobe Target-serverseitige APIs nutzt. |
| [Adobe Target in einer mobilen App ohne Adobe SDK](https://community.tealiumiq.com/t5/Universal-Data-Hub/Adobe-Target-in-a-Mobile-App-Without-the-Adobe-SDK/ta-p/26753) | In diesem Handbuch wird beschrieben, wie Sie Adobe Target in Ihrer mobilen App einrichten, ohne das Adobe SDK zu installieren. Diese Lösung verwendet die Tealium SDK-Webansicht und das Remote Commands-Modul, um Anfragen an die Adobe Besucher API (Experience Cloud) und die Adobe Target API zu senden und zu empfangen. |
| [Funktionsweise von Adobe Target in mobilen Apps](https://docs.adobe.com/content/help/en/target/using/implement-target/mobile-apps/mobile-how-target-works-mobile-apps.html) | Wie [!DNL Target] funktioniert das Mobile SDK? |
| [Konfigurieren [!DNL Target] extension in Experience Platform Launch and Implementing [!DNL Target] der APIs](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-target) | Schritte zum Konfigurieren der [!DNL Target] Erweiterung in Experience Platform Launch, zum Hinzufügen der [!DNL Target] Erweiterung zu Ihrer App und zum Implementieren von [!DNL Target] APIs zum Anfordern von Aktivitäten, zum vorherigen Abrufen von Angeboten und zum Aktivieren des Visual Vorschau-Modus. |
| [Adobe Target Node Client](https://www.npmjs.com/package/@adobe/target-nodejs-sdk) | Open-Source-SDK [!DNL Target] Node.js v1.0 |
| [Serverseitige Übersicht](https://docs.adobe.com/content/help/en/target/using/implement-target/server-side/api-and-sdk-overview.html) | Informationen zu Adobe Target Server Side Versand APIs, Server Side Batch Versand APIs, Node.js SDK und Adobe Target [!DNL Recommendations] APIs. |
| [Adobe Campaign Content Recommendations in E-Mail](https://medium.com/adobetech/adobe-campaign-content-recommendations-in-email-b51ced771d7f) | Blog, in dem beschrieben wird, wie Inhaltsempfehlungen per E-Mail über Adobe Target und Adobe I/O Runtime in Adobe Campaign genutzt werden können. |

## Verwalten von [!DNL Recommendations] Einstellungen mit APIs

In den meisten Fällen werden Empfehlungen in der Adobe Target-Benutzeroberfläche konfiguriert und dann über die [!DNL Target] APIs verwendet oder aufgerufen, z. B. aus den oben genannten Gründen. Diese Koordination zwischen Benutzeroberfläche und API ist häufig. Manchmal möchten Benutzer jedoch alle Aktionen über APIs durchführen - sowohl die Einrichtung als auch die Verwendung der Ergebnisse. Obwohl dies viel seltener der Fall ist, können Benutzer die Ergebnisse von Empfehlungen vollständig mithilfe der APIs konfigurieren, ausführen *und* nutzen.

In einem [früheren Abschnitt](manage-catalog.md) haben wir gelernt, wie Adobe Target Recommendations-Entitäten verwaltet und serverseitig bereitgestellt werden. In ähnlicher Weise können Sie mit der Adobe-E/A Kriterien, Promotions, Sammlungen und Designvorlagen verwalten, ohne sich bei Adobe Target anmelden zu müssen. Eine vollständige Liste aller [!DNL Recommendations] APIs finden Sie [hier](http://developers.adobetarget.com/api/recommendations/), aber hier finden Sie eine Übersicht.

| Ressource | Details |
| --- | --- |
| [Sammlungen](http://developers.adobetarget.com/api/recommendations/#tag/Collections) | Erstellen, Abrufen, Bearbeiten und Löschen von Sammlungen. |
| [Kriterien](http://developers.adobetarget.com/api/recommendations/#tag/Criteria) | Liste und Kriterien abrufen. |
| [Entwürfe](http://developers.adobetarget.com/api/recommendations/#tag/Designs) | Liste, Erstellen, Abrufen, Bearbeiten, Löschen und Überprüfen von Entwürfen. |
| [Entitäten](http://developers.adobetarget.com/api/recommendations/#tag/Entities) | Speichern, löschen und abrufen von Entitäten. |
| [Promotions](http://developers.adobetarget.com/api/recommendations/#tag/Promotions) | Liste, Erstellen, Abrufen, Bearbeiten und Löschen von Promotions. |
| [Kategorien](http://developers.adobetarget.com/api/recommendations/#tag/Category-Criteria) | Kriterien für die Liste, Erstellung, Abrufen, Bearbeitung und Löschen von Kategorien. |
| [Benutzerspezifische Kriterien](http://developers.adobetarget.com/api/recommendations/#tag/Custom-Criteria) | Liste, Erstellen, Abrufen, Bearbeiten und Löschen benutzerdefinierter Kriterien. |
| [Elementkriterien](http://developers.adobetarget.com/api/recommendations/#tag/Item-Criteria) | Liste, Erstellen, Abrufen, Bearbeiten und Löschen von Elementkriterien. |
| [Popularitätskriterien](http://developers.adobetarget.com/api/recommendations/#tag/Popularity-Criteria) | Beliebtheitskriterien für Liste, Erstellen, Abrufen, Bearbeiten und Löschen |
| [Profil-Attributkriterien](http://developers.adobetarget.com/api/recommendations/#tag/Profile-Attribute-Criteria) | Liste, Erstellen, Abrufen, Bearbeiten und Löschen von Profil-Attributkriterien. |
| [Letzte Kriterien](http://developers.adobetarget.com/api/recommendations/#tag/Recent-Criteria) | Liste, Erstellen, Abrufen, Bearbeiten und Löschen aktueller Kriterien. |
| [Sequenzkriterien](http://developers.adobetarget.com/api/recommendations/#tag/Sequence-Criteria) | Liste, Erstellen, Abrufen, Bearbeiten und Löschen von Sequenzkriterien. |

## Referenzdokumentation

* [Adobe Target API-Dokumentation](https://developers.adobetarget.com/api/#getting-started)
* [Adobe Target Versand API](https://developers.adobetarget.com/api/delivery-api/)
* [Mit [!DNL Recommendations] E-Mail integrieren](https://docs.adobe.com/content/help/en/target/using/recommendations/recommendations-faq/integrating-recs-email.html)

## Zusammenfassung und Überprüfung

Herzlichen Glückwunsch! Mit dem Abschluss dieses Lernprogramms haben Sie gelernt, wie:
* [Kataloge mit der Recommendations API verwalten](manage-catalog.md)
* [Verwalten benutzerdefinierter Kriterien mit der Recommendations API](manage-custom-criteria.md)
* [Verwenden der Versand-API mit Recommendations](fetch-recs-server-side-delivery-api.md)
