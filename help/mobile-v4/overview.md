---
title: Adobe Target mit Adobe Mobile Services SDK v4 für Android
description: Adobe Target mit Adobe Mobile Services SDK v4 für Android ist der perfekte Ausgangspunkt für Android-Entwickler, die bereits das Adobe Mobile Services SDK v4 verwenden und mit Adobe Target App-Erlebnisse personalisieren möchten.
role: Developer
level: Intermediate
topic: Mobile, Personalization
feature: Implement Mobile, Overview
doc-type: tutorial
kt: 3040
exl-id: 20f8ed4f-a86d-4c5e-9296-71a93724caa3
source-git-commit: 342e02562b5296871638c1120114214df6115809
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 2%

---

# Adobe Target mit Adobe Mobile Services SDK v4 für Android - Übersicht

_Adobe Target mit Adobe Mobile Services SDK v4 für_ Android ist der perfekte Ausgangspunkt für Android-Entwickler, die bereits das Adobe Mobile Services SDK v4 verwenden und mit Adobe Target App-Erlebnisse personalisieren möchten.

Zum Abschluss der Lektionen erhalten Sie eine Android-Demo-App. Nach Abschluss dieses Tutorials sollten Sie bereit sein, mit der Implementierung von [!DNL Target] in Ihrer eigenen Android-App zu beginnen!

Nach diesem Tutorial können Sie Folgendes:

* Validieren der Einrichtung des [Adobe Mobile Services SDK](https://experienceleague.adobe.com/docs/mobile-services/android/getting-started-android/requirements.html?lang=en)
* Implementieren Sie die folgenden Typen von [!DNL Target] -Anforderungen:
   * Vorabruf des Inhalts von [!DNL Target]
   * Mehrere [!DNL Target]-Orte (Mboxes) in einer einzelnen Anforderung stapeln
   * Sperren von Anforderungen (wird vor der App-Anzeige ausgeführt)
   * Nicht blockierende Anforderungen (läuft im Hintergrund)
   * Echtzeit (Nicht-Caching)
   * Cache-Busting-Neuabruf
* Parameter zu Anforderungen für eine verbesserte Personalisierung hinzufügen
* Erstellen von Zielgruppen und Angeboten
* Layouts personalisieren
* Rollout neuer Funktionen mit Funktionskennzeichnung

## Voraussetzungen 

In diesen Lektionen wird davon ausgegangen, dass Sie:

* Sie benötigen eine Adoben-ID und Zugriff auf die Benutzeroberfläche von Adobe Target auf Genehmigungsebene (siehe die Überprüfungsschritte unten).
* Sie kennen Ihren Adobe Target-Clientcode, damit Sie Anforderungen an Ihr eigenes Konto senden können. Der Clientcode wird in der Adobe Target-Benutzeroberfläche auf der   Setup > Implementierung > Bildschirm &quot;at.js-Einstellungen bearbeiten&quot;
* Sie haben Zugriff auf die [Mobile Services-Benutzeroberfläche](https://mobilemarketing.adobe.com/) und kennen diese.
* Verwenden Sie eine IDE für die Entwicklung mobiler Android-Apps. Dieses Tutorial beinhaltet [Android Studio](https://developer.android.com/studio/install) in verschiedenen Schritten und Screenshots

Wenn Sie nicht den erforderlichen Zugriff auf die Experience Cloud-Lösungen haben, wenden Sie sich an Ihren Experience Cloud-Administrator.

Außerdem wird davon ausgegangen, dass Sie mit der Android-Entwicklung in Java vertraut sind. Sie müssen kein Java-Experte sein, um die Lektionen abzuschließen, aber Sie werden mehr daraus lernen, wenn Sie Code bequem lesen und verstehen können.

### Zugriff auf Adobe Target überprüfen

Diese Lektion erfordert Zugriff auf Adobe Target. Bevor Sie mit den nächsten Schritten fortfahren, müssen Sie wie folgt auf Adobe Target zugreifen:

1. Melden Sie sich bei [Adobe Experience Cloud](https://experience.adobe.com/) an.
1. Klicken Sie auf der Startseite des Experience Cloud auf [!DNL Target]:
   ![Startbildschirm des Experience Cloud](assets/aec_homeScreen_clickTarget.png)
1. Sie sollten zur Aktivitätenliste in Adobe Target gelangen, wie unten dargestellt, und Sie sollten sehen, dass Ihr Benutzer Zugriff auf Genehmigerebene hat. Wenn Sie nicht auf [!DNL Target] zugreifen können oder den Zugriff auf der Ebene der Genehmiger nicht überprüfen können, wenden Sie sich an einen der Experience Cloud-Administratoren Ihres Unternehmens, fordern Sie diesen Zugriff an und nehmen Sie dieses Tutorial wieder auf, sobald es gewährt wurde:

   ![Adobe-Benutzeroberfläche](assets/targetUI_approver.png)

## Über die Lektionen

In diesen Lektionen implementieren Sie Adobe Target mithilfe Ihres eigenen Adobe Target-Kontos in eine Demo-Reiseanwendung mit dem Namen &quot;We.Travel&quot;. Am Ende des Tutorials senden Sie dem Benutzer personalisierte Nachrichten basierend auf seiner Nutzung der App! Die endgültigen Personalisierungserlebnisse sehen wie folgt aus:

![We.Travel app final](assets/overview_final_result.jpg)

Nachdem Sie die Implementierung innerhalb der We.Travel-App durchlaufen haben, können Sie [!DNL Target] in Ihrer eigenen App verwenden.

Fangen wir an!

**[NÄCHSTES : &quot;Download und Aktualisierung der Beispielanwendung&quot;>](download-and-update-the-sample-app.md)**
