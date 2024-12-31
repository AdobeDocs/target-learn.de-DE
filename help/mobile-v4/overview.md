---
title: Adobe Target mit Adobe Mobile Services SDK v4 für Android
description: Adobe Target mit Adobe Mobile Services SDK v4 für Android ist der perfekte Ausgangspunkt für Android-Entwicklerinnen und -Entwickler, die bereits Adobe Mobile Services SDK v4 verwenden und mit der Personalisierung von App-Erlebnissen mit Adobe Target beginnen möchten.
role: Developer
level: Intermediate
topic: Mobile, Personalization
feature: Implement Mobile, Overview
doc-type: tutorial
kt: 3040
exl-id: 20f8ed4f-a86d-4c5e-9296-71a93724caa3
source-git-commit: 342e02562b5296871638c1120114214df6115809
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 2%

---

# Adobe Target mit Adobe Mobile Services SDK v4 für Android - Übersicht

_Adobe Target mit Adobe Mobile Services SDK v4 für Android_ ist der perfekte Ausgangspunkt für Android-Entwicklerinnen und -Entwickler, die bereits Adobe Mobile Services SDK v4 verwenden und mit der Personalisierung von App-Erlebnissen mit Adobe Target beginnen möchten.

Eine Demo-App für Android steht zur Verfügung, um den Unterricht abzuschließen. Nach Abschluss dieses Tutorials sollten Sie bereit sein, [!DNL Target] in Ihrer eigenen Android-App zu implementieren!

Nach diesem Tutorial können Sie Folgendes:

* Überprüfen des SDK-Setups für [Adobe Mobile Services](https://experienceleague.adobe.com/docs/mobile-services/android/getting-started-android/requirements.html?lang=en)
* Implementieren Sie die folgenden Arten von [!DNL Target]:
   * Vorabruf [!DNL Target] Inhalts
   * Mehrere [!DNL Target] (Mboxes) in einer einzigen Anfrage stapeln
   * Blockieren von Anfragen (wird vor der App-Anzeige ausgeführt)
   * Nicht blockierende Anforderungen (wird im Hintergrund ausgeführt)
   * Echtzeit (ohne Caching)
   * Neuabruf von Cache-Busting
* Hinzufügen von Parametern zu Anfragen für eine erweiterte Personalisierung
* Audiences und Angebote erstellen
* Layouts personalisieren
* Einführung neuer Funktionen mit Feature Flagging

## Voraussetzungen 

In diesen Lektionen wird davon ausgegangen, dass Sie:

* Über eine Adobe-ID und Zugriff auf die Benutzeroberfläche von Adobe Target auf der Ebene der genehmigenden Person verfügen (siehe die Verifizierungsschritte unten)
* Kennen Sie Ihren Adobe Target-Client-Code, damit Sie Anfragen an Ihr eigenes Konto senden können. Der Client-Code wird in der Adobe Target-Benutzeroberfläche auf der   Setup > Implementierung > Bildschirm „at.js-Einstellungen bearbeiten“
* Zugriff auf die Benutzeroberfläche von [Mobile Services“ und damit vertraut ](https://mobilemarketing.adobe.com/)
* Eine IDE für die Entwicklung von Android Mobile Apps haben. Dieses Tutorial bietet [Android Studio](https://developer.android.com/studio/install) in verschiedenen Schritten und Screenshots

Wenn Sie nicht den erforderlichen Zugriff auf die Experience Cloud-Lösungen haben, wenden Sie sich an Ihren Experience Cloud-Administrator.

Es wird außerdem davon ausgegangen, dass Sie mit der Android-Entwicklung in Java vertraut sind. Sie müssen kein Java-Experte sein, um die Lektionen zu vervollständigen, aber Sie werden mehr aus ihnen erhalten, wenn Sie Code bequem lesen und verstehen können.

### Überprüfen des Zugriffs auf Adobe Target

Diese Lektion erfordert Zugriff auf Adobe Target. Bevor Sie mit den nächsten Schritten fortfahren, stellen Sie sicher, dass Sie Zugriff auf Adobe Target haben, indem Sie Folgendes durchführen:

1. Melden Sie sich bei der [Adobe Experience Cloud ](https://experience.adobe.com/)
1. Klicken Sie auf dem Experience Cloud-Startbildschirm auf [!DNL Target]:
   ![Experience Cloud-Startbildschirm](assets/aec_homeScreen_clickTarget.png)
1. Sie sollten zur Aktivitätenliste in Adobe Target gelangen, wie unten dargestellt, und sehen, dass Ihre Benutzerin bzw. Ihr Benutzer Zugriff auf die Ebene einer genehmigenden Person hat. Wenn Sie nicht auf [!DNL Target] zugreifen oder den Zugriff auf der Ebene der genehmigenden Person nicht überprüfen können, wenden Sie sich an einen Experience Cloud-Administrator Ihrer Firma, fordern Sie diesen Zugriff an und setzen Sie das Tutorial fort, sobald ihm der Zugriff gewährt wurde:

   ![Adobe-Benutzeroberfläche](assets/targetUI_approver.png)

## Über die Lektionen

In diesen Lektionen implementieren Sie Adobe Target in eine Demo-Reise-App namens „We.Travel“ mit Ihrem eigenen Adobe Target-Konto. Am Ende des Tutorials werden Sie den Benutzenden personalisierte Nachrichten auf Grundlage ihrer Nutzung der App senden! Die endgültigen Personalisierungserlebnisse werden wie folgt aussehen:

![We.Travel App endgültig](assets/overview_final_result.jpg)

Nachdem Sie sich mit der Implementierung in der We.Travel-App vertraut gemacht haben, können Sie [!DNL Target] in Ihrer eigenen Mobile App verwenden.

Fangen wir an!

**[WEITER : „Beispielanwendung herunterladen und aktualisieren“ >](download-and-update-the-sample-app.md)**
