---
title: Layouts personalisieren
description: 'In dieser letzten Lektion bauen wir zwei Aktivitäten zur Personalisierung in Zielgruppe für unsere Audiencen auf. Erfahren Sie, wie Sie die Aktivitäten in der App laden und anzeigen und überprüfen, ob die Inhalte zum richtigen Zeitpunkt an den richtigen Positionen angezeigt werden.  '
role: Entwickler
level: Zwischenschaltung
topic: Mobil, Personalisierung
feature: Mobile implementieren
doc-type: tutorial
kt: 3040
thumbnail: null
author: Daniel Wright
translation-type: tm+mt
source-git-commit: b89732fcca0be8bffc6e580e4ae0e62df3c3655d
workflow-type: tm+mt
source-wordcount: '1098'
ht-degree: 1%

---


# Layouts personalisieren

Jetzt ist es an der Zeit, alles zusammenzubringen und die personalisierten Erlebnisse zu schaffen. Eine _Aktivität_ ist der [!DNL Target]-Mechanismus, der die Orte, Audiencen und Angebot miteinander verknüpft, sodass [!DNL Target] bei einer Anforderung aus der App mit dem personalisierten Inhalt reagiert. Wir werden zwei Aktivitäten zur Personalisierung in [!DNL Target] erstellen und überprüfen, ob personalisierte Inhalte zum richtigen Zeitpunkt und am richtigen Ort für den richtigen Benutzer angezeigt werden.

## Lernziele

Am Ende dieser Lektion können Sie:

* Erstellen von Aktivitäten in Adobe Target
* Aktivitäten in der Beispielanwendung überprüfen

## Erstellen von Aktivitäten in Adobe Target

Erfahren Sie, wie Sie Aktivitäten für Interages-Benutzer und kontextuelle Angebot erstellen.

### Erste Aktivität - &quot;Benutzer einbinden&quot;

Im Folgenden finden Sie eine Zusammenfassung der Aktivität, die wir erstellen werden:

| Zielgruppe | Orte | Angebote |
|---|---|---|
| Neue Mobile App-Benutzer | wetravel_engagement_home, wetravel_loue | Home: Neue Benutzer einbinden, Suchen: Neue Benutzer einbinden |
| Wiederkehrende Benutzer mobiler Apps | wetravel_engagement_home, wetravel_loue | Home: Zurückkehrende Benutzer, default_content |

Führen Sie in der [!DNL Target]-Schnittstelle Folgendes aus:

1. Wählen Sie **[!UICONTROL Aktivitäten]** > **[!UICONTROL Aktivität erstellen]** > **[!UICONTROL Erlebnis-Targeting]**.

   ![Aktivität erstellen](assets/activity_create_1.jpg)

1. Klicken Sie auf **[!UICONTROL Mobile App]**.
1. Wählen Sie den **[!UICONTROL Form Composer]**.
1. Wählen Sie Ihren Arbeitsbereich aus (der Arbeitsbereich, den Sie auch in früheren Lektionen verwendet haben).
1. Wählen Sie Ihre Eigenschaft (die gleiche Eigenschaft, die Sie in früheren Lektionen verwendet haben).
1. Klicken Sie auf **[!UICONTROL Weiter]**.

   ![Aktivität erstellen](assets/activity_create_2.jpg)

1. Ändern Sie den Titel der Aktivität in **[!UICONTROL Benutzer einbinden]**.
1. Wählen Sie **[!UICONTROL Auslassungspunkte]** > **[!UICONTROL Audience ändern]**.
   ![Neue Mobile App-Benutzer ändern die Audience](assets/activity_create_3.jpg)
1. Legen Sie die Audience auf **[!UICONTROL Neue Mobilanwendungsbenutzer]** fest.
1. Klicken Sie auf **[!UICONTROL Fertig]**.
   ![Neue Audience für Benutzer mobiler Apps](assets/activity_create_4.jpg)

1. Ändern Sie den Speicherort in _wetravel_engagement_home_.
1. Wählen Sie den Dropdownpfeil neben Standardinhalt und dann **[!UICONTROL HTML-Angebot ändern]**.

   ![Neue Audience für Benutzer mobiler Apps](assets/activity_create_5.jpg)

