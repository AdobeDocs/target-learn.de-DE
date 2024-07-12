---
title: Funktionskennzeichnung
description: Adobe Target kann verwendet werden, um mit UX-Funktionen wie Farbe, Kopieren, Schaltflächen, Text und Bildern zu experimentieren und diese Funktionen für bestimmte Zielgruppen bereitzustellen.
role: Developer
level: Intermediate
topic: Mobile, Personalization
feature: Implement Mobile
doc-type: tutorial
kt: 3040
exl-id: 034d13f2-63b1-44b0-b3dc-867efe37672f
source-git-commit: 342e02562b5296871638c1120114214df6115809
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 1%

---

# Funktionskennzeichnung

Produkteigentümer mobiler Apps benötigen die Flexibilität, um neue Funktionen in ihrer App einzuführen, ohne in mehrere App-Versionen investieren zu müssen. Sie können auch Funktionen schrittweise auf einen Prozentsatz der Benutzerbasis einführen, um die Effektivität zu testen. Adobe Target kann verwendet werden, um mit UX-Funktionen wie Farbe, Kopieren, Schaltflächen, Text und Bildern zu experimentieren und diese Funktionen für bestimmte Zielgruppen bereitzustellen.

In dieser Lektion erstellen wir ein Angebot mit einer &quot;Feature Flag&quot;-Funktion, das als Trigger zur Aktivierung bestimmter App-Funktionen verwendet werden kann.

## Lernziele

Am Ende dieser Lektion können Sie:

* Hinzufügen eines neuen Speicherorts zur Anfrage zum Vorabruf für den Batch
* Erstellen einer [!DNL Target] -Aktivität mit einem Angebot, das als Feature Flag verwendet wird
* Laden und Überprüfen des Feature Flag-Angebots in Ihrer App

## Hinzufügen eines neuen Speicherorts zur Vorabruf-Anfrage zur Startaktivität

In der Demo-App aus unseren vorherigen Lektionen fügen wir der Vorabruf-Anfrage in der Startaktivität einen neuen Speicherort namens &quot;wetravel_feature_flag_recs&quot;hinzu und laden ihn mit einer neuen Java-Methode auf den Bildschirm.

>[!NOTE]
>
>Einer der Vorteile der Verwendung einer Vorabruf-Anfrage besteht darin, dass das Hinzufügen einer neuen Anfrage keinen zusätzlichen Netzwerkaufwand verursacht oder zusätzliche Ladevorgänge verursacht, da die Anfrage in der Vorabruf-Anfrage gepackt ist

Überprüfen Sie zunächst, ob die Konstante wetravel_feature_flag_recs in der Datei Constant.java hinzugefügt wird:

![Funktionsmarkierungskonstante hinzufügen](assets/feature_flag_constant.jpg)

Im Folgenden finden Sie den Code:

```java
public static final String wetravel_feature_flag_recs = "wetravel_feature_flag_recs";
```

Fügen Sie nun den Speicherort zur Vorabruf-Anfrage hinzu und laden Sie eine neue Funktion namens `processFeatureFlags()`:

![Funktionskennzeichnungscode](assets/feature_flag_code.jpg)

Hier finden Sie den vollständigen aktualisierten Code:

```java
public void targetPrefetchContent() {
    List<TargetPrefetchObject> prefetchList = new ArrayList<>();

    Map<String, Object> params1;
    params1 = new HashMap<String, Object>();
    params1.put("at_property", "7962ac68-17db-1579-408f-9556feccb477");

    prefetchList.add(Target.createTargetPrefetchObject(Constant.wetravel_engage_home, params1));
    prefetchList.add(Target.createTargetPrefetchObject(Constant.wetravel_engage_search, params1));
    prefetchList.add(Target.createTargetPrefetchObject(Constant.wetravel_feature_flag_recs, params1));

    Target.TargetCallback<Boolean> prefetchStatusCallback = new Target.TargetCallback<Boolean>() {
        @Override
        public void call(final Boolean status) {
            HomeActivity.this.runOnUiThread(new Runnable() {
                @Override
                public void run() {
                    String cachingStatus = status ? "YES" : "NO";
                    System.out.println("Received Response from prefetch : " + cachingStatus);
                    engageMessage();
                    processFeatureFlags();
                    setUp();

                }
            });
        }};
    Target.prefetchContent(prefetchList, null, prefetchStatusCallback);
}

public void processFeatureFlags() {
    Target.loadRequest(Constant.wetravel_feature_flag_recs, "", null, null, null,
            new Target.TargetCallback<String>(){
                @Override
                public void call(final String s) {
                    runOnUiThread(new Runnable() {
                        @Override
                        public void run() {
                            System.out.println("Feature Flags : " + s);
                            if(s != null && !s.isEmpty()) {
                                //enable or disable features
                            }
                        }
                    });
                }
            });
}
```

### Überprüfen der Anforderung der Funktionskennzeichnung

Nachdem der Code hinzugefügt wurde, führen Sie den Emulator auf der Startaktivität aus und sehen Sie sich Logcat für die aktualisierte Antwort an:

![Position der Funktionsmarkierung überprüfen](assets/feature_flag_code_logcat.jpg)

## Erstellen eines JSON-Angebots mit Funktionskennzeichnung

