---
title: Feature Flag
description: Adobe Target kann verwendet werden, um mit UX-Funktionen wie Farbe, Kopie, Schaltflächen, Text und Bildern zu experimentieren und diese Funktionen für bestimmte Zielgruppen bereitzustellen.
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

# Feature Flag

Produktverantwortliche für Mobile Apps benötigen die Flexibilität, neue Funktionen in ihrer App bereitzustellen, ohne in mehrere App-Versionen investieren zu müssen. Möglicherweise möchten sie auch Funktionen schrittweise auf einen Prozentsatz der Benutzerbasis ausweiten, um die Effektivität zu testen. Adobe Target kann verwendet werden, um mit UX-Funktionen wie Farbe, Kopie, Schaltflächen, Text und Bildern zu experimentieren und diese Funktionen für bestimmte Zielgruppen bereitzustellen.

In dieser Lektion erstellen wir ein Angebot mit einer „Feature Flag“, das als Trigger verwendet werden kann, um bestimmte App-Funktionen zu aktivieren.

## Lernziele

Am Ende dieser Lektion haben Sie folgende Möglichkeiten:

* Hinzufügen eines neuen Speicherorts zur Batch-Vorabrufanfrage
* Erstellen einer [!DNL Target] Aktivität mit einem Angebot, das als Feature Flag verwendet wird
* Laden und Validieren des Feature Flag-Angebots in der App

## Hinzufügen eines neuen Speicherorts zur Vorabruf-Anfrage an die Startseiten-Aktivität

In der Demo-App aus unseren vorherigen Lektionen fügen wir der Vorabruf-Anfrage in der Startseiten-Aktivität einen neuen Speicherort namens „travel_feature_flag_recs“ hinzu und laden ihn mit einer neuen Java-Methode auf den Bildschirm.

>[!NOTE]
>
>Einer der Vorteile der Verwendung einer Prefetch-Anfrage besteht darin, dass das Hinzufügen einer neuen Anfrage keinen zusätzlichen Netzwerkaufwand verursacht oder zusätzliche Lasten verursacht, da die Anfrage in der Prefetch-Anfrage verpackt ist

Überprüfen Sie zunächst, ob die Konstante wetravel_feature_flag_recs in der Datei Constant.java hinzugefügt wird:

![Feature Flag-Konstante hinzufügen](assets/feature_flag_constant.jpg)

Hier ist der Code:

```java
public static final String wetravel_feature_flag_recs = "wetravel_feature_flag_recs";
```

Fügen Sie nun den Speicherort zur Vorabruf-Anfrage hinzu und laden Sie eine neue Funktion namens `processFeatureFlags()`:

![Feature Flag-Code](assets/feature_flag_code.jpg)

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

### Validieren der Feature Flag-Anfrage

Führen Sie nach dem Hinzufügen des Codes den Emulator auf der Startseite aus und beobachten Sie die Protokolldatei auf die aktualisierte Antwort:

![Position des Feature Flags überprüfen](assets/feature_flag_code_logcat.jpg)

## Erstellen eines JSON-Angebots für Feature Flag

Wir erstellen nun ein einfaches JSON-Angebot, das als Markierung oder Trigger für eine bestimmte Zielgruppe dient - die Zielgruppe, für die der Rollout der Funktionen in ihrer App erfolgen würde. Erstellen Sie in der [!DNL Target] ein neues Angebot:

![JSON-Angebot für Feature Flag erstellen](assets/feature_flag_json_offer.jpg)

Nennen wir sie „Feature Flag v1“ mit dem Wert {„enable“:1}

![feature_flag_v1 JSON-Angebot](assets/feature_flag_json_name.jpg)

## Erstellen einer Aktivität

