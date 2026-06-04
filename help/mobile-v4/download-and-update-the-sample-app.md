---
title: Herunterladen und Aktualisieren der We.Travel-Beispielanwendung
description: Die Beispiel-App „We.Travel“ ist mit dem Adobe Mobile Services SDK v4 vorimplementiert. Sie müssen sie nur aktualisieren, damit sie auf Ihre eigenen Experience Cloud-Organisations- und Lösungskonten verweist.
role: Developer
level: Intermediate
topic: Mobile, Personalization
feature: Implement Mobile
doc-type: tutorial
kt: 3040
exl-id: 244bcf7a-b59b-4dd1-bd05-0a55ce7a7132
TQID: https://experienceleague.adobe.com/23TuO5OZXkf9TDWMgIEXyu2Hx9f3dzI1n91u7A1Wix0
product_v2:
  - id: e43347a8-f2c5-4aa4-8623-6f13875d7e3a
feature_v2:
  - id: c93393a4-e558-47e1-992e-c91ed4d480ce
subfeature_v2:
  - id: fd0ff162-b6d3-4a11-8aeb-e165a01c0f0a
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
source-git-commit: c0b4abf2d4ead4d58a8db6e8970857b7b50dbe5c
workflow-type: tm+mt
source-wordcount: 530
ht-degree: 0%

---

# Herunterladen und Aktualisieren der We.Travel-Beispielanwendung

Die Beispiel-App „We.Travel“ ist mit dem Adobe Mobile Services SDK v4 vorimplementiert. Sie müssen sie nur aktualisieren, damit sie auf Ihre eigenen Experience Cloud-Organisations- und Lösungskonten verweist.

## Lernziele

Am Ende dieser Lektion haben Sie folgende Möglichkeiten:

* Herunterladen und Öffnen der Beispielanwendung We.Travel in Android Studio
* Überprüfen und aktualisieren Sie die Mobile Services SDK-Einstellungen für [!DNL Target]

## Herunterladen der We.Travel-App

* Laden Sie die Datei [sample-app-android-SDKv4-Base-Version.zip) &#x200B;](assets/sample-app-android-SDKv4-Base-Version.zip)
* Dekomprimieren Sie die ZIP-Datei
* Öffnen Sie die App in Android Studio als vorhandenes Projekt (ignorieren Sie alle Fehler über „Ungültige VCS-Stammzuordnung„).
* Führen Sie die App in einem Emulator aus, um zu bestätigen, dass die App erstellt wird und Sie den Startbildschirm sehen können
* Durchsuchen Sie die App und vergewissern Sie sich, dass Sie den Buchungsprozess abschließen können (wählen Sie eine Zahlungsoption aus und klicken Sie einfach auf „Fortfahren“, um über den Rechnungsbildschirm zu springen!)

  ![Öffnen Sie den App](assets/wetravel_homeScreen.png)![Bestätigungsbildschirm](assets/wetravel_confirmationScreen.png)

## Überprüfen und aktualisieren Sie die Mobile Services SDK-Einstellungen für [!DNL Target]

Die Adobe Mobile Services SDK wurde innerhalb der We.Travel-App vorinstalliert [laut Dokumentation](https://experienceleague.adobe.com/docs/mobile-services/android/getting-started-android/requirements.html?lang=en). Jetzt aktualisieren Sie die Installation, sodass sie auf Ihr eigenes [!DNL Target] verweist.

Erstellen Sie zunächst eine neue App in der Mobile Services-Benutzeroberfläche:

1. Melden Sie sich bei der [Adobe Mobile Services-Benutzeroberfläche an](https://mobilemarketing.adobe.com/).
1. Gehen Sie zu [!UICONTROL Programme verwalten] und klicken Sie dann auf **[!UICONTROL Hinzufügen]**, um eine neue App hinzuzufügen, die mit diesem Tutorial verwendet werden soll (**[!UICONTROL Programme verwalten]** > **[!UICONTROL Hinzufügen]**).
1. Wählen Sie eine Analytics Report Suite mit Nicht-Produktionsdaten aus, geben Sie der App einen Namen, wählen Sie den **[!UICONTROL Standard]**-Typ aus und klicken Sie auf **[!UICONTROL Speichern]**.
1. Fügen Sie nach dem Hinzufügen der App Ihren [!DNL Target]-Client-Code auf dem nächsten Bildschirm im Abschnitt [!UICONTROL SDK Target-Optionen] hinzu (Sie finden Ihren Client-Code in der [!DNL Target] unter **[!UICONTROL Setup]** > **[!UICONTROL Implementierung]** > **[!UICONTROL Einstellungen bearbeiten]** neben der Schaltfläche `at.js` herunterladen ).
1. Die Einstellung [!UICONTROL Zeitüberschreitung bei Anfragen] bestimmt, wie lange die App auf die Antwort vom [!DNL Target]-Server wartet, bevor Zeitüberschreitungsanweisungen ausgeführt werden. Lassen Sie einfach die Standardeinstellung.
1. Aktivieren Sie den [!UICONTROL Besucher-ID]Service und stellen Sie sicher, dass [!UICONTROL Organisation] in der Dropdown-Liste ausgewählt ist.
1. Speichern Sie Ihre Änderungen, indem **[!UICONTROL oben rechts im Fenster auf]** Speichern“ klicken (nicht auf die im Abschnitt [!UICONTROL Universelle Links], [!UICONTROL App-Links] Optionen oder [!UICONTROL Push-Services] ).
1. Scrollen Sie zum Abschnitt App-SDK-Downloads unten auf der Seite und laden Sie die Konfigurationsdatei herunter:

   ![Laden Sie die Konfigurationsdatei herunter](assets/config_file.jpg)

1. Ersetzen Sie die `ADBMobileConfig.json` Datei in Ihrem Android Studio-Projekt-Asset-Ordner (app > src > main > assets).

1. Öffnen Sie nun die `ADBMobileConfig.json`-Datei und stellen Sie sicher, dass sie die erwarteten Änderungen enthält, z. B. Ihren [!DNL Target]-Client-Code und Ihre Analytics-Details:
   ![Laden Sie die Konfigurationsdatei herunter](assets/client_code.jpg)

Falls Ihre Einstellungen nicht angezeigt werden, vergewissern Sie sich, dass Sie in der Benutzeroberfläche von [!UICONTROL Mobile Services] auf die rechte **[!UICONTROL Speichern]**-Schaltfläche geklickt und die Datei an den richtigen Speicherort kopiert haben.

Herzlichen Glückwunsch! Sie haben die SDK mit Ihren [!DNL Target] Kontodetails aktualisiert! Wir führen eine zusätzliche Validierung der Konfiguration durch, nachdem wir in der nächsten Lektion [!DNL Target] Anfragen hinzugefügt haben.

**[NEXT : „Target-Anforderungen hinzufügen“ >](add-requests.md)**