1. Wählen Sie **[!UICONTROL Home: Angebot &quot;Neue Benutzer]** einbinden&quot;.
1. Wählen Sie **[!UICONTROL Fertig]**.

   ![Neue Audience für Benutzer mobiler Apps](assets/activity_create_6.jpg)

1. Wählen Sie **[!UICONTROL Hinzufügen Position]**.
   ![Neue Audience für Benutzer mobiler Apps](assets/activity_create_7.jpg)

1. Wählen Sie den Speicherort _wetravel_engagement_search_ aus.
1. Ändern Sie das HTML-Angebot.

   ![Neue Audience für Benutzer mobiler Apps](assets/activity_create_8.jpg)

1. Wählen Sie **[!UICONTROL Suchen: Angebot &quot;Neue Benutzer]** einbinden&quot;.
1. Klicken Sie auf **[!UICONTROL Fertig]**.

   ![Neue Audience für Benutzer mobiler Apps](assets/activity_create_9.jpg)

Sie haben soeben eine Audience mit Orten und Angeboten verbunden und damit das personalisierte Erlebnis für die Benutzer der neuen mobilen App! Das Erlebnis sollte nun wie folgt aussehen:

![Erlebnis - Finale](assets/activity_engage_users_a_final.jpg)

Erstellen Sie jetzt ein Erlebnis für wiederkehrende Mobile App-Benutzer:

1. Wählen Sie links **[!UICONTROL Hinzufügen Erlebnis-Targeting]**.
1. Wählen Sie die Audience **[!UICONTROL Zurückkehrende Mobilanwendungsbenutzer]**.
1. Wählen Sie **[!UICONTROL Fertig]**.
   ![Wiederkehrende Audience für App-Benutzer](assets/activity_create_11.jpg)

Verwenden Sie jetzt denselben Prozess, den wir zuvor zur Konfiguration des neuen Erlebnisses verwendet haben. Die Konfiguration für das Erlebnis &quot;Zurückkehrende Benutzer mobiler Apps&quot;sollte wie folgt aussehen:

![Wiedergeben der Endversion der mobilen App](assets/activity_engage_users_b_final.jpg)

Fahren wir mit dem nächsten Bildschirm im Setup fort:

1. Klicken Sie auf **[!UICONTROL Weiter]**, um zum Bildschirm **[!UICONTROL Targeting]** fortzufahren.
1. Verwenden Sie die Standardeinstellungen für das Targeting. Wenn Sie Erlebnisse für Audiencen hatten, die sich überlagerten (z. _New Yorker Benutzer_ und _Erstmalige Benutzer_) können Sie die Reihenfolge der Priorität in diesem Bildschirm festlegen.
1. Klicken Sie auf **[!UICONTROL Weiter]**, um zu **[!UICONTROL Ziele und Einstellungen]** fortzufahren.

   ![Aktivität &quot;Benutzer einbinden&quot;- Targeting-Standard](assets/activity_engage_users_targeting.jpg)

Führen Sie nun die Aktivität-Einrichtung durch:

1. Setzen Sie das **[!UICONTROL Primär Ziel]** auf **[!UICONTROL Konversion]**.
1. Legen Sie die Aktion auf **[!UICONTROL Angezeigte eine mbox]** > _wetravel_context_dest_ fest (Da sich diese Position im Bestätigungsbildschirm befindet, können wir sie verwenden, um Konversionen zu messen).

   ![Aktivität &quot;Benutzer einbinden&quot;- Ziele](assets/activity_create_12.jpg)

1. Alle anderen Einstellungen auf dem Bildschirm bleiben auf die Standardwerte eingestellt.
1. Klicken Sie auf **[!UICONTROL Speichern und Schließen]**, um die Aktivität zu speichern.
1. Aktivieren Sie die Aktivität **[!UICONTROL im nächsten Bildschirm.]**

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

1. Legen Sie unter **[!UICONTROL Berichte Settings]** das **[!UICONTROL Primär Ziel]** auf **[!UICONTROL Konversion]** fest.
1. Legen Sie die Aktion auf **[!UICONTROL Anzeige einer mbox]** > _wetravel_context_dest_ fest (in dieser Aktivität ist diese Metrik im Wesentlichen bedeutungslos, da sie auch der gleiche Ort ist, der das Erlebnis liefert).
1. Klicken Sie auf **[!UICONTROL Speichern &amp; Schließen]**.

