---
title: Herunterladen und Aktualisieren der Beispiel-App "We.Travel"
description: 'Die Beispiel-App "We.Travel"ist bereits mit der Adobe Mobile Services SDK v4 implementiert. Sie müssen es nur aktualisieren, damit es auf Ihre eigenen Experience Cloud-Org- und Lösungskonten verweist.   '
role: Developer
level: Intermediate
topic: Mobile, Personalization
feature: Implement Mobile
doc-type: tutorial
kt: 3040
thumbnail: null
exl-id: 244bcf7a-b59b-4dd1-bd05-0a55ce7a7132
source-git-commit: ee58c7c85708722cf040cd9b039a2855dd390a16
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 0%

---

# Herunterladen und Aktualisieren der Beispiel-App &quot;We.Travel&quot;

Die Beispiel-App &quot;We.Travel&quot;ist bereits mit der Adobe Mobile Services SDK v4 implementiert. Sie müssen es nur aktualisieren, damit es auf Ihre eigenen Experience Cloud-Org- und Lösungskonten verweist.

## Lernziele

Am Ende dieser Lektion können Sie:

* Laden Sie die Beispielanwendung &quot;We.Travel&quot;herunter und öffnen Sie sie in Android Studio
* Überprüfen und Aktualisieren der Mobile Services SDK-Einstellungen für [!DNL Target]

## Herunterladen der We.Travel-App

* Laden Sie [sample-app-android-SDKv4-Base-Version.zip](assets/sample-app-android-SDKv4-Base-Version.zip) herunter.
* Dekomprimieren Sie die ZIP-Datei.
* Öffnen Sie die App in Android Studio als vorhandenes Projekt (ignorieren Sie alle Fehler bezüglich &quot;Ungültiges VCS-Stamm-Mapping&quot;).
* Führen Sie die App in einem Emulator aus, um zu überprüfen, ob die App erstellt wurde und Sie den Startbildschirm sehen können.
* Durchsuchen Sie die App und vergewissern Sie sich, dass Sie den Buchungsvorgang abschließen können (wählen Sie eine beliebige Zahlungsoption aus und klicken Sie einfach auf &quot;Fortfahren&quot;, um den Abrechnungsbildschirm zu überspringen!)

   ![Öffnen Sie den Bildschirm ](assets/wetravel_homeScreen.png)![appConfirmation .](assets/wetravel_confirmationScreen.png)

## Überprüfen und Aktualisieren der Mobile Services SDK-Einstellungen für [!DNL Target]

Das Adobe Mobile Services SDK wurde in der We.Travel-App [gemäß der Dokumentation](https://experienceleague.adobe.com/docs/mobile-services/android/getting-started-android/requirements.html?lang=en) vorinstalliert. Jetzt aktualisieren Sie die Installation, um auf Ihr eigenes [!DNL Target]-Konto zu verweisen.

Erstellen Sie zunächst eine neue App in der Mobile Services-Benutzeroberfläche:

1. Melden Sie sich bei [Adobe Mobile Services-Benutzeroberfläche](https://mobilemarketing.adobe.com/) an.
1. Gehen Sie zu [!UICONTROL Apps verwalten] und klicken Sie dann auf **[!UICONTROL Hinzufügen]** , um eine neue App hinzuzufügen, die mit diesem Tutorial verwendet werden soll (**[!UICONTROL Apps verwalten]** > **[!UICONTROL Hinzufügen]**).
1. Wählen Sie eine Analytics Report Suite mit Nicht-Produktions-Daten aus, geben Sie der App einen Namen, wählen Sie den Typ **[!UICONTROL Standard]** und klicken Sie auf **[!UICONTROL Speichern]**.
1. Nachdem die App hinzugefügt wurde, fügen Sie den [!DNL Target] Client-Code auf dem nächsten Bildschirm im Abschnitt [!UICONTROL SDK-Target-Optionen] hinzu (Sie finden Ihren Client-Code in der [!DNL Target]-Benutzeroberfläche unter **[!UICONTROL Einrichtung]** > **[!UICONTROL Implementierung]** > **[!UICONTROL Einstellungen bearbeiten]** neben dem Download `at.js`/> Schaltfläche).
1. Die Einstellung [!UICONTROL Anfrage-Timeout] bestimmt, wie lange die App auf die Antwort vom [!DNL Target]-Server wartet, bevor Zeitüberschreitungsanweisungen ausgeführt werden. Behalten Sie einfach die Standardeinstellung bei.
1. Aktivieren Sie den [!UICONTROL Besucher-ID-Dienst] und stellen Sie sicher, dass Ihre [!UICONTROL Organisation] in der Dropdown-Liste ausgewählt ist.
1. Speichern Sie Ihre Änderungen, indem Sie oben rechts im Fenster auf **[!UICONTROL Speichern]** klicken (nicht auf die Option [!UICONTROL Universelle Links], [!UICONTROL App-Links] oder [!UICONTROL Push-Dienste]).
1. Scrollen Sie zum Abschnitt App SDK-Downloads am unteren Rand der Seite und laden Sie die Konfigurationsdatei herunter:

   ![Konfigurationsdatei herunterladen](assets/config_file.jpg)

1. Ersetzen Sie die Datei `ADBMobileConfig.json` in Ihrem Asset-Ordner für Android Studio-Projekte (app > src > main > assets).

1. Öffnen Sie nun die Datei `ADBMobileConfig.json` und stellen Sie sicher, dass sie die erwarteten Änderungen enthält, wie Ihren [!DNL Target] Client-Code und Ihre Analytics-Details:
   ![Konfigurationsdatei herunterladen](assets/client_code.jpg)

Wenn Ihre Einstellungen nicht angezeigt werden, bestätigen Sie, dass Sie auf die rechte Schaltfläche **[!UICONTROL Speichern]** in der [!UICONTROL Mobile Services]-Benutzeroberfläche geklickt und die Datei an den richtigen Speicherort kopiert haben.

Herzlichen Glückwunsch! Sie haben das SDK mit Ihren [!DNL Target] Kontodetails aktualisiert! Wir führen eine zusätzliche Validierung der Konfiguration durch, nachdem wir in der nächsten Lektion [!DNL Target] -Anforderungen hinzugefügt haben.

**[NÄCHSTES : &quot;Target-Anforderungen hinzufügen&quot;>](add-requests.md)**
