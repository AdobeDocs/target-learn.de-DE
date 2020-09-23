---
title: Authentifizierung konfigurieren
keywords: recommendations;adobe recommendations;premium;api;apis
description: Adobe Target Recommendations verfügt über eine dedizierte Reihe von APIs, mit denen Sie Ihren Katalog mit empfohlbaren Produkten und/oder Inhalten verwalten können. Ihre Empfehlungsalgorithmen und -Kampagnen zu verwalten; und geben Empfehlungen in JSON-, HTML- oder XML-Objekten für die Anzeige in Web-, Mobil-, E-Mail-, IOT- und anderen Kanälen ab.
kt: null
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
source-wordcount: '1877'
ht-degree: 2%

---


# Authentifizierung konfigurieren

Die Adobe Target Admin-APIs, einschließlich [!DNL Recommendations] Admin-APIs, werden durch Authentifizierung gesichert, um sicherzustellen, dass nur autorisierte Benutzer auf Adobe Target zugreifen können. Verwenden Sie die [Adobe Developer Console](https://console.adobe.io/) , um diese Authentifizierung für alle Adobe Experience Cloud-Lösungen zu verwalten, einschließlich [!DNL Target].

In dieser Lektion werden die ersten Schritte erläutert, die zum Generieren von Authentifizierungstokens erforderlich sind, um erfolgreich mit Adobe Target-APIs zu interagieren. In den folgenden Abschnitten werden Sie:

1. Erstellen Sie ein Projekt (früher &quot;integration&quot;genannt) in der Adobe Developer Console.
2. Exportieren Sie Projektdetails nach Postman.
3. Generieren Sie ein Inhabermodell-Zugriffstoken.
4. Testen Sie das Zugriffstoken des Inhabers.

## Voraussetzungen

| Ressource | Details |
| --- | --- |
| Postman | Um diese Schritte erfolgreich abzuschließen, rufen Sie die [Postman-App](https://www.postman.com/downloads/) für Ihr Betriebssystem ab. Postman basic ist frei mit der Kontoerstellung. Postman ist zwar für die Verwendung von Adobe Target-APIs im Allgemeinen nicht erforderlich, erleichtert jedoch die Workflows der API und bietet mehrere Postman-Sammlungen an, um die Ausführung der APIs und deren Funktionsweise zu erleichtern. Der Rest dieses Tutorials geht von Arbeitskenntnissen des Postman aus. Hilfe erhalten Sie in der [Postman-Dokumentation](https://learning.getpostman.com/). |
| Verweise | Die Vertrautheit mit den folgenden Ressourcen wird während des gesamten Lernprogramms vorausgesetzt:<UL><li>[Adobe-I/O-Github](https://github.com/adobeio)</li><li>[I/O-Dokumentation zur Adobe der Zielgruppe](https://developers.adobetarget.com/api/#introduction)</li><li>[Recommendations API-Dokumentation](https://developers.adobetarget.com/api/recommendations/)</li></ul> |

## Erstellen eines Adoben-E/A-Projekts

In diesem Abschnitt greifen Sie auf die Adobe Developer Console zu und erstellen ein Projekt für [!DNL Adobe Target]. Weitere Informationen finden Sie in der [Projektdokumentation](https://www.adobe.io/apis/experienceplatform/console/docs.html#!AdobeDocs/adobeio-console/master/projects.md).

<!--1. Generate your private key and public certificate, per the [documentation on authentication](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/JWT/JWTCertificate.md). //<!--as described in **Step 1** of [How to set up Adobe IO: Authentication - Step by Step](https://helpx.adobe.com/marketing-cloud-core/kb/adobe-io-authentication-step-by-step.html). After completing Step 1, return to this tutorial and resume with Step 2, below. // The outcome of this step should be the creation of a `private.key` file and a `certificate_pub.crt` file. Return to this tutorial once you have generated these two files.-->

1. Vergewissern Sie sich, dass Ihr Adoben-Benutzerkonto im [Adobe Admin Console](https://adminconsole.adobe.com/)sowohl auf [Produktadministratorebene](https://helpx.adobe.com/enterprise/using/admin-roles.html) als auch auf [Entwicklerebene](https://helpx.adobe.com/enterprise/using/manage-developers.html) Zugriff auf [!DNL Target]hat.

2. Wählen Sie in der [Adobe Developer Console](https://console.adobe.io/)die Experience Cloud-Organisation aus, für die Sie diese Integration erstellen möchten. (Beachten Sie, dass Sie möglicherweise nur Zugriff auf eine einzige Experience Cloud-Organisation haben.)

   ![configure-io-Zielgruppe-creating-project2.png](assets/configure-io-target-createproject2.png)

3. Click **[!UICONTROL Create new project]**.

   ![configure-io-Zielgruppe-creating-project3.png](assets/configure-io-target-createproject3.png)

4. Klicken Sie auf **[!UICONTROL Hinzufügen API]** , um Ihrem Projekt eine REST-API hinzuzufügen, um auf Adobe Services und Produkte zuzugreifen.

   ![hinzufügen API](assets/configure-io-target-createproject4.png)

5. Wählen Sie **[!DNL Adobe Target]** als Adobe-Dienst, in den Sie integrieren möchten. Klicken Sie auf die **[!UICONTROL Schaltfläche Weiter]** .

   ![configure-io-target-createproject5](assets/configure-io-target-createproject5.png)

6. Wählen Sie eine Option zum Verknüpfen öffentlicher und privater Schlüssel mit der Dienstkontointegration, die Sie zur Zielgruppe erstellen. Wählen Sie für dieses Lernprogramm **[!UICONTROL Option 1: Generieren Sie ein Schlüsselpaar]** und klicken Sie auf **[!UICONTROL Generate keypair]**.
   ![configure-io-target-createproject6](assets/configure-io-target-createproject6.png)

7. Beachten Sie die Ergebnisse! Beachten Sie entsprechend den Anweisungen die automatisch heruntergeladene Konfigurationsdatei (`config`), die Ihren privaten Schlüssel enthält. Klicken Sie auf **[!UICONTROL Weiter]**.
   ![configure-io-target-createproject7](assets/configure-io-target-createproject7.png)
8. Überprüfen Sie im Dateisystem den Speicherort von `config`, d. h. die komprimierte Konfigurationsdatei, die im vorherigen Schritt erstellt wurde. Diese `config` Datei enthält wiederum Ihren privaten Schlüssel, den Sie später benötigen werden. Der genaue Speicherort in Ihrem Dateisystem kann sich von dem hier gezeigten unterscheiden.
   ![configure-io-target-createproject8](assets/configure-io-target-createproject8.png)
9. Wählen Sie in der Adobe Developer Console die [Produkt-Profil aus, die den Eigenschaften entsprechen, in denen Sie arbeiten](https://helpx.adobe.com/enterprise/using/manage-products-and-profiles.html) [!DNL Recommendations]. (Wenn Sie keine Eigenschaften verwenden, wählen Sie die Option &quot;Standard-Arbeitsbereich&quot;.) Klicken Sie auf Konfigurierte API **[!UICONTROL speichern]**.
   ![configure-io-target-createproject9](assets/configure-io-target-createproject9.png)

10. Klicken Sie auf Integration **[!UICONTROL erstellen]**. Sie sollten eine temporäre Meldung erhalten, die darauf hinweist, dass Ihre API erfolgreich konfiguriert wurde.

11. Benennen Sie als letzten Schritt Ihr Projekt in einen aussagekräftigeren Namen als das Original um `Project 1`. Navigieren Sie dazu mithilfe des Navigationspfads zum Projekt, klicken Sie auf Projekt **[!UICONTROL bearbeiten]** , um auf den Modal **Projekt[!UICONTROL bearbeiten] zuzugreifen, und benennen Sie das Projekt um.

![configure-io-target-createproject11](assets/configure-io-target-createproject11.png)

>[!NOTE]
> 
>In diesem Tutorial nennen wir unser Projekt &quot;Zielgruppe Integration&quot;. Wenn Sie davon ausgehen, dass Sie Ihr Projekt für mehr als nur Adobe Target verwenden, sollten Sie es entsprechend benennen. Sie können ihn beispielsweise &quot;Adobe-APIs&quot;oder &quot;Experience Cloud-APIs&quot;nennen, da er mit anderen Lösungen in der Adobe Experience Cloud verwendet werden kann.

## Projektdetails exportieren

Nachdem Sie jetzt ein Adobe-Projekt haben, das Sie für den Zugriff verwenden können, müssen Sie sicherstellen, dass Sie Details zu diesem Projekt zusammen mit Ihren Adoben-API-Anforderungen senden [!DNL Target]können. Diese Details sind erforderlich, um mit mehreren Adoben-APIs, einschließlich mehrerer [!DNL Target] APIs, zu interagieren. Die Integrationsdetails umfassen beispielsweise Autorisierungs- und Authentifizierungsinformationen, die von den [!DNL Target] Admin-APIs benötigt werden. Um die APIs mit Postman zu verwenden, müssen Sie diese Details in Postman eintragen.

Es gibt viele Möglichkeiten, die Details Ihres Projekts in Postman anzugeben, aber in diesem Abschnitt nutzen wir einige vordefinierte Funktionen und Sammlungen. Zunächst (in diesem Abschnitt) exportieren Sie die Details Ihrer Integration in eine Postman-Umgebung. Als Nächstes erstellen Sie (im folgenden Abschnitt) ein Zugriffstoken für den Inhaber, um Ihnen Zugriff auf die erforderlichen Adoben zu gewähren.

>[!NOTE]
>
>Videoanleitungen zu allen Experience Cloud-Lösungen, einschließlich [!DNL Target]finden Sie unter [Verwenden von Postman mit Experience Platform-APIs](https://docs.adobe.com/content/help/en/platform-learn/tutorials/apis/postman.html). Die folgenden Abschnitte sind für die [!DNL Target] APIs relevant:
>
> 1. I/O-Integrationsdetails für Adoben nach Postman exportieren
> 2. Erstellen eines Zugriffstokens mit Postman

>
> 
Diese Schritte werden nachfolgend beschrieben.

1. Navigieren Sie in der [Adobe Developer Console](https://console.adobe.io/)zur Ansicht der **[!UICONTROL JWT-Anmeldedaten (Service Account) Ihres neuen Projekts]** . Verwenden Sie entweder die linke Navigation oder den Abschnitt **[!UICONTROL Anmeldeinformationen]** wie gezeigt.
   ![JWT1](assets/configure-io-target-jwt1.png)In den **[!UICONTROL Berechtigungsdetails]** beachten Sie, dass Sie Ihre **öffentlichen Schlüssel(e)**, **Client-ID**und andere Informationen zu Ihrem Dienstkonto Ansicht haben können.
   ![JWT1a](assets/configure-io-target-jwt1a.png)
2. Klicken Sie auf , um zu Informationen zur **[!UICONTROL Adobe Target]** -API zu navigieren. Verwenden Sie entweder die linke Navigation oder den Abschnitt **[!UICONTROL Connected products and services]** (Verbundene Produkte und Dienste) wie gezeigt.
   ![JWT2](assets/configure-io-target-jwt2.png)
3. Klicken Sie auf **[!UICONTROL Download für Postman]** > **[!UICONTROL Dienstkonto (JWT)]** , um eine JSON-Datei zu erstellen, die Ihre Authentifizierungsinformationen für eine Postman-Umgebung erfasst.
   ![JWT3](assets/configure-io-target-jwt3.png)Notieren Sie die JSON-Datei im Dateisystem.
   ![JWT3a](assets/configure-io-target-jwt3a.png)
4. Klicken Sie in Postman auf das Zahnradsymbol, um Ihre Umgebung zu verwalten, und klicken Sie dann auf **Importieren** , um die JSON-Datei (Umgebung) zu importieren.
   ![JWT4](assets/configure-io-target-jwt4.png)
5. Wählen Sie die Datei aus und klicken Sie auf **Öffnen**.
   ![JWT5](assets/configure-io-target-jwt5.png)
6. Klicken Sie im Modal &quot;Postman **Umgebung** verwalten&quot;auf den Namen der neu importierten Umgebung, um sie zu überprüfen. (Ihr Name der Umgebung kann sich von dem hier gezeigten unterscheiden. Bearbeiten Sie den Namen nach Bedarf. Es muss nicht unbedingt mit dem Projektnamen der Adobe übereinstimmen.)
   ![JWT6](assets/configure-io-target-jwt6.png)
7. Beachten Sie `CLIENT_SECRET` und `API_KEY` (zusammen mit anderen Variablen) können die Werte vorab ausgefüllt werden, die aus Ihrer Integration gemäß der Definition in der Adobe Developer Console entnommen wurden. (Die `CLIENT_SECRET` Variable &quot;Postman&quot;sollte mit der Berechtigung für die `CLIENT SECRET` Adobe übereinstimmen, wie sie in der Developer Console angezeigt wird, und `API_KEY` in Postman sollte ebenfalls `CLIENT ID` in der Developer Console übereinstimmen.) Beachten Sie hingegen `PRIVATE_KEY`, `JWT_TOKEN`und `ACCESS_TOKEN` sind leer. Beginn, indem wir den `PRIVATE_KEY` Wert angeben.
   ![JWT7](assets/configure-io-target-jwt7.png)

   >[!NOTE]
   >
   >**Überraschung!**
   >
   >Pop Quiz! Kannst du dich erinnern, wo dein privater Schlüssel ist?
   >Das stimmt, es befindet sich in der `config` Datei, die Sie zuvor von der Adobe Developer Console heruntergeladen haben!

8. Öffnen Sie in Ihrem Dateisystem die `config` Datei und öffnen Sie die `private` Schlüsseldatei.
   ![JWT8](assets/configure-io-target-jwt8.png)
9. Wählen Sie den gesamten Inhalt der `private` Schlüsseldatei aus und kopieren Sie ihn.
   ![JWT9](assets/configure-io-target-jwt9.png)
10. Fügen Sie in Postman Ihren privaten Schlüsselwert in die Felder **ERSTE WERTE** und **AKTUELLER WERT** ein.
   ![JWT10](assets/configure-io-target-jwt10.png)
11. Klicken Sie auf **[!UICONTROL Aktualisieren]** und schließen Sie das Modal Umgebung.


## Zugriffstoken des Inhabers erstellen

In diesem Abschnitt generieren Sie Ihr Zugriffstoken für den Inhaber, das zum Authentifizieren Ihrer Interaktion mit Adobe Target-APIs erforderlich ist. Um Ihr Inhaberkonto zu erstellen, müssen Sie Ihre Integrationsdetails (wie in den obigen Abschnitten beschrieben) an den [Adobe Identity Management Service (IMS)](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/AuthenticationOverview/AuthenticationGuide.md)senden. Es gibt einige verschiedene Möglichkeiten, dies zu tun, aber in diesem Tutorial haben wir Sie haben eine maßgeschneiderte POST Anfrage an die IMS API. Nur ein Scherz. In diesem Tutorial nutzen wir eine Postman-Sammlung mit einem vordefinierten IMS-Aufruf, der den Prozess direkt und einfach macht. Nachdem Sie die Sammlung importiert haben, können Sie sie bei Bedarf wiederverwenden, um nicht nur für Adobe Target, sondern auch für andere Adoben-APIs neue Token zu generieren.

1. Navigieren Sie zu den Beispielaufrufen für die Identity Management-Dienst-API der [Adobe](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/ims).
   ![token1](assets/configure-io-target-generatetoken1.png)
2. Klicken Sie auf die **Adobe-E/A-Zugriffstoken-Generierung Postman-Sammlung**.
   ![token2](assets/configure-io-target-generatetoken2.png)
3. Rufen Sie die JSON-Rohdatei für diese Sammlung ab, indem Sie auf **Rohdaten**klicken und dann die JSON-Datei in die Zwischenablage kopieren. (Alternativ können Sie die JSON-Rohdatei als JSON-Datei speichern.)
   ![token3](assets/configure-io-target-generatetoken3.png)
4. Importieren Sie in Postman die Sammlung, indem Sie die JSON-Rohdatei aus der Zwischenablage einfügen und senden. (Alternativ können Sie die gespeicherte JSON-Datei hochladen.) Klicken Sie auf **Weiter**.
   ![token4](assets/configure-io-target-generatetoken4.png)
5. Wählen Sie das **[!UICONTROL IMS aus: JWT Generate + Auth via User Token]** -Anforderung in der Adobe-E/A-Zugriffstoken-Generierung Postman-Sammlung, stellen Sie sicher, dass Ihre Umgebung ausgewählt ist, und klicken Sie auf **Senden** , um das Token zu generieren.

   ![token5](assets/configure-io-target-generatetoken5.png)

   >[!NOTE]
   >
   >Dieses Zugriffstoken ist 24 Stunden gültig. Senden Sie die Anforderung erneut, wenn Sie ein neues Token generieren müssen.

6. Öffnen Sie erneut das Modal Umgebung verwalten und wählen Sie Ihre Umgebung aus.
   ![token6](assets/configure-io-target-jwt11.png)
7. Beachten Sie, dass die Werte `ACCESS_TOKEN` und `JWT_TOKEN` Werte nun ausgefüllt werden.
   ![token7](assets/configure-io-target-generatetoken7.png)

>[!NOTE]
>
>Q: Muss ich die Postman-Sammlung zur Adobe-E/A-Zugriffstoken-Generierung verwenden, um das JSON-Web-Token (JWT) und das Trägersystem zu generieren?
>
>A: Nein! Die Adobe-E/A-Zugriffstoken-Generierung Postman-Kollektion ist als eine einfache Möglichkeit verfügbar, um das JWT und Träger-Zugriffstoken in Postman einfacher zu generieren. Alternativ können Sie die Funktionen in der Adobe Developer Console verwenden, um das Trägersystem manuell zu generieren.

## Zugriffstoken des Inhabers testen

In dieser Übung verwenden Sie Ihr neues Inhaberkonto, indem Sie eine API-Anforderung senden, die eine Liste von Aktivitäten aus Ihrem [!DNL Target] Konto abruft. Eine erfolgreiche Antwort weist darauf hin, dass Ihr Adobe-Projekt und Ihre Authentifizierung wie erwartet funktionieren, um die API zu verwenden.

1. Importieren Sie die [Adobe Target Admin APIs Postman Collection](https://developers.adobetarget.com/api/#admin-postman-collection). Befolgen Sie alle Anweisungen, bis die Sammlung in Postman importiert wird.
   ![testtoken1](assets/configure-io-target-testtoken0.png)
1. Erweitern Sie die Sammlung und beachten Sie die Anforderung der **[!UICONTROL Liste-Aktivitäten]** .
   ![testtoken1](assets/configure-io-target-testtoken1.png)
1. Beachten Sie, dass Variablen wie zum Beispiel `{{access_token}}` zunächst ungelöst sind. Sie können dies auf verschiedene Weise lösen - Sie könnten beispielsweise eine neue Sammlungsvariable mit dem Namen `{{access_token}}`-, aber in diesem Lernprogramm ändern Sie stattdessen die API-Anforderung, um die zuvor verwendete Postman-Umgebung zu nutzen. Auf diese Weise kann die Umgebung weiterhin als eine einheitliche, konsistente Konsolidierung aller Variablen dienen, die in allen Adoben-APIs vorkommen.
   ![testtoken2](assets/configure-io-target-testtoken2.png)
1. Ersetzen `{{access_token}}` durch `{{ACCESS_TOKEN}}`.
   ![testtoken3](assets/configure-io-target-testtoken3.png)
1. Ersetzen `{{api_key}}` durch `{{API_KEY}}`.
   ![testtoken4](assets/configure-io-target-testtoken4.png)
1. Ersetzen `{{tenant}}` durch `{{TENANT_ID}}`. Hinweis `{{TENANT_ID}}` wird noch nicht erkannt.
   ![testtoken4](assets/configure-io-target-testtoken4a.png)
1. Öffnen Sie das Modal Umgebung verwalten und wählen Sie Ihre Umgebung aus.
   ![JWT11](assets/configure-io-target-jwt11.png)
1. Geben Sie ein, um eine neue Variable für die `{{TENANT_ID}}` Umgebung hinzuzufügen. Kopieren Sie den Wert Ihrer Mandant-ID und fügen Sie ihn in die **Felder &quot;WERT** &quot;und &quot; **AKTUELLER WERT** &quot;für Ihre neue Variable &quot; `TENANT_ID` Umgebung&quot;ein.
   ![testtoken5](assets/configure-io-target-testtoken5.png)
   >[!NOTE]
   >
   >Die Mandanten-ID unterscheidet sich von Ihrer [!DNL Target]`clientcode`. Die Mandant-ID befindet sich in der URL, wenn Sie angemeldet sind [!DNL Target]. Um Ihre Mandant-ID zu erhalten, melden Sie sich bei der [!DNL Adobe Experience Cloud], öffnen [!DNL Target]und klicken Sie auf die [!DNL Target] Karte. Verwenden Sie den Wert für die Mandant-ID, der in der URL-Subdomäne angegeben ist.
   >
   >Wenn Ihre URL bei der Anmeldung bei Adobe Target z. B.
   ><https://mycompany.experiencecloud.adobe.com/...>
   >Ihre Mandant-ID lautet &quot;meine Firma&quot;.

1. Senden Sie Ihre Anforderung, nachdem Sie die richtige Umgebung ausgewählt haben. Sie sollten eine Antwort mit Ihrer Liste der Aktivitäten erhalten.
   ![testtoken6](assets/configure-io-target-testtoken6.png)

Herzlichen Glückwunsch! Nachdem Sie die Authentifizierung für die Adobe überprüft haben, können Sie damit mit Adobe Target APIs (sowie anderen Adobe-APIs) interagieren. Beispielsweise können Sie Empfehlungen [mit Recommendations-APIs](https://docs.adobe.com/content/help/en/target-learn/recommendations-api-tutorial/recs-api-overview.html) erstellen oder verwalten.
