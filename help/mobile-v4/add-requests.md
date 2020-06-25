---
title: Hinzufügen Adobe Target-Anfragen
description: 'Das Adobe Mobile Services SDK (v4) bietet Adobe Target-Methoden und -Funktionen, mit denen Sie Ihre App mit unterschiedlichen Benutzererlebnissen personalisieren können.   '
feature: mobile
kt: 3040
audience: developer
doc-type: tutorial
activity-type: implement
translation-type: tm+mt
source-git-commit: b331bb29c099bd91df27300ebe199cafa12516db
workflow-type: tm+mt
source-wordcount: '1804'
ht-degree: 0%

---


# Hinzufügen Adobe Target-Anfragen

Das Adobe Mobile Services SDK (v4) bietet Adobe Target-Methoden und -Funktionen, mit denen Sie Ihre App mit unterschiedlichen Benutzererlebnissen personalisieren können. In der Regel werden eine oder mehrere Anfragen von der App an das Adobe Target gesendet, um den personalisierten Inhalt abzurufen und die Auswirkungen dieses Inhalts zu messen.

In dieser Lektion bereiten Sie die App &quot;We.Travel&quot;für die Personalisierung vor, indem Sie [!DNL Target] Anforderungen implementieren.

## Voraussetzungen 

Stellen Sie sicher, dass Sie die Beispielanwendung [herunterladen und aktualisieren](download-and-update-the-sample-app.md).

## Lernziele

Am Ende dieser Lektion können Sie:

* Zwischenspeichern mehrerer [!DNL Target] Angebot (d. h. personalisierter Inhalt) mithilfe einer Batch-Vorab-Anfrage
* Voreingestellte [!DNL Target] Speicherorte laden
* Einen [!DNL Target] Ort in Echtzeit laden (nicht vorab abgerufen)
* Vorab abgerufene Speicherorte aus dem Cache löschen
* Überprüfen von bereits abgerufenen und Echtzeitanforderungen

## Terminologie  

Nachstehend finden Sie einige der wichtigsten Target-Terminologie, die wir im weiteren Verlauf dieses Tutorials verwenden werden.

* **Anforderung:**  eine Netzwerkanforderung an die Adobe Target-Server
* **Angebot:**  ein Codefragment oder ein anderer textbasierter Inhalt, der in der [!DNL Target] Benutzeroberfläche (oder mit API) definiert ist und in der Antwort bereitgestellt wird. Normalerweise JSON, wenn es in nativen mobilen Apps verwendet [!DNL Target] wird.
* **Ort:**  einen benutzerdefinierten Namen, der einer Anforderung zugewiesen wird und in der [!DNL Target] Oberfläche verwendet wird, um Angebot bestimmten Anforderungen zuzuordnen
* **Stapelanforderung:**  eine einzelne Anforderung mit mehreren Speicherorten
* **Anfrage vorab abrufen:**  eine einzige Anforderung, die Angebot abruft und sie im Arbeitsspeicher zwischenspeichert, um sie in der App für die Zukunft verwenden zu können
* **Stapelvorab-Anfrage:**  eine einzige Anforderung, die Angebot für mehrere Standorte im Voraus abruft
* **Audience:**  eine Gruppe von Besuchern, die in der [!DNL Target] [!DNL Target] Oberfläche definiert sind oder für die andere Adobe-Anwendungen freigegeben wurden (z. B. &quot;iPhone X-Besucher&quot;, &quot;Besucher in Kalifornien&quot;, &quot;First App Open&quot;)
* **Aktivität:**  ein in der [!DNL Target] Benutzeroberfläche (oder mit API) definiertes [!DNL Target] Konstrukt, das Orte, Angebot und Audiencen miteinander verknüpft, um ein personalisiertes Erlebnis zu erstellen

## Hinzufügen einer Stapelvorab-Anfrage

