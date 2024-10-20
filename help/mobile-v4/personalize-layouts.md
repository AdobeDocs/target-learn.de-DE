---
title: Layouts personalisieren
description: In dieser letzten Lektion erstellen wir zwei Personalisierungsaktivitäten in Target für unsere Zielgruppen. Erfahren Sie, wie Sie die Aktivitäten in der App laden und anzeigen und überprüfen können, ob der Inhalt zum richtigen Zeitpunkt an den richtigen Orten angezeigt wird.
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

Jetzt ist es an der Zeit, alles zusammenzubringen und die personalisierten Erlebnisse zu erstellen. Eine _Aktivität_ ist der [!DNL Target] -Mechanismus, der die Orte, Zielgruppen und Angebote miteinander verknüpft, sodass [!DNL Target] bei einer Anforderung aus der App mit dem personalisierten Inhalt antwortet. Wir erstellen zwei Personalisierungsaktivitäten in [!DNL Target] und überprüfen, ob personalisierte Inhalte dem richtigen Benutzer zum richtigen Zeitpunkt und an der richtigen Stelle angezeigt werden.

## Lernziele

Am Ende dieser Lektion können Sie:

* Erstellen von Aktivitäten in Adobe Target
* Überprüfen der Aktivitäten in der Beispielanwendung

## Erstellen von Aktivitäten in Adobe Target

Erfahren Sie, wie Sie die Aktivitäten &quot;Benutzer einbinden&quot;und &quot;Kontextuelle Angebote&quot;erstellen.

### Erste Aktivität - &quot;Benutzer einbinden&quot;

Im Folgenden finden Sie eine Zusammenfassung der von uns erstellten Aktivität:

| Zielgruppe | Positionen | Angebote |
|---|---|---|
| Neue Mobile App-Benutzer | wetravel_engage_home, wetravel_engage_search | Startseite: Neue Benutzer einbinden, Suche: Neue Benutzer einbinden |
| Zurückgeben von App-Benutzern | wetravel_engage_home, wetravel_engage_search | Startseite: Wiederkehrende Benutzer, default_content |

Führen Sie in der Oberfläche von [!DNL Target] folgende Schritte aus:

1. Wählen Sie **[!UICONTROL Activities]** > **[!UICONTROL Create Activity]** > **[!UICONTROL Experience Targeting]** aus.

   ![Aktivität erstellen](assets/activity_create_1.jpg)

1. Klicken Sie auf **[!UICONTROL Mobile App]**.
1. Wählen Sie den Wert **[!UICONTROL Form composer]** aus.
1. Wählen Sie Ihren Arbeitsbereich aus (der Arbeitsbereich, den Sie in früheren Lektionen verwendet haben).
1. Wählen Sie Ihre Eigenschaft aus (dieselbe Eigenschaft wie in früheren Lektionen).
1. Klicken Sie auf **[!UICONTROL Next]**.

   ![Aktivität erstellen](assets/activity_create_2.jpg)

1. Ändern Sie den Aktivitätstitel in &quot;**[!UICONTROL Engage Users]**&quot;.
1. Wählen Sie **[!UICONTROL ellipsis]** > **[!UICONTROL Change Audience]** aus.
   ![Neue Benutzer der mobilen App ändern die Zielgruppe](assets/activity_create_3.jpg)
1. Setzen Sie die Zielgruppe auf &quot;**[!UICONTROL New Mobile App Users]**&quot;.
1. Klicken Sie auf **[!UICONTROL Done]**.
   ![Neue Audience für Benutzer mobiler Apps](assets/activity_create_4.jpg)

1. Ändern Sie den Standort in _wetravel_engage_home_.
1. Wählen Sie den Dropdown-Pfeil neben Standardinhalt und dann **[!UICONTROL Change HTML Offer]** aus.

   ![Neue Audience für Benutzer mobiler Apps](assets/activity_create_5.jpg)

1. Wählen Sie das Angebot **[!UICONTROL Home: Engage New Users]** aus.
1. Wählen Sie **[!UICONTROL Done]** aus.

   ![Neue Audience für Benutzer mobiler Apps](assets/activity_create_6.jpg)

1. Wählen Sie **[!UICONTROL Add Location]** aus.
   ![Neue Audience für Benutzer mobiler Apps](assets/activity_create_7.jpg)

1. Wählen Sie den Standort _wetravel_engage_search_ aus.
1. Ändern Sie das HTML-Angebot.

   ![Neue Audience für Benutzer mobiler Apps](assets/activity_create_8.jpg)