Erstellen wir nun mit diesem Angebot eine A/B-Test -Aktivität. Detaillierte Anweisungen zum Erstellen einer Aktivität finden Sie in der vorherigen Lektion. Die Aktivität benötigt für dieses Beispiel nur eine Audience. In einem Live-Szenario können Sie bestimmte benutzerdefinierte Zielgruppen für bestimmte Funktions-Rollouts erstellen und dann die Aktivität so einstellen, dass diese Zielgruppen verwendet werden. In diesem Beispiel weisen wir nur Traffic von 50/50 zu (50 % den Besuchern, die die Funktionsaktualisierungen sehen würden, und 50 % den Besuchern, die ein Standarderlebnis sehen würden). Im Folgenden finden Sie die Konfiguration der Aktivität:

1. Benennen Sie die Aktivität mit „Feature Flag“
1. Speicherort „WeTravel_Feature_Flag_Recs“ auswählen
1. Ändern des Inhalts in das JSON-Angebot „Feature Flag v1“

   ![Aktivitätskonfiguration für Feature Flag](assets/feature_flag_activity.jpg)

1. Klicken Sie auf **[!UICONTROL Add Experience]** , um Erlebnis B hinzuzufügen.
1. Verlassen Sie den Speicherort „WeTravel_Feature_Flag_Recs“
1. **[!UICONTROL Default Content]** für den Inhalt belassen
1. Klicken Sie auf **[!UICONTROL Next]** , um zum Bildschirm [!UICONTROL Targeting] zu gelangen

   ![Aktivitätskonfiguration für Feature Flag](assets/feature_flag_activity_2.jpg)

1. Stellen Sie auf dem Bildschirm [!UICONTROL Targeting] sicher, dass die [!UICONTROL Traffic Allocation] auf die Standardeinstellung (Manuell) eingestellt ist und dass für jedes Erlebnis die standardmäßige 50-%-Zuordnung gilt. Wählen Sie **[!UICONTROL Next]** aus, um zu **[!UICONTROL Goals & Settings]** zu wechseln.

   ![Aktivitätskonfiguration für Feature Flag](assets/feature_flag_activity_3.jpg)

1. Legen Sie die **[!UICONTROL Primary Goal]** auf **[!UICONTROL Conversion]** fest.
1. Legen Sie die Aktion auf **[!UICONTROL Viewed an Mbox]** fest. Wir verwenden den Speicherort „weTravel_context_dest“ (da dieser Speicherort auf dem Bestätigungsbildschirm ist, können wir ihn verwenden, um zu sehen, ob die neue Funktion zu weiteren Konversionen führt).
1. Klicken Sie auf **[!UICONTROL Save & Close]**.

   ![Aktivitätskonfiguration für Feature Flag](assets/feature_flag_activity_4.jpg)

die Aktivität aktivieren.

## Validieren der Feature Flag-Aktivität

Verwenden Sie nun den Emulator, um nach der Anfrage zu suchen. Da wir die Zielgruppenbestimmung auf 50 % der Benutzenden festgelegt haben, gibt es 50 %. Die Antwort mit dem Feature Flag zeigt den `{enable:1}` Wert an.

![Feature Flag-Validierung](assets/feature_flag_validation.jpg)

Wenn Sie den `{enable:1}` nicht sehen, bedeutet das, dass Sie für das Erlebnis nicht angesprochen wurden. Um das Anzeigen des Angebots zu erzwingen, haben Sie folgende Möglichkeiten:

1. Deaktivieren Sie die Aktivität.
1. Ändern Sie die Traffic-Zuordnung im neuen Funktionserlebnis auf 100 %.
1. Speichern und erneut aktivieren.
1. Löschen Sie die Daten auf dem Emulator und starten Sie die App neu.
1. Das Angebot sollte jetzt den `{enable:1}` zurückgeben.

In einem Live-Szenario kann die `{enable:1}`-Antwort verwendet werden, um in Ihrer App eine stärker benutzerdefinierte Logik zu aktivieren und den spezifischen Funktionssatz anzuzeigen, den Sie Ihrer Zielgruppe anzeigen möchten.

## Schlussfolgerung 

Gut gemacht! Jetzt verfügen Sie über die erforderlichen Fähigkeiten, um Funktionen für bestimmte Benutzergruppen bereitzustellen.
