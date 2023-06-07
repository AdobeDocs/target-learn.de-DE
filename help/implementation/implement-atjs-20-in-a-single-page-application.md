---
title: Implementieren von at.js 2.0 in Einzelseiten-Apps (SPA)
description: Adobe Target at.js 2.0 bietet umfassende Funktionen, mit denen Ihr Unternehmen mithilfe von Client-seitigen Technologien der neuesten Generation Personalisierungen ausführen kann. Führen Sie diese Schritte aus, um at.js 2.0 in einer Einzelseiten-App (SPA) zu implementieren.
role: Developer
level: Intermediate
topic: SPA, Architecture, Development
feature: Implementation
doc-type: technical video
kt: null
author: Daniel Wright
exl-id: 955f0571-5791-4dbb-9931-e6d5c8bb42a7
source-git-commit: 80208b3ecbc0d627d2afe72f882e91c9800d2726
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# Implementieren von Adobe Target at.js 2.0 in eine Einzelseiten-App (SPA)

Adobe Target `at.js` 2.0 bietet umfassende Funktionen, mit denen Ihr Unternehmen mithilfe von Client-seitigen Technologien der neuesten Generation Personalisierungen durchführen kann. Diese Version konzentriert sich auf die Aktualisierung `at.js` harmonische Interaktionen mit Einzelseitenanwendungen (SPA).

>[!VIDEO](https://video.tv.adobe.com/v/26248?quality=12)

## Implementieren von at.js 2.0 in einer SPA

* Implementierung `at.js` 2,0 im &lt;head> Ihrer Einzelseiten-App.
* Implementieren des `adobe.target.triggerView()` immer dann, wenn sich die Ansicht in Ihrer SPA ändert. Dazu können verschiedene Techniken eingesetzt werden, z. B. das Überwachen von URL-Hash-Änderungen, das Überwachen von benutzerdefinierten Ereignissen, die von Ihrer SPA ausgelöst werden, oder das Einbetten der `triggerView()` Code direkt in Ihre Anwendung einfügen. Sie sollten die Option auswählen, die am besten für Ihre spezifische Einzelseitenanwendung geeignet ist.
* Der Name der Ansicht ist der erste Parameter der `triggerView()` -Funktion. Verwenden Sie einfache, klare und eindeutige Namen, damit sie im Visual Experience Composer von Target leicht ausgewählt werden können.
* Sie können Trigger-Ansichten in kleinen Ansichtsänderungen sowie in nicht SPA Kontexten wie der halben Navigation nach unten auf einer unendlichen Scrollseite anzeigen.
* `at.js` 2.0 und `triggerView()` kann über eine Tag-Management-Lösung wie Adobe Experience Platform Launch implementiert werden.

## Einschränkungen von at.js 2.0

Beachten Sie die folgenden Einschränkungen von `at.js` 2.0 vor der Aktualisierung:

* Das domänenübergreifende Tracking wird in `at.js` 2,0
* Die URL-Parameter mboxOverride.browserIp und mboxSession werden in `at.js` 2,0
* Die alten Funktionen mboxCreate, mboxDefine, mboxUpdate werden in `at.js` 2.0. Standardinhalt wird angezeigt und es werden keine Netzwerkanfragen gestellt.

## Im Video verwendeter Bibliotheksfußzeilencode

Der unten stehende Code wurde dem Abschnitt &quot;Bibliotheksfußzeile&quot;des `at.js` -Bibliothek während des Videos. Sie wird ausgelöst, wenn die App zuerst geladen wird und dann bei jeder Hash-Änderung in der App. Es verwendet eine bereinigte Version des Hash als Ansichtsnamen und &quot;home&quot;, wenn der Hash leer ist. Beachten Sie, dass der Code zur Identifizierung des SPA nach dem Text &quot;react/&quot;in der URL sucht, der höchstwahrscheinlich auf Ihrer Site aktualisiert werden muss. Denken Sie auch daran, dass es für Ihre SPA geeigneter sein könnte, zu feuern `triggerView()` von benutzerspezifischen Ereignissen entfernt oder indem Sie den Code direkt in Ihre App einbetten.

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
* [Verwenden von Adobe Target Visual Experience Composer für Einzelseiten-Apps (SPA VEC)](../experiences/use-the-visual-experience-composer-for-single-page-applications.md)
