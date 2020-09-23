---
title: Benutzerspezifische Kriterien verwalten
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
source-wordcount: '959'
ht-degree: 1%

---


# Benutzerspezifische Kriterien verwalten

Manchmal [!DNL Recommendations] sind die von Ihnen bereitgestellten Algorithmen nicht in der Lage, bestimmte Artikel zu überdecken, die Sie bewerben möchten. In einem solchen Fall bieten benutzerdefinierte Kriterien die Möglichkeit, einen bestimmten Satz empfohlener Artikel für ein bestimmtes Schlüsselelement oder eine bestimmte Kategorie bereitzustellen. Sie definieren die Zuordnung zwischen dem Schlüsselelement oder der Kategorie und den empfohlenen Elementen und importieren diese Zuordnung als benutzerspezifische Kriterien. Dieser Vorgang wird in der Dokumentation zu [benutzerdefinierten Kriterien beschrieben](https://docs.adobe.com/content/help/en/target/using/recommendations/criteria/recommendations-csv.html). Wie in der Dokumentation beschrieben, können Sie benutzerdefinierte Kriterien über die Benutzeroberfläche (Benutzeroberfläche) erstellen, bearbeiten und löschen. [!DNL Target] Sie [!DNL Target] erhalten jedoch auch eine Reihe von benutzerspezifischen Kriterien-APIs, die eine detailliertere Verwaltung Ihrer benutzerspezifischen Kriterien ermöglichen.

>[!IMPORTANT]
>
>Befolgen Sie diese Gebrauchsanleitung für benutzerdefinierte Kriterien:
>
> Führen Sie entweder alle Schritte (Erstellen, Bearbeiten, Löschen) für ein bestimmtes benutzerdefiniertes Kriterium mithilfe der APIs durch oder führen Sie über die Benutzeroberfläche alle Schritte durch (Erstellen, Bearbeiten, Löschen). Die Verwaltung benutzerdefinierter Kriterien durch eine Kombination aus Benutzeroberfläche und API kann zu widersprüchlichen Informationen oder unerwarteten Ergebnissen führen. Wenn Sie beispielsweise ein benutzerdefiniertes Kriterium in der Benutzeroberfläche erstellen, es dann aber über die API bearbeiten, werden Ihre Aktualisierungen in der Benutzeroberfläche nicht angezeigt, auch wenn sie im Backend aktualisiert werden, wie über die API sichtbar.

## Benutzerspezifische Kriterien erstellen

Zum Erstellen benutzerdefinierter Kriterien mithilfe der API [&quot;Benutzerspezifische Kriterien](https://developers.adobetarget.com/api/recommendations/#operation/createCriteriaCustom)erstellen&quot;lautet die Syntax:

`POST https://mc.adobe.io/{{TENANT_ID}}/target/recs/criteria/custom`

>[!WARNING]
>
>Benutzerdefinierte Kriterien, die mit der API zum Erstellen benutzerdefinierter Kriterien erstellt wurden, wie in dieser Übung beschrieben, werden in der Benutzeroberfläche angezeigt, wo sie bestehen bleiben. Sie können sie nicht in der Benutzeroberfläche bearbeiten oder löschen. Sie können sie **über API** bearbeiten oder löschen, sie werden jedoch weiterhin in der [!DNL Target] Benutzeroberfläche angezeigt. Um die Option zum Bearbeiten oder Löschen in der Benutzeroberfläche beizubehalten, erstellen Sie die benutzerdefinierten Kriterien mithilfe der Benutzeroberfläche gemäß [der Dokumentation](https://docs.adobe.com/content/help/en/target/using/recommendations/criteria/recommendations-csv.html), im Gegensatz zur API &quot;Benutzerspezifische Kriterien erstellen&quot;.

Fahren Sie mit diesem Tutorial erst dann fort, wenn Sie die oben stehende Warnung gelesen haben und es bequem sind, neue benutzerdefinierte Kriterien zu erstellen, die nicht später aus der Benutzeroberfläche gelöscht werden können.

1. Überprüfen `TENANT_ID` und `API_KEY` für die **Erstellung benutzerdefinierter Kriterien** verweisen Sie auf die zuvor festgelegten Postman-Umgebung. Verwenden Sie das unten stehende Bild zum Vergleich.

   ![CreateCustomCriteria1](assets/CreateCustomCriteria1.png)

2. hinzufügen **Body** als **rohe** JSON, die den Speicherort Ihrer CSV-Datei für benutzerdefinierte Kriterien definiert. Verwenden Sie das in der Dokumentation zur API [](https://developers.adobetarget.com/api/recommendations/#operation/getAllCriteriaCustom) zum Erstellen benutzerdefinierter Kriterien bereitgestellte Beispiel als Vorlage, um Ihre `environmentId` und andere Werte nach Bedarf bereitzustellen. In diesem Beispiel verwenden wir LAST_PURCHASED als Schlüssel.

   ![CreateCustomCriteria2](assets/CreateCustomCriteria2.png)

3. Senden Sie die Anforderung und beobachten Sie die Antwort, die die Details der benutzerdefinierten Kriterien enthält, die Sie gerade erstellt haben.

   ![CreateCustomCriteria3](assets/CreateCustomCriteria3.png)

4. Um zu überprüfen, ob Ihre benutzerspezifischen Kriterien erstellt wurden, navigieren Sie innerhalb von Adobe Target zu **[!UICONTROL Recommendations]>[!UICONTROL Kriterien]** und suchen Sie nach Ihren Kriterien anhand des Namens oder verwenden Sie im nächsten Schritt die API **für benutzerspezifische Kriterien der** Liste.

   ![CreateCustomCriteria4](assets/CreateCustomCriteria4.png)

In diesem Fall haben wir einen Fehler. Lassen Sie uns den Fehler untersuchen, indem wir die benutzerspezifischen Kriterien mithilfe der API **für benutzerspezifische** Listen genauer untersuchen.

## Benutzerspezifische Kriterien für Listen

Um eine Liste aller benutzerspezifischen Kriterien zusammen mit Details zu den einzelnen Kriterien abzurufen, verwenden Sie die [Liste Custom Criteria API](https://developers.adobetarget.com/api/recommendations/#operation/getAllCriteriaCustom). Die Syntax lautet:

`GET https://mc.adobe.io/{{TENANT_ID}}/target/recs/criteria/custom`

1. Überprüfen `TENANT_ID` und `API_KEY` wie zuvor, und senden Sie die Anforderung. Beachten Sie in der Antwort die benutzerdefinierte Kriteriums-ID sowie Details zur oben genannten Fehlermeldung.
   ![ListCustomCriteria](assets/ListCustomCriteria.png)

In diesem Fall ist der Fehler aufgetreten, weil die Serverinformationen nicht korrekt sind. Das bedeutet, dass [!DNL Target] kein Zugriff auf die CSV-Datei möglich ist, die die Definition der benutzerdefinierten Kriterien enthält. Bearbeiten wir die benutzerdefinierten Kriterien, um dies zu korrigieren.

## Benutzerspezifische Kriterien bearbeiten

Um die Details einer benutzerdefinierten Kriteriendefinition zu ändern, verwenden Sie die API [&quot;Benutzerspezifische Kriterien bearbeiten&quot;](https://developers.adobetarget.com/api/recommendations/#operation/updateCriteriaCustom). Die Syntax lautet:

`POST https://mc.adobe.io/{{TENANT_ID}}/target/recs/criteria/custom/:criteriaId`

1. Überprüfen `TENANT_ID` und `API_KEY`, wie zuvor.
   ![EditCustomCriteria1](assets/EditCustomCriteria1.png)

1. Geben Sie die Kriterien-ID des (einzelnen) benutzerspezifischen Kriteriums an, das Sie bearbeiten möchten.
   ![EditCustomCriteria2](assets/EditCustomCriteria2.png)

1. Geben Sie im Body aktualisierte JSON-Dateien mit den richtigen Serverinformationen ein. (Geben Sie für diesen Schritt den FTP-Zugriff auf einen Server an, auf den Sie zugreifen können.)
   ![EditCustomCriteria3](assets/EditCustomCriteria3.png)

1. Senden Sie die Anforderung und notieren Sie sich die Antwort.
   ![EditCustomCriteria4](assets/EditCustomCriteria4.png)

Überprüfen Sie anhand der API ****&quot;Benutzerspezifische Kriterien abrufen&quot;den Erfolg der aktualisierten benutzerspezifischen Kriterien.

## Benutzerspezifische Kriterien abrufen

Verwenden Sie zur Ansicht benutzerdefinierter Kriteriendetails für ein bestimmtes benutzerdefiniertes Kriterium die API [&quot;Benutzerspezifische Kriterien abrufen&quot;](https://developers.adobetarget.com/api/recommendations/#operation/getCriteriaCustom). Die Syntax lautet:

`GET https://mc.adobe.io/{{TENANT_ID}}/target/recs/criteria/custom/:criteriaId`

1. Geben Sie die Kriterien-ID der benutzerdefinierten Kriterien an, deren Details Sie erhalten möchten. Senden Sie die Anforderung und überprüfen Sie die Antwort.
   ![GetCustomCriteria.png](assets/GetCustomCriteria.png)
1. Überprüfen Sie den Erfolg. (Überprüfen Sie in unserem Fall, ob keine weiteren FTP-Fehler vorliegen.)
   ![GetCustomCriteria1.png](assets/GetCustomCriteria1.png)
1. (Optional) Überprüfen Sie, ob das Update in der Benutzeroberfläche korrekt dargestellt wird.
   ![GetCustomCriteria2.png](assets/GetCustomCriteria2.png)

## Benutzerspezifische Kriterien löschen

Löschen Sie mithilfe der zuvor genannten Kriterien-ID Ihre benutzerspezifischen Kriterien mit der API zum [Löschen benutzerdefinierter Kriterien](https://developers.adobetarget.com/api/recommendations/#operation/deleteCriteriaCustom). Die Syntax lautet:

`DELETE https://mc.adobe.io/{{TENANT_ID}}/target/recs/criteria/custom/:criteriaId`

1. Geben Sie die Kriterien-ID des (einzelnen) benutzerspezifischen Kriteriums an, das Sie löschen möchten. Klicken Sie auf **Senden**.
   ![DeleteCustomCriteria1](assets/DeleteCustomCriteria1.png)

1. Überprüfen Sie, ob die Kriterien mit &quot;Benutzerdefinierte Kriterien abrufen&quot;gelöscht wurden.
   ![DeleteCustomCriteria2](assets/DeleteCustomCriteria2.png)In diesem Fall gibt der erwartete 404-Fehler an, dass die gelöschten Kriterien nicht gefunden werden können.

>[!NOTE]
>Zur Erinnerung: Die Kriterien werden nicht aus der [!DNL Target] Benutzeroberfläche entfernt, obwohl sie gelöscht wurden, da sie mit der API &quot;Benutzerspezifische Kriterien erstellen&quot;erstellt wurden.

Herzlichen Glückwunsch! Sie können jetzt mit der [!DNL Recommendations] API Details zu benutzerspezifischen Kriterien erstellen, Liste, bearbeiten, löschen und abrufen. Im nächsten Abschnitt verwenden Sie die [!DNL Target] Versand-API, um Empfehlungen abzurufen.

[Weiter &quot;Recommendations mit der serverseitigen Versand-API abrufen&quot;>](fetch-recs-server-side-delivery-api.md)
