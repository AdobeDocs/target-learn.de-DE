---
title: Adobe Target mit Adobe Mobile Services SDK v4 für Android
description: Adobe Target mit Adobe Mobile Services SDK v4 für Android ist der perfekte Ausgangspunkt für Android-Entwickler, die bereits Adobe Mobile Services SDK v4 verwenden und mit Adobe Target App-Erlebnisse personalisieren möchten.
feature: mobile
kt: 3040
audience: developer
doc-type: tutorial
activity-type: implement
translation-type: tm+mt
source-git-commit: d6cedd55dcc9c08d2d2ca5709e15fe5ea9fab8b8
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 2%

---


# Adobe Target mit Adobe Mobile Services SDK v4 für Android - Übersicht

_Adobe Target mit der Adobe Mobile Services SDK v4 für_ Androidis ist der perfekte Ausgangspunkt für Android-Entwickler, die bereits Adobe Mobile Services SDK v4 verwenden und mit Adobe Target App-Erlebnisse personalisieren möchten.

Zum Abschließen des Unterrichts steht eine Demo-Android-App zur Verfügung. Nach Abschluss dieses Lernprogramms sollten Sie bereit sein, mit der Implementierung von [!DNL Target] in Ihrer eigenen Android-App Beginn zu machen!

Nach diesem Tutorial können Sie Folgendes:

* Validieren Sie das Setup für das [Adobe Mobile Services SDK](https://docs.adobe.com/content/help/en/mobile-services/android/getting-started-android/requirements.html)
* Implementieren Sie die folgenden Typen von [!DNL Target]-Anforderungen:
   * Vorab-Abrufen von [!DNL Target]-Inhalten
   * Stapelverarbeitung mehrerer [!DNL Target]-Orte (Mboxes) in einer einzelnen Anforderung
   * Blockieren von Anforderungen (wird vor der App-Anzeige ausgeführt)
   * Nicht blockierende Anforderungen (wird im Hintergrund ausgeführt)
   * Echtzeit (nicht zwischenspeichern)
   * Cache-Busting-Wiederherstellung
* hinzufügen von Parametern für Anforderungen zur erweiterten Personalisierung
* Audiencen und Angebote erstellen
* Layouts personalisieren
* Rollout neuer Funktionen mit Kennzeichnung der Funktionen

## Voraussetzungen 

In diesen Lektionen wird davon ausgegangen, dass Sie:

* Sie haben eine Adoben-ID und Zugriff auf die Adobe Target-Benutzeroberfläche auf der Genehmigungsebene (siehe die unten stehenden Überprüfungsschritte).
* Machen Sie sich mit Ihrem Adobe Target Client-Code vertraut, damit Sie Anfragen an Ihr eigenes Konto richten können. Der Clientcode wird auf der Adobe Target-Oberfläche auf der   Einstellungen > Implementierung > Bildschirm &quot;at.js-Einstellungen bearbeiten&quot;
* Zugriff auf die [Mobile Services-Benutzeroberfläche ](https://mobilemarketing.adobe.com) haben und mit ihr vertraut sind
* Verwenden Sie eine IDE für die Entwicklung mobiler Apps für Android. Dieses Lernprogramm enthält [Android Studio](https://developer.android.com/studio/install) in verschiedenen Schritten und Screenshots

Wenn Sie nicht über den erforderlichen Zugriff auf die Experience Cloud-Lösungen verfügen, wenden Sie sich an Ihren Experience Cloud-Administrator.

Außerdem wird davon ausgegangen, dass Sie mit der Android-Entwicklung in Java vertraut sind. Sie müssen kein Java-Experte sein, um die Lektionen abzuschließen, aber Sie werden mehr davon bekommen, wenn Sie problemlos Code lesen und verstehen können.

### Zugriff auf Adobe Target überprüfen

Diese Lektion erfordert Zugriff auf Adobe Target. Bevor Sie die nächsten Schritte durchführen, stellen Sie sicher, dass Sie Zugriff auf Adobe Target haben, indem Sie folgende Schritte ausführen:

1. Melden Sie sich bei [Adobe Experience Cloud](https://experience.adobe.com/) an
1. Klicken Sie auf dem Startbildschirm des Experience Cloud auf [!DNL Target]:
   ![Startbildschirm des Experience Cloud](assets/aec_homeScreen_clickTarget.png)
1. Sie sollten zur Liste &quot;Aktivitäten&quot;in Adobe Target gelangen, wie unten dargestellt, und Sie sollten sehen, dass Ihr Benutzer Zugriff auf der Stufe &quot;Genehmigende Person&quot;hat. Wenn Sie nicht auf [!DNL Target] zugreifen können oder den Zugriff auf der Ebene der genehmigenden Person nicht überprüfen können, wenden Sie sich an einen der Experience Cloud-Administratoren Ihrer Firma, fordern Sie diesen Zugriff an und nehmen Sie dieses Lernprogramm nach Erteilung wieder auf:

   ![Benutzeroberfläche der Adobe](assets/targetUI_approver.png)

## Die Lehren

In diesen Lektionen implementieren Sie Adobe Target mit Ihrem eigenen Adobe Target-Konto in eine Demoanwendung mit dem Namen &quot;We.Travel&quot;. Am Ende des Lernprogramms senden Sie dem Benutzer personalisierte Nachrichten basierend auf der Nutzung der App! Die endgültige Personalisierung sieht wie folgt aus:

![We.Travel-App endgültig](assets/overview_final_result.jpg)

Nachdem Sie die Implementierung in der App &quot;We.Travel&quot;durchlaufen haben, können Sie mit [!DNL Target] in Ihrer eigenen mobilen App Beginn ausführen.

Fangen wir an!

**[NÄCHSTES: &quot;Download und Aktualisierung der Beispielanwendung&quot;>](download-and-update-the-sample-app.md)**
