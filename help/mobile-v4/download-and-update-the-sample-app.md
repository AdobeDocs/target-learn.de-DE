---
title: Herunterladen und Aktualisieren der Web.Travel-Beispielanwendung
description: 'Die Beispiel-App "We.Travel"ist mit dem Adobe Mobile Services SDK v4 vorimplementiert. Sie müssen es nur aktualisieren, damit es auf Ihre eigenen Experience Cloud-Organisations- und Lösungskonten verweist.   '
role: Entwickler
level: Zwischenschaltung
topic: Mobil, Personalisierung
feature: Mobile implementieren
doc-type: tutorial
kt: 3040
thumbnail: null
translation-type: tm+mt
source-git-commit: b89732fcca0be8bffc6e580e4ae0e62df3c3655d
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---


# Herunterladen und Aktualisieren der Web.Travel-Beispielanwendung

Die Beispiel-App &quot;We.Travel&quot;ist mit dem Adobe Mobile Services SDK v4 vorimplementiert. Sie müssen es nur aktualisieren, damit es auf Ihre eigenen Experience Cloud-Organisations- und Lösungskonten verweist.

## Lernziele

Am Ende dieser Lektion können Sie:

* Laden Sie die Beispiel-App &quot;We.Travel&quot;herunter und öffnen Sie sie in Android Studio
* Überprüfen und Aktualisieren der Mobile Services SDK-Einstellungen für [!DNL Target]

## Laden Sie die App &quot;We.Travel&quot;herunter

* Laden Sie die Datei [sample-app-android-SDKv4-Base-Version.zip](assets/sample-app-android-SDKv4-Base-Version.zip) herunter.
* Dekomprimieren der ZIP-Datei
* Öffnen Sie die App in Android Studio als vorhandenes Projekt (ignorieren Sie alle Fehler zu &quot;Ungültige VCS-Stammzuordnung&quot;)
* Führen Sie die App in einem Emulator aus, um zu bestätigen, dass die App erstellt wurde, und Sie können den Startbildschirm sehen
* Durchsuchen Sie die App und überprüfen Sie, ob Sie den Buchungsprozess abschließen können (wählen Sie eine beliebige Zahlungsoption aus und klicken Sie auf &quot;Weiter&quot;, um den Abrechnungsbildschirm zu überspringen!)

   ![Öffnen Sie den ](assets/wetravel_homeScreen.png)![Bildschirm &quot;appConfirmation&quot;](assets/wetravel_confirmationScreen.png)

## Überprüfen und Aktualisieren der Mobile Services SDK-Einstellungen für [!DNL Target]

Das Adobe Mobile Services SDK wurde in der Web.Travel-App [gemäß der Dokumentation ](https://docs.adobe.com/content/help/en/mobile-services/android/getting-started-android/requirements.html) vorinstalliert. Jetzt werden Sie die Installation aktualisieren, um auf Ihr eigenes [!DNL Target]-Konto zu verweisen.

Erstellen Sie zunächst eine neue App in der Mobile Services-Benutzeroberfläche:

1. Melden Sie sich bei der [Adobe Mobile Services-Schnittstelle](https://mobilemarketing.adobe.com) an.
1. Wechseln Sie zu [!UICONTROL Apps verwalten] und klicken Sie dann auf **[!UICONTROL Hinzufügen]**, um eine neue App hinzuzufügen, die mit diesem Lernprogramm verwendet werden soll (**[!UICONTROL Apps verwalten]** > **[!UICONTROL Hinzufügen]**).
1. Wählen Sie eine Analytics-Report Suite mit Nicht-Produktionsdaten, geben Sie der App einen Namen, wählen Sie den Typ **[!UICONTROL Standard]** und klicken Sie auf **[!UICONTROL Speichern]**.
1. Nachdem die App hinzugefügt wurde, fügen Sie im nächsten Bildschirm im Bereich [!UICONTROL SDK-Zielgruppe-Optionen] Ihren [!DNL Target]-Clientcode hinzu (Sie finden Ihren Clientcode in der [!DNL Target]-Schnittstelle unter **[!UICONTROL Setup]** > **[!UICONTROL Implementierung]** > **[!UICONTROL Einstellungen bearbeiten]** neben dem Download `at.js` 0/>).
1. Die Einstellung [!UICONTROL Anforderungs-Timeout] bestimmt, wie lange die App auf die Antwort vom [!DNL Target]-Server wartet, bevor Zeitüberschreitungsanweisungen ausgeführt werden. Belassen Sie einfach die Standardeinstellung.
1. Aktivieren Sie den [!UICONTROL Besucher-ID-Dienst] und stellen Sie sicher, dass [!UICONTROL Unternehmen] in der Dropdown-Liste ausgewählt ist.
1. Speichern Sie Ihre Änderungen, indem Sie auf **[!UICONTROL Speichern]** oben rechts im Fenster klicken (nicht auf die Optionen [!UICONTROL Universelle Links], [!UICONTROL App-Links] oder [!UICONTROL Push-Dienste]).
1. Blättern Sie unten auf der Seite zum Abschnitt App SDK-Downloads und laden Sie die Konfigurationsdatei herunter:

   ![Konfigurationsdatei herunterladen](assets/config_file.jpg)

1. Ersetzen Sie die Datei `ADBMobileConfig.json` im Asset-Ordner Ihres Android-Studio-Projekts (App > src > main > assets).

1. Öffnen Sie nun die Datei `ADBMobileConfig.json` und stellen Sie sicher, dass sie die erwarteten Änderungen enthält, wie z. B. Ihren [!DNL Target]-Client-Code und Ihre Analytics-Details:
   ![Konfigurationsdatei herunterladen](assets/client_code.jpg)

Wenn Ihre Einstellungen nicht angezeigt werden, bestätigen Sie, dass Sie auf die rechte Schaltfläche **[!UICONTROL Speichern]** in der [!UICONTROL Mobile Services]-Schnittstelle geklickt und die Datei an den richtigen Speicherort kopiert haben.

Herzlichen Glückwunsch! Sie haben das SDK mit Ihren [!DNL Target]-Kontodetails aktualisiert! Wir führen eine zusätzliche Validierung der Konfiguration durch, nachdem wir [!DNL Target] Anforderungen in der nächsten Lektion hinzugefügt haben.

**[NÄCHSTES: &quot;Hinzufügen Zielgruppen-Anfragen&quot;>](add-requests.md)**