Jetzt erstellen wir ein einfaches JSON-Angebot, das als Flag oder Trigger für eine bestimmte Zielgruppe fungiert - die Zielgruppe, die das Feature-Rollout in ihrer App erhalten würde. Erstellen Sie in der Benutzeroberfläche von [!DNL Target] ein neues Angebot:

![JSON-Angebot &quot;Feature Flag erstellen&quot;](assets/feature_flag_json_offer.jpg)

Nennen wir es &quot;Feature Flag v1&quot;mit dem Wert {&quot;enable&quot;:1}

![feature_flag_v1 JSON-Angebot](assets/feature_flag_json_name.jpg)

## Erstellen einer Aktivität

Erstellen wir nun eine A/B-Test -Aktivität mit diesem Angebot. Ausführliche Anweisungen zum Erstellen einer Aktivität finden Sie in der vorherigen Lektion. Für dieses Beispiel benötigt die Aktivität nur eine Zielgruppe. In einem Live-Szenario möchten Sie möglicherweise spezifische benutzerdefinierte Zielgruppen für bestimmte Feature Rollouts erstellen und dann die Aktivität so einstellen, dass sie diese Zielgruppen verwendet. In diesem Beispiel weisen wir Traffic nur 50/50 zu (50 % für Besucher, denen die Funktion aktualisiert wird, und 50 % für Besucher, denen ein Standarderlebnis angezeigt wird). Dies ist die Konfiguration für die Aktivität:

1. Benennen Sie die Aktivität mit &quot;Feature Flag&quot;.
1. Wählen Sie den Speicherort &quot;wetravel_feature_flag_recs&quot;
1. Ändern Sie den Inhalt in das JSON-Angebot &quot;Feature Flag v1&quot;

   ![Konfiguration der Funktionskennzeichnung ](assets/feature_flag_activity.jpg)

1. Klicken Sie auf **[!UICONTROL Add Experience]** , um Erlebnis B hinzuzufügen.
1. Behalten Sie den Speicherort &quot;wetravel_feature_flag_recs&quot;bei.
1. Behalten Sie **[!UICONTROL Default Content]** für den Inhalt bei
1. Klicken Sie auf **[!UICONTROL Next]** , um zum Bildschirm [!UICONTROL Targeting] zu gelangen.

   ![Konfiguration der Funktionskennzeichnung ](assets/feature_flag_activity_2.jpg)

1. Überprüfen Sie auf dem Bildschirm &quot;[!UICONTROL Targeting]&quot;, ob die Methode &quot;[!UICONTROL Traffic Allocation]&quot; auf die Standardeinstellung (Manuell) eingestellt ist und dass jedem Erlebnis die standardmäßige Zuordnung von 50 % zugewiesen ist. Wählen Sie **[!UICONTROL Next]** aus, um zu **[!UICONTROL Goals & Settings]** zu wechseln.

   ![Konfiguration der Funktionskennzeichnung ](assets/feature_flag_activity_3.jpg)

1. Setzen Sie die **[!UICONTROL Primary Goal]** auf **[!UICONTROL Conversion]**.
1. Setzen Sie die Aktion auf &quot;**[!UICONTROL Viewed an Mbox]**&quot;. Wir verwenden den Standort &quot;wetravel_context_dest&quot;(da dieser Ort sich auf dem Bestätigungsbildschirm befindet, können wir ihn verwenden, um zu sehen, ob die neue Funktion zu mehr Konversionen führt).
1. Klicken Sie auf **[!UICONTROL Save & Close]**.

   ![Konfiguration der Funktionskennzeichnung ](assets/feature_flag_activity_4.jpg)

die Aktivität aktivieren.

## Überprüfen der Aktivität &quot;Funktionskennzeichnung&quot;

Verwenden Sie jetzt den Emulator, um die Anforderung zu überwachen. Da das Targeting auf 50 % der Benutzer festgelegt wird, wird eine Antwort mit dem Feature Flag zu 50 % mit dem Wert `{enable:1}` angezeigt.

![Validierung der Funktionskennzeichnung](assets/feature_flag_validation.jpg)

Wenn der Wert `{enable:1}` nicht angezeigt wird, bedeutet das, dass Sie nicht für das Erlebnis angesprochen wurden. Um die Anzeige des Angebots zu erzwingen, haben Sie als temporärer Test folgende Möglichkeiten:

1. Deaktivieren Sie die Aktivität.
1. Ändern Sie die Traffic-Zuordnung beim neuen Feature-Erlebnis auf 100 %.
1. Speichern und reaktivieren Sie.
1. Wischen Sie die Daten auf Ihrem Emulator ab und starten Sie dann die App neu.
1. Das Angebot sollte jetzt den Wert `{enable:1}` zurückgeben.

In einem Live-Szenario kann die Antwort `{enable:1}` verwendet werden, um eine benutzerspezifischere Logik in Ihrer App zu aktivieren, um den spezifischen Funktionssatz anzuzeigen, den Sie Ihrer Zielgruppe zeigen möchten.

## Schlussfolgerung 

Gut gemacht! Sie verfügen jetzt über die erforderlichen Fähigkeiten, um Funktionen für bestimmte Zielgruppen einzuführen.
