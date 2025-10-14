---
title: Layouts personalisieren
description: In dieser letzten Lektion erstellen wir zwei Personalisierungsaktivitäten in Target für unsere Zielgruppen. Erfahren Sie, wie Sie die Aktivitäten in der App laden und anzeigen und überprüfen Sie, ob die Inhalte zur richtigen Zeit an den richtigen Stellen angezeigt werden.
role: Developer
level: Intermediate
topic: Mobile, Personalization
feature: Implement Mobile
doc-type: tutorial
kt: 3040
author: Daniel Wright
exl-id: a9f033d9-9f72-4154-88f5-d36423a404d0
source-git-commit: 342e02562b5296871638c1120114214df6115809
workflow-type: tm+mt
source-wordcount: '992'
ht-degree: 1%

---

# Layouts personalisieren

Jetzt ist es an der Zeit, alles zusammenzuführen und die personalisierten Erlebnisse zu schaffen. Eine _Aktivität_ ist der [!DNL Target] Mechanismus, der die Standorte, Zielgruppen und Angebote miteinander verknüpft, sodass [!DNL Target] bei einer Anfrage über die App mit den personalisierten Inhalten antwortet. Wir erstellen zwei Personalisierungsaktivitäten in [!DNL Target] und überprüfen, ob personalisierte Inhalte dem richtigen Benutzer zur richtigen Zeit und am richtigen Ort angezeigt werden.

## Lernziele

Am Ende dieser Lektion haben Sie folgende Möglichkeiten:

* Erstellen von Aktivitäten in Adobe Target
* Validieren der Aktivitäten in der Beispiel-App

## Erstellen von Aktivitäten in Adobe Target

Erfahren Sie, wie Sie Engage-Benutzer und kontextuelle Angebotsaktivitäten erstellen.

### Erste Aktivität - „Benutzer einbinden“

Hier ist eine Zusammenfassung der Aktivität, die wir erstellen werden:

| Zielgruppe | Positionen | Angebote |
|---|---|---|
| Neue Mobile-App-Benutzer | wetravel_engage_home, wetravel_engage_search | Startseite: Neue Benutzer einbinden, Suche: Neue Benutzer einbinden |
| Rückkehrende Mobile-App-Benutzer | wetravel_engage_home, wetravel_engage_search | Startseite: Wiederkehrende Benutzer, default_content |

Gehen Sie in der [!DNL Target] folgendermaßen vor:

1. Wählen Sie **[!UICONTROL Activities]** > **[!UICONTROL Create Activity]** > **[!UICONTROL Experience Targeting]** aus.

   ![Aktivität erstellen](assets/activity_create_1.jpg)

1. Klicken Sie auf **[!UICONTROL Mobile App]**.
1. Wählen Sie die **[!UICONTROL Form composer]** aus.
1. Wählen Sie Ihren Arbeitsbereich aus (der gleiche Arbeitsbereich, den Sie in vorherigen Lektionen verwendet haben).
1. Wählen Sie Ihre Eigenschaft aus (die Eigenschaft, die Sie in vorherigen Lektionen verwendet haben).
1. Klicken Sie auf **[!UICONTROL Next]**.

   ![Aktivität erstellen](assets/activity_create_2.jpg)

1. Ändern Sie den Aktivitätstitel in **[!UICONTROL Engage Users]**.
1. Wählen Sie die **[!UICONTROL ellipsis]** > **[!UICONTROL Change Audience]** aus.
   ![Benutzende von neuen Mobile Apps ändern die Zielgruppe](assets/activity_create_3.jpg)
1. Legen Sie die Zielgruppe auf **[!UICONTROL New Mobile App Users]** fest.
1. Klicken Sie auf **[!UICONTROL Done]**.
   ![Zielgruppe der neuen Mobile-App-Benutzer](assets/activity_create_4.jpg)

1. Ändern Sie den Speicherort in _wetravel_engage_home_.
1. Wählen Sie den Dropdown-Pfeil neben Standardinhalt und dann **[!UICONTROL Change HTML Offer]** aus.

   ![Zielgruppe der neuen Mobile-App-Benutzer](assets/activity_create_5.jpg)

1. Wählen Sie das **[!UICONTROL Home: Engage New Users]** aus.
1. Wählen Sie **[!UICONTROL Done]** aus.

   ![Zielgruppe der neuen Mobile-App-Benutzer](assets/activity_create_6.jpg)

