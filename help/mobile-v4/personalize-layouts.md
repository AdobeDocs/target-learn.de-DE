---
title: Layouts personalisieren
seo-title: Layouts personalisieren
description: 'In dieser letzten Lektion werden wir zwei Aktivitäten zur Personalisierung in Zielgruppe für unsere Audiencen aufbauen. Wir laden und zeigen die Aktivitäten in der App an und überprüfen, ob der Inhalt zum richtigen Zeitpunkt an den richtigen Positionen angezeigt wird.  '
seo-description: In dieser letzten Lektion werden wir zwei Aktivitäten zur Personalisierung in Zielgruppe für unsere Audiencen aufbauen. Wir laden und zeigen die Aktivitäten in der App an und überprüfen, ob der Inhalt zum richtigen Zeitpunkt an den richtigen Positionen angezeigt wird.
feature: mobile
kt: 3040
audience: developer
doc-type: tutorial
activity-type: implement
translation-type: tm+mt
source-git-commit: b331bb29c099bd91df27300ebe199cafa12516db
workflow-type: tm+mt
source-wordcount: '1129'
ht-degree: 1%

---


# Layouts personalisieren

Jetzt ist es an der Zeit, alles zusammenzubringen und die personalisierten Erlebnisse zu schaffen. Eine _Aktivität_ ist der [!DNL Target] Mechanismus, der Orte, Audiencen und Angebot miteinander verknüpft, sodass beim Erstellen der Anforderung aus der App mit dem personalisierten Inhalt [!DNL Target] reagiert. Wir werden zwei Aktivitäten zur Personalisierung erstellen [!DNL Target] und bestätigen, dass personalisierte Inhalte zum richtigen Zeitpunkt und am richtigen Ort für den richtigen Benutzer angezeigt werden.

## Lernziele

Am Ende dieser Lektion können Sie:

* Erstellen von Aktivitäten in Adobe Target
* Aktivitäten in der Beispielanwendung überprüfen

## Aktivitäten in Adobe Target erstellen

Erfahren Sie, wie Sie Aktivitäten für Interages-Benutzer und kontextuelle Angebot erstellen.

### Erste Aktivität - &quot;Benutzer einbinden&quot;

Im Folgenden finden Sie eine Zusammenfassung der Aktivität, die wir erstellen werden:

| Zielgruppe | Orte | Angebote |
|---|---|---|
| Neue Mobile App-Benutzer | wetravel_engagement_home, wetravel_loue | Home: Neue Benutzer einbinden, Suchen: Neue Benutzer einbinden |
| Wiederkehrende Benutzer mobiler Apps | wetravel_engagement_home, wetravel_loue | Home: Zurückkehrende Benutzer, default_content |

Führen Sie auf der [!DNL Target] Oberfläche folgende Schritte aus:

1. Wählen Sie **[!UICONTROL Aktivitäten]** > Aktivität **** erstellen > **[!UICONTROL Erlebnis-Targeting]**.

   ![Aktivität erstellen](assets/activity_create_1.jpg)

1. Klicken Sie auf **[!UICONTROL Mobilanwendung]**.
1. Wählen Sie den **[!UICONTROL Form Composer]** aus.
1. Wählen Sie Ihren Arbeitsbereich aus (der Arbeitsbereich, den Sie in früheren Lektionen verwendet haben).
1. Wählen Sie Ihre Eigenschaft (die gleiche Eigenschaft, die Sie in früheren Lektionen verwendet haben).
1. Klicken Sie auf **[!UICONTROL Weiter]**.

   ![Aktivität erstellen](assets/activity_create_2.jpg)

1. Ändern Sie den Titel der Aktivität in **[!UICONTROL Benutzereingabe]**.
1. Wählen Sie **[!UICONTROL Auslassungspunkte]** > Audience **[!UICONTROL ändern]**.
   ![Neue Mobile App-Benutzer ändern die Audience](assets/activity_create_3.jpg)
1. Legen Sie die Audience auf **[!UICONTROL Neue Mobilanwendungsbenutzer]** fest.
1. Klicken Sie auf **[!UICONTROL Fertig]**.
   ![Neue Audience für Benutzer mobiler Apps](assets/activity_create_4.jpg)

1. Ändern Sie den Speicherort in _wetravel_engagement_home_.
1. Wählen Sie den Dropdownpfeil neben &quot;Standardinhalt&quot;und dann &quot;HTML-Angebot **[!UICONTROL ändern&quot;]**.

   ![Neue Audience für Benutzer mobiler Apps](assets/activity_create_5.jpg)

1. Wählen Sie die **[!UICONTROL Startseite aus: Angebot für neue Benutzer]** einbinden.
1. Wählen Sie **[!UICONTROL Fertig]**.

   ![Neue Audience für Benutzer mobiler Apps](assets/activity_create_6.jpg)