1. Wählen Sie das Angebot **[!UICONTROL Search: Engage New Users]** aus.
1. Klicken Sie auf **[!UICONTROL Done]**.

   ![Neue Audience für Benutzer mobiler Apps](assets/activity_create_9.jpg)

Sie haben gerade eine Zielgruppe mit Standorten und Angeboten verbunden und damit das personalisierte Erlebnis für die neuen App-Benutzer geschaffen! Das Erlebnis sollte nun wie folgt aussehen:

![Erlebnis eines endgültigen ](assets/activity_engage_users_a_final.jpg)

Erstellen Sie nun ein Erlebnis für wiederkehrende Benutzer mobiler Apps:

1. Wählen Sie links **[!UICONTROL Add Experience Targeting]** aus.
1. Wählen Sie die Zielgruppe **[!UICONTROL Returning Mobile App Users]** aus.
1. Wählen Sie **[!UICONTROL Done]** aus.
   ![Returning Mobile App Users Audience](assets/activity_create_11.jpg)

Verwenden Sie nun denselben Prozess, den wir zuvor zur Konfiguration des neuen Erlebnisses verwendet haben. Die Konfiguration für das Erlebnis &quot;Returning Mobile App Users&quot;sollte wie folgt aussehen:

![Returning Mobile App Users Final](assets/activity_engage_users_b_final.jpg)

Fahren wir mit dem nächsten Bildschirm im Setup fort:

1. Klicken Sie auf **[!UICONTROL Next]** , um zum Bildschirm **[!UICONTROL Targeting]** zu gelangen.
1. Verwenden Sie die Standardeinstellungen für das Targeting. Wenn Sie Erlebnisse für Zielgruppen hatten, die sich überlappen (z. B. _New York-Benutzer_ und _Erstmalige Benutzer_), können Sie die Prioritätsreihenfolge auf diesem Bildschirm festlegen.
1. Klicken Sie auf **[!UICONTROL Next]** , um zu **[!UICONTROL Goals & Settings]** zu wechseln.

   ![Benutzeraktivität einbinden - Targeting-Standard](assets/activity_engage_users_targeting.jpg)

Schließen wir nun die Aktivitätseinrichtung ab:

1. Setzen Sie die **[!UICONTROL Primary Goal]** auf **[!UICONTROL Conversion]**.
1. Setzen Sie die Aktion auf &quot;**[!UICONTROL Viewed an mbox]**&quot;> &quot;_wetravel_context_dest_&quot;(Da sich diese Position auf dem Bestätigungsbildschirm befindet, können wir sie zum Messen von Konversionen verwenden).

   ![Aktivität &quot;Benutzer einbinden&quot;- Ziele](assets/activity_create_12.jpg)

1. Behalten Sie alle anderen Bildschirmeinstellungen auf die Standardeinstellungen bei.
1. Klicken Sie auf **[!UICONTROL Save & Close]** , um die Aktivität zu speichern.
1. Aktivieren Sie die **[!UICONTROL Activity]** auf dem nächsten Bildschirm.

![Erlebnis B-Zielgruppe](assets/activity_create_13.jpg)

Unsere erste Aktivität ist jetzt live und kann getestet werden!

### Zweite Aktivität - &quot;Kontextuelle Angebote&quot;

Im Folgenden finden Sie eine Zusammenfassung der zweiten Aktivität, die wir erstellen werden:

| Zielgruppe | Standort | Angebote |
| --- | --- | --- |
| Ziel: San Diego | wetravel_context_dest | Förderung von San Diego |
| Ziel: Los Angeles | wetravel_context_dest | Promotion für Los Angeles |

Wiederholen Sie den obigen Vorgang für die nächste Aktivität - &quot;Kontextuelle Angebote&quot;. Die endgültige Konfiguration für beide Erlebnisse ist unten dargestellt:

#### San Diego

![ Kontextuelle Angebote - Erlebnis A](assets/activity_contextual_a_final.jpg)

#### Los Angeles

![Kontextuelle Angebote - Erlebnis B](assets/activity_contextual_b_final.jpg)

Im Schritt Ziele und Einstellungen ändern wir das Primäre Ziel in den Ort auf dem Buchungsbestätigungsbildschirm:

