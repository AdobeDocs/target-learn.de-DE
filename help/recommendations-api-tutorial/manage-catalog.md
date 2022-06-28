---
title: Verwalten Ihres Recommendations-Katalogs mithilfe von APIs
description: Dieser Teil des Tutorials führt Entwickler durch die Schritte, die zur Verwendung von Adobe Target-APIs zum Erstellen, Aktualisieren, Speichern, Abrufen und Löschen von Entitäten in Ihrem Recommendations-Katalog erforderlich sind.
role: Developer
level: Intermediate
topic: Personalization, Administration, Integrations, Development
feature: APIs/SDKs, Recommendations, Administration & Configuration
doc-type: tutorial
kt: 3815
author: Judy Kim
exl-id: 8060b69b-e8e5-4fe7-895f-742410d8ed45
source-git-commit: 0ecfde208b3e201de135512d5aab70192fc2b826
workflow-type: tm+mt
source-wordcount: '918'
ht-degree: 2%

---

# Verwalten Ihrer [!DNL Recommendations] Katalog mit APIs

An dieser Stelle haben Sie gelernt, wie Sie mithilfe des JWT-Authentifizierungsflusses ein Zugriffstoken generieren, um die Adobe Target Admin-APIs mit Adobe I/O zu verwenden.

Sie können die [Recommendations-APIs](https://developers.adobetarget.com/api/recommendations/) , um Artikel in Ihrem Empfehlungskatalog hinzuzufügen, zu aktualisieren oder zu löschen. Wie bei den anderen Adobe Target-Admin-APIs muss die [!DNL Recommendations] APIs erfordern Authentifizierung.

>[!TIP]
>
>Senden Sie die **[!UICONTROL IMS: JWT-Generierung + Auth über Benutzer-Token]** immer dann anfordern, wenn Sie Ihr Zugriffstoken zur Authentifizierung aktualisieren müssen, da es nach 24 Stunden abläuft. Siehe [Adobe API-Authentifizierung konfigurieren](https://developer.adobe.com/target/before-administer/configure-authentication/){target=_blank} für Anweisungen.

![JWT3ff](assets/configure-io-target-jwt3ff.png)

>[!NOTE]
>
>Bevor Sie fortfahren, rufen Sie die [Recommendations Postman-Sammlung](https://developers.adobetarget.com/api/recommendations/#section/Postman).

## Erstellen und Aktualisieren von Elementen mit der API &quot;Entitäten speichern&quot;

So füllen Sie Ihre [!DNL Recommendations] Produktdatenbank, die die API anstelle eines CSV-Produkt-Feeds verwendet, oder [!DNL Target] -Anfragen, die auf Produktseiten ausgelöst werden, verwenden Sie die [Entitäten-API speichern](https://developers.adobetarget.com/api/recommendations/#operation/saveEntities). Diese Anfrage fügt ein Element in einem [!DNL Target] Umgebung. Die Syntax lautet:

```
POST https://mc.adobe.io/{{TENANT_ID}}/target/recs/entities
```

So können beispielsweise &quot;Save Entities&quot;verwendet werden, um Artikel zu aktualisieren, wenn bestimmte Schwellenwerte erreicht werden (z. B. Werte für Inventar oder Preis), um diese Elemente zu kennzeichnen und zu verhindern, dass sie empfohlen werden.

1. Navigieren Sie zu **[!DNL Target]> [!UICONTROL Einrichtung] > [!UICONTROL Hosts] > [!UICONTROL Umgebungen]** um [!DNL Target] Umgebungs-ID, in der Sie ein Element hinzufügen oder aktualisieren möchten.

   ![SaveEntities1](assets/SaveEntities01.png)

2. Überprüfen `TENANT_ID` und `API_KEY` referenzieren Sie die zuvor erstellten Postman-Umgebungsvariablen. Verwenden Sie das folgende Bild zum Vergleich. Ändern Sie bei Bedarf die Kopfzeilen und den Pfad in Ihrer API-Anfrage so, dass sie mit denen in der Abbildung unten übereinstimmen.

   ![SaveEntities3](assets/SaveEntities03.png)

3. Geben Sie Ihre JSON als **raw** im **body**. Vergessen Sie nicht, Ihre Umgebungs-ID mithilfe der `environment` -Variable. (Im folgenden Beispiel ist die Umgebungs-ID 6781.)

   ![SaveEntities4.png](assets/SaveEntities04.png)

   >!![NOTE]
   Nachfolgend finden Sie ein Beispiel-JSON, das entity.id kit2001 mit den zugehörigen Entitätswerten für ein Toaster Oven-Produkt in die Umgebung 6781 hinzufügt.

   ```
      {
      "entities": [{
              "name": "Toaster Oven",
              "id": "kit2001",
              "environment": 6781,
              "categories": [
                  "housewares:appliances"
              ],
              "attributes": {
                  "inventory": 77,
                  "margin": 23,
                  "message": "crashing helicopter",
                  "pageUrl": "www.foobar.foo.com/helicopter.html",
                  "thumbnailUrl": "www.foobar.foo.com/helicopter.jpg",
                  "value": 19.2
              }
          }]
      }
   ```

4. Klicken Sie auf **Senden**. Sie sollten die folgende Antwort erhalten.

   ![SaveEntities5.png](assets/SaveEntities05.png)

Das JSON-Objekt kann skaliert werden, um mehrere Produkte zu senden. Diese JSON gibt beispielsweise zwei Entitäten an.

```
    {
        "entities": [{
                "name": "Toaster Oven",
                "id": "kit2001",
                "environment": 6781,
                "categories": [
                    "housewares:appliances"
                ],
                "attributes": {
                    "inventory": 89,
                    "margin": 11,
                    "message": "Toaster Oven",
                    "pageUrl": "www.foobar.foo.com/helicopter.html",
                    "thumbnailUrl": "www.foobar.foo.com/helicopter.jpg",
                    "value": 102.5
                }
            },
            {
                "name": "Blender",
                "id": "kit2002",
                "environment": 6781,
                "categories": [
                    "housewares:appliances"
                ],
                "attributes": {
                    "inventory": 36,
                    "margin": 5,
                    "message": "Blender",
                    "pageUrl": "www.foobar.foo.com/helicopter.html",
                    "thumbnailUrl": "www.foobar.foo.com/helicopter.jpg",
                    "value": 54.5
                }
            }
        ]
    }
```

1. Jetzt bist du dran! Verwenden Sie die **Entitäten speichern** API zum Hinzufügen der folgenden Elemente zu Ihrem Katalog. Verwenden Sie die obige JSON-Beispieldatei als Ausgangspunkt. (Sie müssen die JSON-Datei um weitere Entitäten erweitern.)

   ![SaveEntities6.png](assets/SaveEntities06.png)

Ups, sieht so aus, als ob die letzten beiden Dinge nicht gehören. Untersuchen wir sie mithilfe des **Entität abrufen** APIs erstellen und diese bei Bedarf mithilfe der **Entitäten löschen** API.

## Abrufen von Elementdetails mit der Get Entity API

Um die Details eines vorhandenen Elements abzurufen, verwenden Sie die [Entitäts-API abrufen](https://developers.adobetarget.com/api/recommendations/#operation/getEntity). Die Syntax lautet:

```
GET https://mc.adobe.io/{{TENANT_ID}}/target/recs/entities/[entity.id]
```

Entitätsdetails können jeweils nur für eine Entität abgerufen werden. Sie können &quot;Entität abrufen&quot;verwenden, um zu bestätigen, dass im Katalog Aktualisierungen wie erwartet vorgenommen wurden, oder um anderweitig den Inhalt des Katalogs zu überprüfen.

1. Geben Sie in der API-Anfrage mithilfe der -Variablen die Entitäts-ID an `entityId`. Im folgenden Beispiel werden Details für die Entität zurückgegeben, deren entityId=kit2004 lautet.

   ![GetEntity1](assets/GetEntity1.png)

2. Überprüfen `TENANT_ID` und `API_KEY` referenzieren Sie die zuvor erstellten Postman-Umgebungsvariablen. Verwenden Sie das folgende Bild zum Vergleich. Ändern Sie bei Bedarf die Kopfzeilen und den Pfad in Ihrer API-Anfrage so, dass sie mit denen in der Abbildung unten übereinstimmen.

   ![GetEntity2](assets/GetEntity2.png)

3. Senden Sie die Anfrage.

   ![GetEntity3](assets/GetEntity3.png)
Wenn Sie eine Fehlermeldung erhalten, dass die Entität nicht gefunden wurde, wie im Beispiel oben gezeigt, überprüfen Sie, ob Sie die Anfrage an die richtige senden [!DNL Target] Umgebung.

   >[!NOTE]
   Wenn keine Umgebung explizit angegeben ist, versucht &quot;Get Entity&quot;, die Entität von Ihrer [Standardumgebung](https://experienceleague.adobe.com/docs/target/using/administer/hosts.html?lang=en) nur. Wenn Sie von einer anderen Umgebung als der Standardumgebung abrufen möchten, müssen Sie die Umgebungs-ID angeben.

4. Fügen Sie bei Bedarf die `environmentId` und senden Sie die Anfrage erneut.

   ![GetEntity4](assets/GetEntity4.png)

5. Senden einer weiteren **Entität abrufen** dieses Mal die Entität überprüfen, deren entityId=kit2005.

   ![GetEntity5](assets/GetEntity5.png)

Angenommen, Sie entscheiden, dass diese Entitäten aus Ihrem Katalog entfernt werden müssen. Verwenden wir die **Entitäten löschen** API.

## Löschen von Elementen mit der API &quot;Entitäten löschen&quot;

Um Elemente aus Ihrem Katalog zu entfernen, verwenden Sie die [Entitäten-API löschen](https://developers.adobetarget.com/api/recommendations/#operation/deleteEntities). Die Syntax lautet:

```
DELETE https://mc.adobe.io/{{TENANT_ID}}/target/recs/entities?ids=[comma-delimited-entity-ids]&environment=[environmentId]
```

>[!WARNING]
Diese API löscht Entitäten, die von Ihnen angegebenen IDs referenziert werden.
Wenn keine Entitäts-IDs bereitgestellt werden, werden alle Entitäten in der angegebenen Umgebung gelöscht. Wenn keine Umgebungs-ID angegeben wird, werden Entitäten aus allen Umgebungen gelöscht. Seien Sie vorsichtig!

1. Navigieren Sie zu **[!DNL Target]> [!UICONTROL Einrichtung] > [!UICONTROL Hosts] > [!UICONTROL Umgebungen]** um [!DNL Target] Umgebungs-ID, aus der Sie Elemente löschen möchten.

   ![DeleteEntities1](assets/SaveEntities01.png)

2. Geben Sie in der API-Anfrage mithilfe der Syntax die Entitäts-IDs der Entitäten an, die Sie löschen möchten `&ids=[comma-delimited-entity-ids]` (Abfrageparameter). Trennen Sie beim Löschen mehrerer Entitäten die IDs durch Kommas.

   ![DeleteEntities2](assets/DeleteEntities2.png)

3. Geben Sie die Umgebungs-ID mithilfe der Syntax an. `&environment=[environmentId]`, andernfalls werden Entitäten in allen Umgebungen gelöscht.

   ![DeleteEntities3](assets/DeleteEntities3.png)

4. Überprüfen `TENANT_ID` und `API_KEY` referenzieren Sie die zuvor erstellten Postman-Umgebungsvariablen. Verwenden Sie das folgende Bild zum Vergleich. Ändern Sie bei Bedarf die Kopfzeilen und den Pfad in Ihrer API-Anfrage so, dass sie mit denen in der Abbildung unten übereinstimmen.

   ![DeleteEntities4](assets/DeleteEntities4.png)

5. Senden Sie die Anfrage.

   ![DeleteEntities5](assets/DeleteEntities5.png)

6. Überprüfen Sie die Ergebnisse mit **Entität abrufen**, der nun angibt, dass die gelöschten Entitäten nicht gefunden werden können.

   ![DeleteEntities6](assets/DeleteEntities6.png)

   ![DeleteEntities6](assets/DeleteEntities7.png)

Herzlichen Glückwunsch! Sie können jetzt die [!DNL Recommendations] APIs zum Erstellen, Aktualisieren, Löschen und Abrufen von Details zu den Entitäten in Ihrem Katalog. Im nächsten Abschnitt erfahren Sie, wie Sie benutzerdefinierte Kriterien verwalten.

[Weiter mit &quot;Benutzerdefinierte Kriterien verwalten&quot;>](https://developer.adobe.com/target/before-administer/recs-api/manage-custom-criteria/){target=_blank}