Die erste Anforderung, die wir in We.Travel implementieren werden, ist eine Batch-Anfrage mit zwei [!DNL Target] Stellen auf dem Startbildschirm. In einer späteren Lektion konfigurieren wir Angebot für diese Orte, die Meldungen anzeigen, um neue Benutzer durch den Buchungsprozess zu führen.

Eine Anforderung zum vorherigen Abrufen ruft [!DNL Target] Inhalte so minimal wie möglich ab, indem die Adobe Target-Server-Antwort (Angebot) zwischengespeichert wird. Bei einer Stapelvorab-Anfrage werden mehrere Angebot abgerufen und zwischengespeichert, die jeweils mit einem anderen Speicherort verknüpft sind. Alle zuvor abgerufenen Speicherorte werden auf dem Gerät zwischengespeichert, damit sie in der Benutzersitzung verwendet werden können. Wenn Sie mehrere Speicherorte auf dem Startbildschirm aufrufen, können wir Angebot abrufen, die später verwendet werden, wenn der Besucher durch die App navigiert. Weitere Informationen zu Prefetch-Methoden finden Sie in der [Dokumentation](https://docs.adobe.com/content/help/en/mobile-services/android/target-android/c-mob-target-prefetch-android.html) zum Prefetch.

### Hinzufügen der Stapelvorab-Anfrage

Aktualisieren wir den HomeActivity-Controller (den Quellcode des Startbildschirms), der sich unter &quot;app > main > java > com.wetravel > Controller&quot;befindet. Die beiden Codeblöcke werden in rot dargestellt:

Wir werden mit dem HomeActivity-Controller (dem Quellcode des Startbildschirms) Beginn machen, der sich unter App > main > java > com.wetravel > Controller befindet.

Die beiden Codeblöcke werden in rot dargestellt:

![HomeActivity Prefetch-Code](assets/homeactivity.jpg)

Blättern Sie nach unten zum Ende des HomeActivity-Codes und fügen Sie den unten angegebenen Code nach der `setHeader()` Funktion hinzu und *ersetzen* Sie die aktuelle `onResume()` Funktion:

```java
@Override
protected void onResume() {
    super.onResume();
    targetPrefetchContent();
}

public void targetPrefetchContent() {
    List<TargetPrefetchObject> prefetchList = new ArrayList<>();
    prefetchList.add(Target.createTargetPrefetchObject(Constant.wetravel_engage_home, null));
    prefetchList.add(Target.createTargetPrefetchObject(Constant.wetravel_engage_search, null));
    Target.TargetCallback<Boolean> prefetchStatusCallback = new Target.TargetCallback<Boolean>() {
        @Override
        public void call(final Boolean status) {
            HomeActivity.this.runOnUiThread(new Runnable() {
                @Override
                public void run() {
                    String cachingStatus = status ? "YES" : "NO";
                    System.out.println("Received Response from prefetch : " + cachingStatus);
                    setUp();

                }
            });
        }};
    Target.prefetchContent(prefetchList, null, prefetchStatusCallback);
}
```

Ihre IDE wird Sie wahrscheinlich darauf hinweisen, dass die [!DNL Target] Klassen nicht in der Datei importiert wurden. Importieren Sie die [!DNL Target] Klassen am oberen Rand des HomeActivity-Controllers, wie unten dargestellt:

```java
import com.adobe.mobile.Target;
import com.adobe.mobile.TargetPrefetchObject;
```

![Target-Klassen importieren](assets/import.jpg)

Wahrscheinlich werden auch Fehler für &quot;Die Symbolvariable wetravel_engagement_home kann nicht gefunden werden&quot;und &quot;Die Symbolvariable wetravel_engagement_search kann nicht gefunden werden&quot;angezeigt. Hinzufügen Sie diese in die `Constant.java` Datei (in App > src > main > java > com > wetravel > Utils):

```java
public static final String wetravel_engage_home = "wetravel_engage_home";
public static final String wetravel_engage_search = "wetravel_engage_search";
```

![Hinzufügen Sie die Ortsnamen in die Datei &quot;Constant.java&quot;.](assets/constants.jpg)

### Erklärung zum Anforderungscode für die Stapelvorbereitung

| Code | Beschreibung |
|--- |--- |
| `targetPrefetchContent()` | Eine benutzerdefinierte Funktion (nicht Teil des SDK), die [!DNL Target] Methoden zum Abrufen und Zwischenspeichern von zwei [!DNL Target] Speicherorten verwendet. |
| `prefetchContent()` | Die [!DNL Target] SDK-Methode, die die Anforderung zum vorherigen Abrufen sendet |
| `Constant.wetravel_engage_home` | Vorab abgerufener [!DNL Target] Ortsname, der den Angebot auf dem Startbildschirm anzeigt |
| `Constant.wetravel_engage_search` | Vorab abgerufener [!DNL Target] Ortsname, der den Angebot im Bildschirm &quot;Suchergebnisse&quot;anzeigt. Da es sich um eine zweite Position im Prefetch handelt, wird diese Prefetch-Anforderung als &quot;Prefetch-Batch-Anforderung&quot;bezeichnet. |
| setUp() | Eine benutzerdefinierte Funktion, die den Startbildschirm der App nach dem vorherigen Abrufen der [!DNL Target] Angebot rendert |

### Über Asynchrone und synchrone

Mit dem soeben implementierten Code erfolgt die Anfrage zum Vorababruf als synchroner Blockieraufruf, kurz bevor der Startbildschirm angezeigt wird. Als der neue Code in den HomeActivity-Controller eingefügt wurde, wurde die `setUp()` Funktionsausführung von der `onResume()` Funktion bis nach der Target-Anforderung verschoben. Dies kann nützlich sein, wenn Sie Inhalte beim ersten Öffnen der App personalisieren möchten, da dadurch sichergestellt wird, dass personalisierte Inhalte von den Target-Servern zurückgegeben (oder abgelaufen) werden, bevor der erste Bildschirm angezeigt wird. Damit die Anforderungen asynchron geladen werden können (im Hintergrund), müssen Sie stattdessen `setUp()` innerhalb der `onCreate()` Funktion aufrufen.

### Validieren der Stapelvorab-Anfrage

Erstellen Sie die App neu und öffnen Sie den Android-Emulator. (Die folgenden Screenshots verwenden Pixel 2 auf Android Q Version 9+, API Level 29). Die Antwort vor dem Abrufen sollte &quot;Antwort vor dem Abrufen erhalten&quot;lauten:

Wenn der Startbildschirm angezeigt wird, sollte die Anforderung zum vorherigen Abrufen geladen werden. Filtern Sie mit Logcat nach [!DNL "Target"] der Anforderung und Antwort:

![Validieren der Anforderungen auf dem Startbildschirm](assets/prefetch_validation.jpg)

Wenn keine erfolgreiche Antwort angezeigt wird, überprüfen Sie die Einstellungen in der `ADBMobileConfig.json` Datei und die Code-Syntax in der Datei HomeActivity.

Zwei Speicherorte werden jetzt an das Gerät zwischengespeichert. Die Ortsnamen werden in Kürze verzögert in die [!DNL Target] Benutzeroberfläche geladen, wo sie in verschiedenen Dropdown-Menüs ausgewählt werden können, wenn Sie sie in einer Aktivität verwenden.

### Hinzufügen Anforderungen für jeden zwischengespeicherten Speicherort laden

Nachdem die Speicherorte vorab abgerufen und die zugehörigen Antworten im Cache gespeichert wurden, fügen wir die `Target.loadRequest()` Methode hinzu, mit der der Inhalt des Angebots aus dem Cache abgerufen wird, damit Sie Ihre Anwendung aktualisieren können. Wir fügen eine neue benutzerspezifische Methode namens `engageMessage()` &quot;hinzu, die mit der Abfrage vor dem Abrufen ausgeführt wird. `engageMessage()` wird aufgerufen `Target.loadRequest()`. `engageMessage()` ausgeführt werden, `setUp()` um sicherzustellen, dass die Ladeanforderung aufgerufen wird, bevor der Bildschirm eingerichtet wird.

Fügen Sie zunächst den `engageMessage()` Aufruf &amp; die Methode für den Speicherort &quot;wetravel_engagement_home&quot;in der HomeActivity hinzu:

![Hinzufügen erste Ladeanforderung](assets/wetravel_engage_home_loadRequest.jpg)

Im Folgenden finden Sie den aktualisierten Code:

```java
    public void targetPrefetchContent() {
        List<TargetPrefetchObject> prefetchList = new ArrayList<>();
        Map<String, Object> params1;
        params1 = new HashMap<String, Object>();
        params1.put("at_property", "your at_property value goes here");
        prefetchList.add(Target.createTargetPrefetchObject(Constant.wetravel_engage_home, params1));
        prefetchList.add(Target.createTargetPrefetchObject(Constant.wetravel_engage_search, params1));
        Target.TargetCallback<Boolean> prefetchStatusCallback = new Target.TargetCallback<Boolean>() {
            @Override
            public void call(final Boolean status) {
                HomeActivity.this.runOnUiThread(new Runnable() {
                    @Override
                    public void run() {
                        String cachingStatus = status ? "YES" : "NO";
                        System.out.println("Received Response from prefetch : " + cachingStatus);
                        engageMessage();
                        setUp();
                    }
                });
            }};
        Target.prefetchContent(prefetchList, null, prefetchStatusCallback);
    }
    public void engageMessage() {
        Target.loadRequest(Constant.wetravel_engage_home, "", null, null, null,
            new Target.TargetCallback<String>(){
                @Override
                public void call(final String s) {
                    runOnUiThread(new Runnable() {
                        @Override
                        public void run() {
                            System.out.println("Engage Message : " + s);
                            if(s != null && !s.isEmpty()) Utility.showToast(getApplicationContext(), s);
                        }
                    });
                }
            });
    }
```

Fügen Sie nun den `engageMessage()` Aufruf &amp; die Methode für die Position &quot;wetravel_engagement_search&quot;in SearchBusActivity hinzu. Beachten Sie, dass der `engageMessage()` Aufruf in der `onResume()` -Methode festgelegt ist, bevor der Aufruf ausgeführt wird, `setUpSearch()` sodass er vor der Einrichtung des Bildschirms ausgeführt wird:

![Hinzufügen zweite Ladeanforderung](assets/wetravel_engage_search_loadRequest.jpg)

Im Folgenden finden Sie den aktualisierten Code:

```java
    @Override
    public void onResume() {
        super.onResume();
        engageMessage();
        setUpSearch();
    }
    public void engageMessage() {
        Target.loadRequest(Constant.wetravel_engage_search, "", null, null, null,
                new Target.TargetCallback<String>(){
                    @Override
                    public void call(final String s) {
                        runOnUiThread(new Runnable() {
                            @Override
                            public void run() {
                                System.out.println("Engage Message : " + s);
                                if(s != null && !s.isEmpty()) Utility.showToast(getApplicationContext(), s);
                            }
                        });
                    }
                });
    }
```

Da Sie soeben Target-Methoden zu SearchBusActivity hinzugefügt haben, müssen Sie die [!DNL Target] Klassen importieren:

```java
import com.adobe.mobile.Target;
import com.adobe.mobile.TargetPrefetchObject;
```

## Hinzufügen einer Echtzeitanforderung

Die nächste Anforderung, die wir der App hinzufügen werden, ist eine Echtzeitanforderung im Bildschirm &quot;Vielen Dank&quot;. Mit &quot;Echtzeit&quot; meinen wir, dass sowohl die Anforderung als auch die Antwort sofort angewendet wird (nicht für später zwischengespeichert). In einer späteren Lektion erstellen wir mit dieser Anforderung ein Erlebnis, das dem Reiseziel des Benutzers angepasst ist.

Fügen wir eine Echtzeitanforderung auf dem Dankesbildschirm hinzu. In der Datei &quot;Vielen DankYouActivity&quot;nehmen wir die in Rot angezeigten Änderungen vor:
![Hinzufügen einer Echtzeit-Position auf dem Bildschirm &quot;Vielen Dank&quot;](assets/thankyou.jpg)

Führen Sie einen Bildlauf zum Ende der Datei &quot;DanksagungYouActivity&quot;durch. Kommentieren Sie die drei Zeilen in der `getRecommandations()` Funktion aus und fügen Sie den Aufruf der `targetLoadRequest()` Funktion hinzu:

```java
// AppDialogs.dialogLoaderHide();
// recommandations.addAll(recommandation.recommandations);
// recommandationbAdapter.notifyDataSetChanged();
```

Hinzufügen diese Codezeile der `getRecommandations()` Funktion:

```java
targetLoadRequest(recommandation.recommandations);
```

Nun müssen wir die `targetLoadRequest()` Funktion definieren:
![Hinzufügen einer Echtzeit-Position auf dem Bildschirm &quot;Vielen Dank&quot;](assets/thankyou2.jpg)

Hinzufügen diesen Codeblock nach der `filterRecommendationBasedOnOffer()` Funktion:

```java
public void targetLoadRequest(final ArrayList<Recommandation> recommandations) {
    Target.loadRequest(Constant.wetravel_context_dest, "", null, null, null, new Target.TargetCallback<String>() {
        @Override
        public void call(final String response) {
            try {
                runOnUiThread(new Runnable() {
                    @Override
                    public void run() {
                        AppDialogs.dialogLoaderHide();
                        filterRecommendationBasedOnOffer(recommandations, response);
                        recommandationbAdapter.notifyDataSetChanged();
                    }
                });
            } catch (Exception e) {
                e.printStackTrace();
            }
        }
    });
}
```

Da Sie soeben Target-Methoden zu der DanksagungYouActivity hinzugefügt haben, sollten Sie die Target-Klassen importieren:

```java
import com.adobe.mobile.Target;
import com.adobe.mobile.TargetPrefetchObject;
```

### targetLoadRequest()-Codebeschreibung

| Code | Beschreibung |
|--- |--- |
| `targetLoadRequest()` | Eine benutzerdefinierte Funktion (die nicht Teil des SDK ist), `Target.loadRequest()` die den Speicherort &quot;wetravel_context_dest&quot;lädt und anzeigt |
| `Target.loadRequest()` | Die SDK-Methode, die die Anforderung an den Target-Server sendet |
| Constant.wetravel_context_dest | Der der Anforderung zugewiesene Ortsname, den wir später verwenden werden, wenn wir die Aktivität auf der [!DNL Target] Oberfläche erstellen |
| `filterRecommendationBasedOnOffer()` | Eine benutzerdefinierte Funktion in der App, die das Angebot des Standorts aus der Antwort des Targets abruft und entscheidet, wie die App basierend auf dem Inhalt des Angebots geändert werden soll |
| `recommandations.addAll()` | Eine benutzerdefinierte Funktion in der App, die standardmäßig ausgeführt wurde, wenn der Bildschirm &quot;Vielen Dank&quot;geladen wurde, jetzt jedoch ausgeführt wird, nachdem die Antwort des Targets empfangen und analysiert wurde von `filterRecommendationBasedOnOffer()` |

Dies war eine raffiniertere Aktualisierung, die wir dann mit der Anfrage an den Startbildschirm vorgenommen haben, also lasst uns einen Moment dauern, um zu überprüfen, was wir getan haben:

1. Das vorherige Verhalten der App, drei Standardaktionen anzuzeigen, wurde durch Auskommentieren der Codezeilen unterbrochen.
1. Stattdessen wurde der App empfohlen, eine neue Funktion auszuführen, die wir willkürlich targetLoadRequest nennen
1. Wir haben die `targetLoadRequest` Funktion definiert, um eine Anforderung an ein Target mithilfe der Target.loadRequest-Methode zu erstellen und die `filterRecommendationBasedOnOffer()` Funktion sofort auszuführen, wenn die [!DNL Target] Angebot-Antwort empfangen wird.
1. Die `filterRecommendationBasedOnOffer()` Funktion interpretiert die Antwort und entscheidet, welche Promotions auf den Bildschirm angewendet werden sollen

Dies ist ein sehr häufiges Nutzungsmuster bei der Verwendung [!DNL Target] in mobilen Apps.  Es ist sehr leistungsstark, da Sie fast jeden Aspekt Ihrer mobilen App personalisieren können. Es erfordert auch die Koordinierung zwischen dem App-Code und den Angeboten, die wir später in der [!DNL Target] Oberfläche definieren. Aufgrund dieser Koordination ist es bei einigen Personalisierungsfällen erforderlich, dass Sie Ihre App im App Store aktualisieren, um die Aktivität zu starten.

### Echtzeitanforderung überprüfen

Öffnen Sie den Android Emulator und führen Sie alle Schritte durch, um eine Reise zu buchen: Startseite > Ergebnisse der Bussuche > Auswahl der Sitze, Zahlungsoptionen (jede Zahlungsoption mit leeren Daten funktioniert).

Im letzten Dankesbildschirm sehen Sie Logcat für die Antwort. Die Antwort sollte lauten: &quot;Standardinhalt wurde für &quot;wetravel_context_dest&quot;zurückgegeben:

![Hinzufügen einer Echtzeit-Position auf dem Bildschirm &quot;Vielen Dank&quot;](assets/thankyou_validation.jpg)

## Bereinigen von zuvor abgerufenen Speicherorten aus dem Cache

Es kann Situationen geben, in denen zuvor abgerufene Orte während einer Sitzung gelöscht werden müssen. Wenn beispielsweise eine Buchung erfolgt, ist es sinnvoll, die zwischengespeicherten Orte zu löschen, da der Benutzer jetzt &quot;beschäftigt&quot;ist und den Buchungsprozess versteht. Wenn sie während ihrer Sitzung eine weitere Reise buchen, benötigen sie nicht die ursprünglichen Orte auf dem Startbildschirm und dem Suchergebnisbildschirm, um ihre Buchung zu leiten. Es wäre sinnvoller, die Speicherorte aus dem Cache zu löschen und neue Angebot für eine diskontierte zweite Buchung oder ein anderes relevantes Szenario vorzuziehen. Wenn während der Sitzung eine Buchung stattgefunden hat, könnte eine Logik zum Startbildschirm und zum Suchergebnisbildschirm hinzugefügt werden, um neue Orte im Voraus abzurufen.

In diesem Beispiel löschen wir die zuvor abgerufenen Orte für die Sitzung, wenn eine Buchung stattfindet. Dies erfolgt durch Aufruf der `Target.clearPrefetchCache()` Funktion. Legen Sie die Funktion innerhalb der `targetLoadRequest()` Funktion wie folgt fest:

```java
Target.clearPrefetchCache()
```

![Vorab abgerufene Speicherorte aus dem Cache löschen](assets/clearPrefetch.jpg)

Herzlichen Glückwunsch! Ihre App verfügt jetzt über das Framework zur Personalisierung. In der nächsten Lektion erweitern wir unsere Personalisierungsfunktionen, indem wir Parameter zu diesen Orten hinzufügen.

**[NÄCHSTES: &quot;Hinzufügen Parameter&quot;>](add-parameters.md)**
