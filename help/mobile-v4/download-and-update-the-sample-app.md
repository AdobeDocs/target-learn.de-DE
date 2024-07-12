---
title: Herunterladen und Aktualisieren der Beispiel-App "We.Travel"
description: Die Beispielanwendung "We.Travel"ist mit dem Adobe Mobile Services SDK v4 vorimplementiert. Sie müssen es nur aktualisieren, damit es auf Ihre eigenen Experience Cloud-Org- und Lösungskonten verweist.
role: Developer
level: Intermediate
topic: Mobile, Personalization
feature: Implement Mobile
doc-type: tutorial
kt: 3040
exl-id: 244bcf7a-b59b-4dd1-bd05-0a55ce7a7132
source-git-commit: 342e02562b5296871638c1120114214df6115809
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# Herunterladen und Aktualisieren der Beispiel-App &quot;We.Travel&quot;

Die Beispielanwendung &quot;We.Travel&quot;ist mit dem Adobe Mobile Services SDK v4 vorimplementiert. Sie müssen es nur aktualisieren, sodass es auf Ihre eigenen Experience Cloud-Org- und Lösungskonten verweist.

## Lernziele

Am Ende dieser Lektion können Sie:

* Laden Sie die Beispielanwendung We.Travel herunter und öffnen Sie sie in Android Studio
* Mobile Services SDK-Einstellungen für [!DNL Target] überprüfen und aktualisieren

## Herunterladen der We.Travel-App

* Laden Sie die Datei [sample-app-android-SDKv4-base-Version.zip](assets/sample-app-android-SDKv4-Base-Version.zip) herunter.
* Dekomprimieren Sie die ZIP-Datei
* Öffnen Sie die App in Android Studio als vorhandenes Projekt (ignorieren Sie alle Fehler bezüglich &quot;Ungültiges VCS-Root-Mapping&quot;).
* Führen Sie die App in einem Emulator aus, um zu überprüfen, ob die App erstellt wurde und Sie den Startbildschirm sehen können.
* Durchsuchen Sie die App und vergewissern Sie sich, dass Sie den Buchungsvorgang abschließen können (wählen Sie eine beliebige Zahlungsoption aus und klicken Sie einfach auf &quot;Fortfahren&quot;, um den Abrechnungsbildschirm zu überspringen!)

  ![Öffnen Sie die App](assets/wetravel_homeScreen.png)![Bestätigungsbildschirm](assets/wetravel_confirmationScreen.png)

## Mobile Services SDK-Einstellungen für [!DNL Target] überprüfen und aktualisieren

Das Adobe Mobile Services SDK wurde in der We.Travel-App [gemäß der Dokumentation vorinstalliert](https://experienceleague.adobe.com/docs/mobile-services/android/getting-started-android/requirements.html?lang=en). Jetzt aktualisieren Sie die Installation, um auf Ihr eigenes [!DNL Target] -Konto zu verweisen.

Erstellen Sie zunächst eine neue App in der Mobile Services-Benutzeroberfläche:

1. Melden Sie sich bei der [Adobe Mobile Services-Benutzeroberfläche](https://mobilemarketing.adobe.com/) an.
1. Wechseln Sie zu &quot;[!UICONTROL Manage Apps]&quot;und klicken Sie dann auf &quot;**[!UICONTROL Add]**&quot;, um eine neue App hinzuzufügen, die mit diesem Tutorial (**[!UICONTROL Manage Apps]** > **[!UICONTROL Add]**) verwendet werden soll.
1. Wählen Sie eine Analytics Report Suite ohne Produktionsdaten aus, geben Sie der App einen Namen, wählen Sie den Typ **[!UICONTROL Standard]** und klicken Sie auf **[!UICONTROL Save]**.
1. Nachdem die App hinzugefügt wurde, fügen Sie Ihren [!DNL Target] Client-Code auf dem nächsten Bildschirm im Abschnitt [!UICONTROL SDK Target Options] hinzu (Sie finden Ihren Client-Code in der [!DNL Target] -Benutzeroberfläche unter **[!UICONTROL Setup]** > **[!UICONTROL Implementation]** > **[!UICONTROL Edit Settings]** neben der Schaltfläche &quot;Download `at.js`&quot;).
1. Die Einstellung [!UICONTROL Request Timeout] bestimmt, wie lange die App auf die Antwort vom [!DNL Target] -Server wartet, bevor Zeitüberschreitungsanweisungen ausgeführt werden. Behalten Sie einfach die Standardeinstellung bei.
1. Aktivieren Sie den [!UICONTROL Visitor ID Service] und stellen Sie sicher, dass Ihr [!UICONTROL Organization] in der Dropdown-Liste ausgewählt ist.
1. Speichern Sie Ihre Änderungen, indem Sie oben rechts im Fenster auf **[!UICONTROL Save]** klicken (nicht auf die im Abschnitt [!UICONTROL Universal Links], [!UICONTROL App Links] oder [!UICONTROL Push Services]).
1. Scrollen Sie zum Abschnitt App SDK-Downloads am unteren Rand der Seite und laden Sie die Konfigurationsdatei herunter:

   ![Laden Sie die Konfigurationsdatei herunter](assets/config_file.jpg)

1. Ersetzen Sie die Datei &quot;`ADBMobileConfig.json`&quot;im Ordner mit den Android Studio-Projekt-Assets (App > src > main > assets).

1. Öffnen Sie nun die Datei `ADBMobileConfig.json` und stellen Sie sicher, dass sie die erwarteten Änderungen enthält, wie Ihren [!DNL Target] Client-Code und Ihre Analytics-Details:
   ![Laden Sie die Konfigurationsdatei herunter](assets/client_code.jpg)

Wenn Ihre Einstellungen nicht angezeigt werden, vergewissern Sie sich, dass Sie in der Benutzeroberfläche von [!UICONTROL Mobile Services] auf die rechte Schaltfläche **[!UICONTROL Save]** geklickt und die Datei an den richtigen Speicherort kopiert haben.

Herzlichen Glückwunsch! Sie haben das SDK mit Ihren [!DNL Target] Kontodetails aktualisiert! Wir führen eine zusätzliche Validierung der Konfiguration durch, nachdem wir in der nächsten Lektion [!DNL Target] -Anforderungen hinzugefügt haben.

**[NEXT : &quot;Target-Anforderungen hinzufügen&quot;>](add-requests.md)**