1. Wählen Sie **[!UICONTROL Add Location]** aus.
   ![Zielgruppe der neuen Mobile-App-Benutzer](assets/activity_create_7.jpg)

1. Wählen Sie den _wetravel_engage_search_ aus.
1. Ändern Sie das HTML-Angebot.

   ![Zielgruppe der neuen Mobile-App-Benutzer](assets/activity_create_8.jpg)

1. Wählen Sie das **[!UICONTROL Search: Engage New Users]** aus.
1. Klicken Sie auf **[!UICONTROL Done]**.

   ![Zielgruppe der neuen Mobile-App-Benutzer](assets/activity_create_9.jpg)

Sie haben soeben eine Zielgruppe mit Standorten und Angeboten verbunden und so ein personalisiertes Erlebnis für die neuen Mobile-App-Benutzer erstellt! Das Erlebnis sollte nun wie folgt aussehen:

![Erleben Sie ein Finale](assets/activity_engage_users_a_final.jpg)

Erstellen Sie jetzt ein Erlebnis für zurückkehrende Mobile-App-Benutzer:

1. Wählen Sie links **[!UICONTROL Add Experience Targeting]** aus.
1. Wählen Sie die Zielgruppen-**[!UICONTROL Returning Mobile App Users]** aus.
1. Wählen Sie **[!UICONTROL Done]** aus.
   ![Wiederkehrende Zielgruppe von Mobile-App-Benutzern](assets/activity_create_11.jpg)

Verwenden Sie nun denselben Prozess wie zuvor, um das neue Erlebnis zu konfigurieren. Die Konfiguration für das Erlebnis „Benutzer von wiederkehrenden Mobile Apps“ sollte wie folgt aussehen:

![Wiederkehrende Benutzende von Mobile Apps endgültig](assets/activity_engage_users_b_final.jpg)

Fahren wir im Setup mit dem nächsten Bildschirm fort:

1. Klicken Sie auf **[!UICONTROL Next]** , um zum Bildschirm **[!UICONTROL Targeting]** zu gelangen.
1. Verwenden Sie die Standardeinstellungen für das Targeting. Wenn sich überschneidende Audiences vorhanden sind (z. B. _New York Users_ und _First Time Users_), können Sie die Prioritätsreihenfolge auf diesem Bildschirm festlegen.
1. Klicken Sie auf **[!UICONTROL Next]** , um zu **[!UICONTROL Goals & Settings]** zu gelangen.

   ![Aktivität „Benutzer einbinden“ - Standard-Targeting](assets/activity_engage_users_targeting.jpg)

Schließen wir nun die Aktivitätseinrichtung ab:

1. Legen Sie die **[!UICONTROL Primary Goal]** auf **[!UICONTROL Conversion]** fest.
1. Legen Sie die Aktion auf **[!UICONTROL Viewed an mbox]** > _wetravel_context_dest_ fest (Da sich diese Position auf dem Bestätigungsbildschirm befindet, können wir sie zum Messen von Konversionen verwenden).

   ![Benutzeraktivität interagieren - Ziele](assets/activity_create_12.jpg)

1. Alle anderen Einstellungen auf dem Bildschirm auf die Standardeinstellungen zurücksetzen.
1. Klicken Sie auf **[!UICONTROL Save & Close]** , um die Aktivität zu speichern.
1. Aktivieren Sie die **[!UICONTROL Activity]** im nächsten Bildschirm.

![Experience B-Zielgruppe](assets/activity_create_13.jpg)

Unsere erste Aktivität ist jetzt live und bereit zum Testen!

### Zweite Aktivität - „Kontextuelle Angebote“

Hier ist eine Zusammenfassung der zweiten Aktivität, die wir erstellen werden:

| Zielgruppe | Standort | Angebote |
| --- | --- | --- |
| Zielort: San Diego | wetravel_context_dest | Promotion für San Diego |
| Zielort: Los Angeles | wetravel_context_dest | Promotion für Los Angeles |

Wiederholen Sie denselben Vorgang wie oben für die nächste Aktivität - „Kontextuelle Angebote“. Die endgültige Konfiguration für beide Erlebnisse ist unten dargestellt:

#### San Diego

![Kontextuelle Angebote - Erlebnis A](assets/activity_contextual_a_final.jpg)

#### Los Angeles

![Kontextuelle Angebote - Erlebnis B](assets/activity_contextual_b_final.jpg)

Im Schritt Ziele und Einstellungen ändern wir das Primäre Ziel in die Position auf dem Buchungsbestätigungsbildschirm:

1. Legen Sie unter der **[!UICONTROL Reporting Settings]** den **[!UICONTROL Primary Goal]** auf **[!UICONTROL Conversion]** fest.
1. Legen Sie die Aktion auf **[!UICONTROL Viewed an mbox]** > _wetravel_context_dest_ fest (in dieser Aktivität ist diese Metrik im Grunde bedeutungslos, da dies auch derselbe Ort ist, an dem das Erlebnis bereitgestellt wird).
1. Klicken Sie auf **[!UICONTROL Save & Close]**.

![Kontextuelle Angebote - Erlebnis](assets/activity_create_14.jpg)

Aktivieren Sie die Aktivität auf dem nächsten Bildschirm.

Jetzt ist unsere zweite Aktivität live und bereit zum Testen!

## Validieren des Startseiten-Angebots

Führen Sie den Emulator aus und achten Sie unten auf dem Startbildschirm auf das erste anzuzeigende Angebot. Wenn Sie ein wiederkehrender Benutzer mit 5 oder mehr Mobile-App-Starts sind, wird das _Willkommen zurück_-Angebot angezeigt. Wenn Sie ein neuer Benutzer sind (weniger als 5 Programmstarts), sollten Sie die Nachricht _neuer Benutzer_ sehen:

![Validieren des Startangebots](assets/layout_home_validate.jpg)

Wenn das neue Benutzerangebot nicht angezeigt wird, versuchen Sie, die Daten für Ihren Emulator zu löschen. Dadurch werden die App-Starts beim nächsten Start auf 1 zurückgesetzt. Dies geschieht unter **[!UICONTROL Tools]** > **[!UICONTROL AVD Manager]**. Möglicherweise müssen Sie auch Android Studio neu starten, wenn Logcat nicht ordnungsgemäß funktioniert:

![Emulator &#x200B;](assets/layout_home_validate_avd_wipe.jpg)

Sie können die Antwort auch in Logcat überprüfen, indem Sie nach &quot;__engage_home“_:

![Validieren des Startangebots - LogCat](assets/layout_home_validate_logcat.jpg)

## Angebote durchsuchen

Wählen Sie **[!UICONTROL San Jose]** als **[!UICONTROL Departure]** und **[!UICONTROL San Diego]** als **[!UICONTROL Destination]** aus und klicken Sie auf **[!UICONTROL Find Bus]**, um nach verfügbaren Bussen zu suchen.

Auf dem Ergebnisbildschirm sollte die Meldung „Filter _&quot; angezeigt_. Wenn Sie ein wiederkehrender Benutzer mit 5 oder mehr App-Starts sind, wird hier keine Nachricht angezeigt, da der Standardinhalt für diesen Speicherort festgelegt ist (der leer ist):

![Suchangebot validieren](assets/layout_search_validate.jpg)

## Validieren der kontextuellen Angebote auf dem Dankesbildschirm

Fahren Sie nun mit dem Buchungsprozess fort:

* Wählen Sie auf dem Ergebnisbildschirm einen Bus aus.
* Wählen Sie einen Platz auf der Kasse.
* Wählen Sie **[!UICONTROL Credit Card]** auf dem Zahlungsbildschirm (lassen Sie die Zahlungsinformationen leer - es findet keine tatsächliche Buchung statt).

Da San Diego als Ziel ausgewählt wurde, sollten Sie das _DJ SAM_ Angebotsbanner auf dem Bestätigungsbildschirm sehen:

![Kontextangebot validieren - San Diego](assets/layout_context_san_diego.jpg)

Wählen Sie jetzt **[!UICONTROL Done]** und versuchen Sie eine andere Buchung mit Los Angeles als Ziel. Auf dem Bestätigungsbildschirm sollte das Banner _Universal Studios_ angezeigt werden:

![Kontextangebot validieren - Los Angeles](assets/layout_context_los_angeles.jpg)

## Schlussfolgerung 

Herzlichen Glückwunsch! Damit ist der Hauptteil des Tutorials zu Adobe Target SDK 4.x für Android abgeschlossen. Sie haben jetzt die Fähigkeiten, Personalisierung in Android-Apps zu implementieren! Sie können auf diese Dokumentation und Demo-App als Referenz für Ihre zukünftigen Projekte verweisen.

Weiter: Feature Flagging ist eine weitere Funktion, die mit Adobe Target in Android implementiert werden kann. Weitere Informationen zu Feature Flags finden Sie in der nächsten Lektion.

**[WEITER : Feature Flagging >](feature-flagging.md)**