![Kontextuelle Angebote - Erfahrung](assets/activity_create_14.jpg)

Aktivieren Sie die Aktivität im nächsten Bildschirm.

Jetzt ist unsere zweite Aktivität live und bereit zu testen!

## Validieren des Home-Angebots

Führen Sie den Emulator aus und achten Sie darauf, dass das erste Angebot unten auf dem Startbildschirm angezeigt wird. Wenn Sie ein wiederkehrender Benutzer mit 5 oder mehr App-Starts sind, wird das Angebot _welcome back_ angezeigt. Wenn Sie ein neuer Benutzer sind (weniger als 5 App-Starts), sollte die Meldung _neuer Benutzer_ angezeigt werden:

![Home-Angebot überprüfen](assets/layout_home_validate.jpg)

Wenn das neue Angebot nicht angezeigt wird, löschen Sie die Daten für Ihren Emulator. Dadurch wird die App beim nächsten Start auf 1 zurückgesetzt. Dies geschieht unter **[!UICONTROL Tools]** > **[!UICONTROL AVD Manager]**. Möglicherweise müssen Sie auch Android Studio neu starten, wenn Logcat nicht ordnungsgemäß funktioniert:

![Emulator wischen](assets/layout_home_validate_avd_wipe.jpg)

Sie können die Antwort auch in Logcat überprüfen, indem Sie nach _wetravel_engagement_home_ filtern:

![Home-Angebot validieren - Logcat](assets/layout_home_validate_logcat.jpg)

## Validieren des Angebots &quot;Suchen&quot;

Wählen Sie **[!UICONTROL San Jose]** als **[!UICONTROL Abfahrt]** und **[!UICONTROL San Diego]** als **[!UICONTROL Ziel]** aus und klicken Sie auf **[!UICONTROL Bus]** suchen, um nach verfügbaren Bussen zu suchen.

Im Ergebnisbildschirm sollte die Meldung _Filter verwenden_ angezeigt werden. Wenn Sie ein wiederkehrender Benutzer mit 5 oder mehr App-Starts sind, wird hier keine Meldung angezeigt, da für diesen Speicherort (der leer ist) Standardinhalt festgelegt ist:

![Angebot der Suche überprüfen](assets/layout_search_validate.jpg)

## Überprüfen der kontextbezogenen Angebote im Bildschirm &quot;Vielen Dank&quot;

Fahren Sie jetzt mit dem Buchungsprozess fort:

* Wählen Sie im Ergebnisbildschirm einen Bus aus.
* Wählen Sie einen Platz auf dem Kassengangsbildschirm aus.
* Wählen Sie **[!UICONTROL Kreditkarte]** auf dem Zahlungsbildschirm aus (lassen Sie die Zahlungsinformationen leer - es findet keine tatsächliche Buchung statt).

Da San Diego als Ziel ausgewählt wurde, sollte das Banner _DJ SAM_ auf dem Bestätigungsbildschirm angezeigt werden:

![Context Angebot validieren - San Diego](assets/layout_context_san_diego.jpg)

Wählen Sie **[!UICONTROL Fertig]** und versuchen Sie eine weitere Buchung mit Los Angeles als Ziel. Auf dem Bestätigungsbildschirm sollte das Banner _Universelle Studios_ angezeigt werden:

![Context Angebot validieren - Los Angeles](assets/layout_context_los_angeles.jpg)

## Schlussfolgerung 

Herzlichen Glückwunsch! Hiermit wird der Hauptteil des Adobe Target SDK 4.x für Android-Tutorials beendet. Sie haben jetzt die Fertigkeiten, Personalisierungen in Android-Apps zu implementieren! Sie können diese Dokumentation und Demo-App als Referenz für Ihre zukünftigen Projekte verwenden.

Weiter: Die Funktion-Kennzeichnung ist eine weitere Funktion, die mit Adobe Target in Android implementiert werden kann. Weitere Informationen zum Kennzeichnen von Funktionen finden Sie in der nächsten Lektion.

**[NÄCHSTES: Funktionsmarkierung >](feature-flagging.md)**
