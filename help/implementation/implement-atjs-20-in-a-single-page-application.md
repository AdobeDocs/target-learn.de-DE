---
title: '"at.js 2.0"des Adobe Targets in eine Einzelseitenanwendung (SPA) implementieren'
seo-title: '"at.js 2.0"des Adobe Targets in eine Einzelseitenanwendung (SPA) implementieren'
description: Die neueste Version von at.js bietet umfassende Funktionen, mit denen Ihr Unternehmen mithilfe von Client-seitigen Technologien der neuesten Generation Personalisierungen ausführen kann. Diese neue Version konzentriert sich auf die Aktualisierung von at.js, um harmonische Interaktionen mit Einzelseiten-Apps (SPAs) zu ermöglichen.
audience: developer
difficulty: 3
author: Daniel Wright
doc-type: implement
activity-type: technical-video
translation-type: tm+mt
source-git-commit: 37443ae4c1cdda387c8db0053201d520fa1ec224
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 8%

---


# &quot;at.js 2.0&quot;des Adobe Targets in eine Einzelseitenanwendung (SPA) implementieren

The newest version of `at.js` provides rich feature sets that equip your business to execute personalization on next-generation, client-side technologies. This new version is focused on upgrading `at.js` to have harmonious interactions with single page applications (SPAs).

>[!VIDEO](https://video.tv.adobe.com/v/26248?quality=12)

## &quot;at.js 2.0&quot;in einer SPA implementieren

* Implementieren Sie `at.js` 2.0 im &lt;head> der Einzelseitenanwendung.
* Implementieren Sie die `adobe.target.triggerView()` Funktion, wenn sich die Ansicht in Ihrer SPA ändert. Dazu können verschiedene Methoden eingesetzt werden, z. B. das Listening auf Änderungen am URL-Hash, das Listening auf benutzerdefinierte Ereignis, die von Ihrer SPA ausgelöst werden, oder das Einbetten des `triggerView()` Codes direkt in Ihre Anwendung. Sie sollten die Option wählen, die für Ihre spezifische Einzelseitenanwendung am besten geeignet ist.
* Der Ansicht-Name ist der erste Parameter der `triggerView()` Funktion. Verwenden Sie einfache, klare und eindeutige Namen, um sie im Visual Experience Composer der Zielgruppe auszuwählen.
* Sie können Ansichten in kleinen Ansichten sowie in Nicht-SPA-Kontexten auslösen, z. B. in der Mitte einer unendlichen Bildlaufseite.
* `at.js` 2.0 und `triggerView()` kann über eine Tag-Management-Lösung wie Adobe Experience Platform Launch implementiert werden.

## at.js 2.0-Einschränkungen

Beachten Sie vor dem Upgrade die folgenden Einschränkungen von `at.js` 2.0:

* In `at.js` 2.0 wird die domänenübergreifende Verfolgung nicht unterstützt
* Die URL-Parameter mboxOverride.browserIp und mboxSession werden in `at.js` 2.0 nicht unterstützt
* Die alten Funktionen mboxCreate, mboxDefine und mboxUpdate werden in `at.js` 2.0 nicht mehr unterstützt. Standardinhalt wird angezeigt und es werden keine Netzwerkanforderungen gesendet.

## Im Video verwendeter Bibliotheksfußzeilencode

Der unten stehende Code wurde während des Videos zum Abschnitt &quot;Bibliotheksfußzeile&quot;der `at.js` Bibliothek hinzugefügt. Es wird ausgelöst, wenn die App zuerst geladen wird und dann bei jeder Hash-Änderung in der App. Es verwendet eine bereinigte Version des Hashs als Ansicht und &quot;Home&quot;, wenn der Hash leer ist. Beachten Sie, dass zur Identifizierung der SPA der Code nach dem Text &quot;response/&quot;in der URL sucht, der höchstwahrscheinlich auf Ihrer Site aktualisiert werden muss. Denken Sie auch daran, dass es für Ihre SPA angemessener sein könnte, benutzerdefinierte Ereignis `triggerView()` zu löschen oder den Code direkt in Ihre App einzubetten.

```javascript
function sanitizeViewName(viewName) {
  if (viewName.startsWith('#')) {
    viewName = viewName.substr(1);
  }
  if (viewName.startsWith('/')) {
    viewName = viewName.substr(1);
  }
  return viewName;
}
function triggerView(viewName) {
  viewName = sanitizeViewName(viewName) || 'home';
  // Validate if the Target Libraries are available on your website
  if (typeof adobe != 'undefined' && adobe.target && typeof adobe.target.triggerView === 'function') {
    adobe.target.triggerView(viewName);
    console.log('AT: View triggered on page load: '+viewName)
  }
}
//fire triggerView when the SPA loads and when the hash changes in the SPA
if(window.location.pathname.indexOf('react/') >-1){
    triggerView(location.hash);
}
window.onhashchange = function() {
    if(window.location.pathname.indexOf('react/') >-1){
        triggerView(location.hash);
    }
}
```

## Zusätzliche Ressourcen

* [Funktionsweise von at.js 2.0 (Architekturdiagramme)](understanding-how-atjs-20-works.md)
* [Visual Experience Composer von Adobe Target für Einzelseitenanwendungen (SPA VEC)](../experiences/use-the-visual-experience-composer-for-single-page-applications.md)
* [Aktualisierung der Dokumentation von &quot;at.js 1.x&quot;auf &quot;at.js 2.0&quot;](https://docs.adobe.com/content/help/en/target/using/implement-target/client-side/upgrading-from-atjs-1x-to-atjs-20.html)