1. Wählen Sie **[!UICONTROL Hinzufügen Ort]**.
   ![Neue Audience für Benutzer mobiler Apps](assets/activity_create_7.jpg)

1. Wählen Sie die _Position &quot;wetravel_engagement_search&quot;_ .
1. Ändern Sie das HTML-Angebot.

   ![Neue Audience für Benutzer mobiler Apps](assets/activity_create_8.jpg)

1. Wählen Sie die **[!UICONTROL Suche aus: Angebot für neue Benutzer]** einbinden.
1. Klicken Sie auf **[!UICONTROL Fertig]**.

   ![Neue Audience für Benutzer mobiler Apps](assets/activity_create_9.jpg)

Sie haben soeben eine Audience mit Orten und Angeboten verbunden und damit das personalisierte Erlebnis für die Benutzer der neuen mobilen App! Das Erlebnis sollte nun wie folgt aussehen:

![Erlebnis - Finale](assets/activity_engage_users_a_final.jpg)

Erstellen Sie jetzt ein Erlebnis für wiederkehrende Mobile App-Benutzer:

1. Wählen Sie **[!UICONTROL Hinzufügen Erlebnis-Targeting]** auf der linken Seite.
1. Wählen Sie die Audience **[!UICONTROL Zurückkehrende Mobilanwendungsbenutzer]** aus.
1. Wählen Sie **[!UICONTROL Fertig]**.
   ![Wiederkehrende Audience für App-Benutzer](assets/activity_create_11.jpg)

Verwenden Sie jetzt denselben Prozess, den wir zuvor zur Konfiguration des neuen Erlebnisses verwendet haben. Die Konfiguration für das Erlebnis &quot;Zurückkehrende Benutzer mobiler Apps&quot;sollte wie folgt aussehen:

![Wiedergeben der Endversion der mobilen App](assets/activity_engage_users_b_final.jpg)

Fahren wir mit dem nächsten Bildschirm im Setup fort:

1. Click **[!UICONTROL Next]** to advance to the **[!UICONTROL Targeting]** screen.
1. Verwenden Sie die Standardeinstellungen für das Targeting. Wenn Sie Erlebnisse für Audiencen hatten, die sich überlagerten (z. B. _New York-Benutzer_ und _Erstbenutzer_), können Sie die Reihenfolge der Priorität in diesem Bildschirm festlegen.
1. Klicken Sie auf **[!UICONTROL Weiter]** , um zu **[!UICONTROL Zielen und Einstellungen]** zu gelangen.

   ![Aktivität &quot;Benutzer einbinden&quot;- Targeting-Standard](assets/activity_engage_users_targeting.jpg)

Führen Sie nun die Aktivität-Einrichtung durch:

1. Legen Sie als **[!UICONTROL Primär]** Ziel die **[!UICONTROL Umrechnung]** fest.
1. Legen Sie die Aktion auf **[!UICONTROL Anzeige einer mbox]** > _wetravel_context_dest_ fest (da sich diese Position im Bestätigungsbildschirm befindet, können wir damit Konversionen messen).

   ![Aktivität &quot;Benutzer einbinden&quot;- Ziele](assets/activity_create_12.jpg)

1. Alle anderen Einstellungen auf dem Bildschirm bleiben auf die Standardwerte eingestellt.
1. Click **[!UICONTROL Save &amp; Close]** to save the Activity.
1. Aktivieren Sie die **[!UICONTROL Aktivität]** im nächsten Bildschirm.

![Erlebnis B-Audience](assets/activity_create_13.jpg)

Unsere erste Aktivität ist jetzt live und bereit zu testen!

### Zweite Aktivität - &quot;Kontextuelle Angebote&quot;

Im Folgenden finden Sie eine Zusammenfassung der zweiten Aktivität, die wir erstellen werden:

| Zielgruppe | Position | Angebote |
| --- | --- | --- |
| Ziel: San Diego | wetravel_context_dest | Verkaufsförderung für San Diego |
| Ziel: Los Angeles | wetravel_context_dest | Promotion für Los Angeles |

Wiederholen Sie diesen Vorgang für die nächste Aktivität - &quot;Kontextuelle Angebot&quot;. Die endgültige Konfiguration für beide Erlebnisse wird unten angezeigt:

#### San Diego

![Kontextuelle Angebote - Erlebnis A](assets/activity_contextual_a_final.jpg)

#### Los Angeles

![Kontextuelle Angebote - Erlebnis B](assets/activity_contextual_b_final.jpg)

Im Schritt Ziele und Einstellungen ändern wir das Primär Goal in den Speicherort im Bildschirm Buchungsbestätigung:

1. Legen Sie unter &quot; **[!UICONTROL Berichte Settings]**&quot;das **[!UICONTROL Primär Goal]** auf **[!UICONTROL Conversion]** fest.
1. Setzen Sie die Aktion auf **[!UICONTROL Anzeige einer mbox]** > _wetravel_context_dest_ (in dieser Aktivität ist diese Metrik im Grunde bedeutungslos, da sie auch der gleiche Ort ist, der das Erlebnis liefert).
1. Klicken Sie auf **[!UICONTROL Speichern &amp; Schließen]**.

![Kontextuelle Angebote - Erfahrung](assets/activity_create_14.jpg)

Aktivieren Sie die Aktivität im nächsten Bildschirm.

Jetzt ist unsere zweite Aktivität live und bereit zu testen!

## Validieren des Home-Angebots

Führen Sie den Emulator aus und achten Sie darauf, dass das erste Angebot unten auf dem Startbildschirm angezeigt wird. Wenn Sie ein wiederkehrender Benutzer mit 5 oder mehr App-Starts sind, wird das _Angebot &quot;Willkommen zurück_ &quot;angezeigt. Wenn Sie ein neuer Benutzer sind (weniger als 5 App-Starts), sollte die _neue Benutzer_ -Nachricht angezeigt werden:

![Home-Angebot überprüfen](assets/layout_home_validate.jpg)

Wenn das neue Angebot nicht angezeigt wird, löschen Sie die Daten für Ihren Emulator. Dadurch wird die App beim nächsten Start auf 1 zurückgesetzt. Dies geschieht unter **[!UICONTROL Tools]** > **[!UICONTROL AVD Manager]**. Möglicherweise müssen Sie auch Android Studio neu starten, wenn Logcat nicht ordnungsgemäß funktioniert:

![Emulator wischen](assets/layout_home_validate_avd_wipe.jpg)

Sie können die Antwort auch in Logcat überprüfen, indem Sie nach _wetravel_engagement_home_ filtern:

![Home-Angebot validieren - Logcat](assets/layout_home_validate_logcat.jpg)

## Validieren des Angebots &quot;Suchen&quot;

Wählen Sie **[!UICONTROL San Jose]** als **[!UICONTROL Abfahrt]** und **[!UICONTROL San Diego]** als **[!UICONTROL Ziel]** und klicken Sie auf **[!UICONTROL Bus]** suchen, um nach verfügbaren Bussen zu suchen.

Im Ergebnisbildschirm sollte die Meldung _Filter_ verwenden angezeigt werden. Wenn Sie ein wiederkehrender Benutzer mit 5 oder mehr App-Starts sind, wird hier keine Meldung angezeigt, da für diesen Speicherort (der leer ist) Standardinhalt festgelegt ist:

![Angebot der Suche überprüfen](assets/layout_search_validate.jpg)

## Überprüfen der kontextbezogenen Angebote im Bildschirm &quot;Vielen Dank&quot;

Fahren Sie jetzt mit dem Buchungsprozess fort:

* Wählen Sie im Ergebnisbildschirm einen Bus aus.
* Wählen Sie einen Platz auf dem Kassengangsbildschirm aus.
* Wählen Sie auf dem Zahlungsbildschirm die **[!UICONTROL Kreditkarte]** aus (lassen Sie die Zahlungsinformationen leer - es findet keine tatsächliche Buchung statt).

Da San Diego als Zielort ausgewählt wurde, sollte das Banner des _DJ SAM_ -Angebots auf dem Bestätigungsbildschirm angezeigt werden:

![Context Angebot validieren - San Diego](assets/layout_context_san_diego.jpg)

Wählen Sie nun **[!UICONTROL Fertig]** und versuchen Sie eine weitere Buchung mit Los Angeles als Ziel. Auf dem Bestätigungsbildschirm sollte das Banner _Universal Studios_ angezeigt werden:

![Context Angebot validieren - Los Angeles](assets/layout_context_los_angeles.jpg)

## Schlussfolgerung 

Herzlichen Glückwunsch! Hiermit wird der Hauptteil des Adobe Target-SDK 4.x für Android-Tutorials beendet. Sie haben jetzt die Fertigkeiten, Personalisierungen in Android-Apps zu implementieren! Sie können diese Dokumentation und Demo-App als Referenz für Ihre zukünftigen Projekte verwenden.

Weiter: Die Funktion-Kennzeichnung ist eine weitere Funktion, die mit Adobe Target in Android implementiert werden kann. Weitere Informationen zum Kennzeichnen von Funktionen finden Sie in der nächsten Lektion.

**[NÄCHSTES: Funktionsmarkierung >](feature-flagging.md)**
