---
title: Adobe Target mit Adobe Mobile Services SDK v4 für Android
description: Adobe Target mit Adobe Mobile Services SDK v4 für Android ist der perfekte Ausgangspunkt für Android-Entwickler, die bereits Adobe Mobile Services SDK v4 verwenden und mit Adobe Target personalisierte App-Erlebnisse erstellen möchten.
feature: mobile
kt: 3040
audience: developer
doc-type: tutorial
activity-type: implement
translation-type: tm+mt
source-git-commit: b331bb29c099bd91df27300ebe199cafa12516db
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 2%

---


# Überblick

_Adobe Target mit Adobe Mobile Services SDK v4 für Android_ ist der perfekte Ausgangspunkt für Android-Entwickler, die bereits Adobe Mobile Services SDK v4 verwenden und mit Adobe Target personalisierte App-Erlebnisse erstellen möchten.

Zum Abschließen des Unterrichts steht eine Demo-Android-App zur Verfügung. Nach Abschluss dieses Lernprogramms sollten Sie bereit sein, Beginn zur Implementierung [!DNL Target] in Ihrer eigenen Android-App auszuführen!

Nach diesem Tutorial können Sie Folgendes:

* Überprüfen der [Adobe Mobile Services SDK](https://docs.adobe.com/content/help/en/mobile-services/android/getting-started-android/requirements.html) -Einrichtung
* Implementieren Sie die folgenden Typen von [!DNL Target] Anforderungen:
   * Vorab-Abrufen von [!DNL Target] Inhalten
   * Stapelung mehrerer [!DNL Target] Orte (Mboxes) in einer einzelnen Anforderung
   * Blockieren von Anforderungen (wird vor der App-Anzeige ausgeführt)
   * Nicht blockierende Anforderungen (wird im Hintergrund ausgeführt)
   * Echtzeit (nicht zwischenspeichern)
   * Cache-Busting-Wiederherstellung
* Hinzufügen von Parametern für Anforderungen zur erweiterten Personalisierung
* Audiencen und Angebote erstellen
* Layouts personalisieren
* Rollout neuer Funktionen mit Kennzeichnung der Funktionen

## Voraussetzungen 

In diesen Lektionen wird davon ausgegangen, dass Sie:

* Zugriff auf die Benutzeroberfläche des Adobe Targets auf Adobe ID- und Genehmiger-Ebene haben (siehe die unten stehenden Überprüfungsschritte)
* Kennen Sie Ihren Adobe Target-Client-Code, damit Sie Anfragen an Ihr eigenes Konto richten können. Der Clientcode wird auf der Benutzeroberfläche &quot;Adobe Target&quot;im Bildschirm &quot;Einstellungen&quot;> &quot;Implementierung&quot;> &quot;at.js-Einstellungen bearbeiten&quot;angezeigt
* Zugriff auf die [Mobile Services-Benutzeroberfläche haben und mit ihr vertraut sind](https://mobilemarketing.adobe.com)
* Verwenden Sie eine IDE für die Entwicklung mobiler Apps für Android. Diese Übung umfasst [Android Studio](https://developer.android.com/studio/install) in verschiedenen Schritten und Screenshots

Wenn Sie nicht über den erforderlichen Zugriff auf die Experience Cloud-Lösungen verfügen, wenden Sie sich an Ihren Experience Cloud-Administrator.

Außerdem wird davon ausgegangen, dass Sie mit der Android-Entwicklung in Java vertraut sind. Sie müssen kein Java-Experte sein, um die Lektionen abzuschließen, aber Sie werden mehr davon bekommen, wenn Sie problemlos Code lesen und verstehen können.

### Zugriff auf Adobe Target überprüfen

Diese Lektion erfordert Zugriff auf Adobe Target. Bevor Sie die nächsten Schritte ausführen, stellen Sie sicher, dass Sie Zugriff auf Adobe Target haben, indem Sie folgende Schritte ausführen:

1. Bei der [Adobe Experience Cloud anmelden](https://experience.adobe.com/)
1. From the Experience Cloud home screen, click [!DNL Target]:
   ![Startbildschirm des Experience Cloud](assets/aec_homeScreen_clickTarget.png)
1. Sie sollten die Liste &quot;Aktivitäten&quot;in Adobe Target aufrufen, wie unten dargestellt, und Sie sollten sehen, dass Ihr Benutzer Zugriff auf der Stufe &quot;Genehmigende Person&quot;hat. Wenn Sie den Zugriff auf der Ebene der genehmigenden Person nicht aufrufen können [!DNL Target] oder diesen nicht überprüfen können, wenden Sie sich an einen der Experience Cloud-Administratoren Ihrer Firma, fordern Sie diesen Zugriff an und nehmen Sie dieses Lernprogramm wieder auf, sobald es erteilt wurde:

   ![Adobe-Benutzeroberfläche](assets/targetUI_approver.png)

## Die Lehren

In diesen Lektionen implementieren Sie Adobe Target mit Ihrem eigenen Adobe Target-Konto in eine Demo-Reise-App namens &quot;We.Travel&quot;. Am Ende des Lernprogramms senden Sie dem Benutzer personalisierte Nachrichten basierend auf der Nutzung der App! Die endgültige Personalisierung sieht wie folgt aus:

![We.Travel-App endgültig](assets/overview_final_result.jpg)

Nachdem Sie die Implementierung innerhalb der App &quot;We.Travel&quot;durchlaufen haben, können Sie mit Ihrer [!DNL Target] eigenen mobilen App Beginn erstellen.

Fangen wir an!

**[NÄCHSTES: &quot;Download und Aktualisierung der Beispielanwendung&quot;>](download-and-update-the-sample-app.md)**