1. Setzen Sie unter dem **[!UICONTROL Reporting Settings]** die **[!UICONTROL Primary Goal]** auf **[!UICONTROL Conversion]**.
1. Setzen Sie die Aktion auf &quot;**[!UICONTROL Viewed an mbox]**&quot;> &quot;_wetravel_context_dest_&quot;(in dieser Aktivität ist diese Metrik im Grunde genommen nicht sinnvoll, da sie auch derselbe Ort ist, der das Erlebnis bereitstellt).
1. Klicken Sie auf **[!UICONTROL Save & Close]**.

![Kontextuelle Angebote - Erlebnis](assets/activity_create_14.jpg)

Aktivieren Sie die Aktivität auf dem nächsten Bildschirm.

Jetzt ist unsere zweite Aktivität live und kann getestet werden!

## Validieren des Startangebots

Führen Sie den Emulator aus und beobachten Sie, ob das erste Angebot unten auf dem Startbildschirm angezeigt wird. Wenn Sie ein wiederkehrender Benutzer mit 5 oder mehr App-Starts sind, wird das Angebot _welcome back_ angezeigt. Wenn Sie ein neuer Benutzer sind (weniger als 5 App-Starts), sollte die Meldung _neuer Benutzer_ angezeigt werden:

![Validieren des Startangebots](assets/layout_home_validate.jpg)

Wenn das neue Benutzerangebot nicht angezeigt wird, versuchen Sie, die Daten für Ihren Emulator zu löschen. Dadurch wird der App-Starter beim nächsten Start auf 1 zurückgesetzt. Dies geschieht unter **[!UICONTROL Tools]** > **[!UICONTROL AVD Manager]**. Möglicherweise müssen Sie auch Android Studio neu starten, wenn Logcat nicht ordnungsgemäß funktioniert:

![Emulator wischen](assets/layout_home_validate_avd_wipe.jpg)

Sie können die Antwort auch in Logcat überprüfen, indem Sie nach _wetravel_engage_home_ filtern:

![Validieren des Startangebots - logcat](assets/layout_home_validate_logcat.jpg)

## Überprüfen des Suchangebots

Wählen Sie **[!UICONTROL San Jose]** als Ihren **[!UICONTROL Departure]** und **[!UICONTROL San Diego]** als Ihren **[!UICONTROL Destination]** und klicken Sie auf **[!UICONTROL Find Bus]**, um nach verfügbaren Bussen zu suchen.

Auf dem Ergebnisbildschirm sollte die Meldung _Filter verwenden_ angezeigt werden. Wenn Sie ein wiederkehrender Benutzer mit 5 oder mehr App-Starts sind, wird hier keine Nachricht angezeigt, da für diesen Ort (der leer ist) Standardinhalt festgelegt ist:

![Suchangebot validieren](assets/layout_search_validate.jpg)

## Validieren der kontextuellen Angebote auf dem Dankesbildschirm

Fahren Sie nun mit dem Buchungsvorgang fort:

* Wählen Sie auf dem Ergebnisbildschirm einen Bus aus.
* Wählen Sie einen Platz auf dem Checkout-Bildschirm aus.
* Wählen Sie **[!UICONTROL Credit Card]** auf dem Zahlungsbildschirm aus (lassen Sie die Zahlungsinformationen leer - es findet keine tatsächliche Buchung statt).

Da San Diego als Ziel ausgewählt wurde, sollte das Angebotsbanner _DJ SAM_ auf dem Bestätigungsbildschirm angezeigt werden:

![Validieren des Kontextangebots - San Diego](assets/layout_context_san_diego.jpg)

Wählen Sie nun **[!UICONTROL Done]** aus und versuchen Sie eine weitere Buchung mit Los Angeles als Ziel. Auf dem Bestätigungsbildschirm sollte das Banner _Universal Studios_ angezeigt werden:

![Validieren des Kontextangebots - Los Angeles](assets/layout_context_los_angeles.jpg)

## Schlussfolgerung 

Herzlichen Glückwunsch! Dadurch wird der Hauptteil des Tutorials zum Adobe Target-SDK 4.x für Android beendet. Sie verfügen jetzt über die Fähigkeiten, Personalisierung in Android-Apps zu implementieren! Sie können diese Dokumentation und Demo-App als Referenz für Ihre künftigen Projekte nutzen.

Weiter: Die Funktionskennzeichnung ist eine weitere Funktion, die mit Adobe Target in Android implementiert werden kann. Weitere Informationen zur Funktionskennzeichnung finden Sie in der nächsten Lektion.

**[WEITER : Funktionskennzeichnung >](feature-flagging.md)**
