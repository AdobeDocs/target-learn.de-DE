---
title: Herunterladen und Aktualisieren der Web.Travel-Beispielanwendung
seo-title: Laden Sie die Beispielanwendung herunter und überprüfen Sie das SDK für mobile Dienste
description: 'Die Beispiel-App "We.Travel"ist mit dem Adobe Mobile Services SDK v4 vorimplementiert. Sie müssen es nur aktualisieren, damit es auf Ihre eigenen Experience Cloud-Organisations- und Lösungskonten verweist.   '
seo-description: Die Beispiel-App "We.Travel"ist mit dem Adobe Mobile Services SDK v4 vorimplementiert. Sie müssen es nur aktualisieren, damit es auf Ihre eigenen Experience Cloud-Organisations- und Lösungskonten verweist.
feature: mobile
kt: 3040
audience: developer
doc-type: tutorial
activity-type: implement
translation-type: tm+mt
source-git-commit: b331bb29c099bd91df27300ebe199cafa12516db
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 0%

---


# Herunterladen und Aktualisieren der Web.Travel-Beispielanwendung

Die Beispiel-App &quot;We.Travel&quot;ist mit dem Adobe Mobile Services SDK v4 vorimplementiert. Sie müssen es nur aktualisieren, damit es auf Ihre eigenen Experience Cloud-Organisations- und Lösungskonten verweist.

## Lernziele

Am Ende dieser Lektion können Sie:

* Laden Sie die Beispiel-App &quot;We.Travel&quot;herunter und öffnen Sie sie in Android Studio
* SDK-Einstellungen für Mobile Services überprüfen und aktualisieren für [!DNL Target]

## Laden Sie die App &quot;We.Travel&quot;herunter

* Laden Sie [sample-app-android-SDKv4-Base-Version.zip herunter](assets/sample-app-android-SDKv4-Base-Version.zip)
* Dekomprimieren der ZIP-Datei
* Öffnen Sie die App in Android Studio als vorhandenes Projekt (ignorieren Sie alle Fehler zu &quot;Ungültige VCS-Stammzuordnung&quot;)
* Führen Sie die App in einem Emulator aus, um zu bestätigen, dass die App erstellt wurde, und Sie können den Startbildschirm sehen
* Durchsuchen Sie die App und überprüfen Sie, ob Sie den Buchungsprozess abschließen können (wählen Sie eine beliebige Zahlungsoption aus und klicken Sie auf &quot;Weiter&quot;, um den Abrechnungsbildschirm zu überspringen!)

   ![Öffnen Sie den](assets/wetravel_homeScreen.png)![Bildschirm &quot;appConfirmation&quot;](assets/wetravel_confirmationScreen.png)

## SDK-Einstellungen für Mobile Services überprüfen und aktualisieren für [!DNL Target]

Das Adobe Mobile Services SDK wurde [gemäß der Dokumentation](https://docs.adobe.com/content/help/en/mobile-services/android/getting-started-android/requirements.html)vorinstalliert. Jetzt werden Sie die Installation so aktualisieren, dass sie auf Ihr eigenes [!DNL Target] Konto verweist.

Erstellen Sie zunächst eine neue App in der Mobile Services-Benutzeroberfläche:

1. Log in to the [Adobe Mobile Services interface](https://mobilemarketing.adobe.com).
1. Rufen Sie die Seite &quot; [!UICONTROL Apps]verwalten&quot;auf und klicken Sie dann auf **[!UICONTROL Hinzufügen]** , um eine neue App hinzuzufügen, die Sie in diesem Lernprogramm verwenden können (**[!UICONTROL Apps]** verwalten > **[!UICONTROL Hinzufügen]**).
1. Wählen Sie eine Analytics-Report Suite mit Nicht-Produktionsdaten aus, geben Sie der App einen Namen, wählen Sie den **[!UICONTROL Standard]** -Typ und klicken Sie auf **[!UICONTROL Speichern]**.
1. Nachdem die App hinzugefügt wurde, fügen Sie Ihren [!DNL Target] Clientcode im nächsten Bildschirm im Abschnitt [!UICONTROL SDK-Target-Optionen] hinzu (Sie finden Ihren Clientcode auf der [!DNL Target] Benutzeroberfläche unter **[!UICONTROL Einstellungen]** > **[!UICONTROL Implementierung]** > Einstellungen **[!UICONTROL bearbeiten]**`at.js` neben der Schaltfläche Herunterladen).
1. Die Einstellung [!UICONTROL Anforderungs-Timeout] bestimmt, wie lange die App auf die Antwort vom [!DNL Target] Server wartet, bevor Zeitüberschreitungsanweisungen ausgeführt werden. Belassen Sie einfach die Standardeinstellung.
1. Aktivieren Sie den [!UICONTROL Besucher-ID-Dienst] und vergewissern Sie sich, dass in der Dropdown-Liste Ihre [!UICONTROL Organisation] ausgewählt ist.
1. Speichern Sie Ihre Änderungen, indem Sie oben rechts im Fenster auf **[!UICONTROL Speichern]** klicken (nicht im Abschnitt [!UICONTROL Universelle Links], [!UICONTROL App-Links] oder [!UICONTROL Push-Dienste] ).
1. Blättern Sie unten auf der Seite zum Abschnitt App SDK-Downloads und laden Sie die Konfigurationsdatei herunter:

   ![Konfigurationsdatei herunterladen](assets/config_file.jpg)

1. Ersetzen Sie die `ADBMobileConfig.json` Datei im Asset-Ordner Ihres Android-Studio-Projekts (App > src > main > assets).

1. Öffnen Sie jetzt die `ADBMobileConfig.json` Datei und stellen Sie sicher, dass sie die erwarteten Änderungen enthält, wie Ihren [!DNL Target] Clientcode und Ihre Analytics-Details:
   ![Konfigurationsdatei herunterladen](assets/client_code.jpg)

Wenn Ihre Einstellungen nicht angezeigt werden, vergewissern Sie sich, dass Sie auf der Benutzeroberfläche von **[!UICONTROL Mobile Services]** auf die rechte Schaltfläche &quot; [!UICONTROL Speichern] &quot;geklickt und die Datei an den richtigen Speicherort kopiert haben.

Herzlichen Glückwunsch! Sie haben das SDK mit Ihren [!DNL Target] Kontodetails aktualisiert! Wir führen eine zusätzliche Validierung der Konfiguration durch, nachdem wir in der nächsten Lektion [!DNL Target] Anforderungen hinzugefügt haben.

**[NÄCHSTES: &quot;Hinzufügen Target-Anfragen&quot;>](add-requests.md)**
