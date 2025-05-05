---
title: Implementieren von at.js 2.0 in einer Single Page Application (SPA)
description: at.js 2.0 von Adobe Target bietet umfangreiche Funktionssätze, mit denen Ihr Unternehmen Personalisierungen auf Client-seitigen Technologien der nächsten Generation durchführen kann. Führen Sie diese Schritte aus, um at.js 2.0 in einer Single Page Application (SPA) zu implementieren.
role: Developer
level: Intermediate
topic: SPA, Architecture, Development
feature: Implementation
doc-type: technical video
kt: null
author: Daniel Wright
exl-id: 955f0571-5791-4dbb-9931-e6d5c8bb42a7
source-git-commit: fcd2273ba373dc2b3bc59a77f1925cdb7b2ed3ee
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# Implementieren von at.js 2.0 in einer Single Page Application (SPA) von Adobe Target

Adobe Target `at.js` 2.0 bietet umfangreiche Funktionssätze, mit denen Ihr Unternehmen Personalisierungen auf Client-seitigen Technologien der nächsten Generation durchführen kann. Diese Version konzentriert sich auf das Upgrade von `at.js`, um harmonische Interaktionen mit Single Page Applications (SPAs) zu ermöglichen.

>[!VIDEO](https://video.tv.adobe.com/v/34771?quality=12&captions=ger)

## Implementieren von at.js 2.0 in einer SPA

* Implementieren Sie `at.js` 2.0 im &lt;head> Ihrer Einzelseitenanwendung.
* Implementieren Sie die `adobe.target.triggerView()` Funktion immer dann, wenn sich die Ansicht in Ihrer SPA ändert. Dazu können verschiedene Techniken verwendet werden, z. B. das Überwachen von URL-Hash-Änderungen, das Überwachen benutzerdefinierter Ereignisse, die von Ihrer SPA ausgelöst werden, oder das Einbetten des `triggerView()`-Codes direkt in Ihre Anwendung. Wählen Sie die Option aus, die für Ihr spezifisches Einzelseiten-Programm am besten geeignet ist.
* Der Ansichtsname ist der erste Parameter der `triggerView()`. Verwenden Sie einfache, klare und eindeutige Namen, damit sie im Visual Experience Composer von Target einfach ausgewählt werden können.
* Sie können Trigger-Ansichten sowohl in kleinen Ansichtsänderungen als auch in Nicht-SPA-Kontexten wie der halben Seite nach unten oder dem unendlichen Scrollen verwenden.
* `at.js` 2.0 und `triggerView()` können über eine Tag-Management-Lösung wie Adobe Experience Platform Launch implementiert werden.

## Einschränkungen von at.js 2.0

Beachten Sie die folgenden Einschränkungen von `at.js` 2.0, bevor Sie ein Upgrade durchführen:

* Domain-übergreifendes Tracking wird in `at.js` 2.0 nicht unterstützt
* Die URL-Parameter mboxOverride.browserIp und mboxSession werden in `at.js` 2.0 nicht unterstützt
* Die Legacy-Funktionen mboxCreate, mboxDefine, mboxUpdate werden in `at.js` 2.0 nicht mehr unterstützt. Standardinhalt wird angezeigt und es werden keine Netzwerkanfragen gestellt.

## Im Video verwendeter Bibliotheks-Fußzeilen-Code

Der unten stehende Code wurde während des Videos zum Abschnitt „Fußzeile der Bibliothek“ der `at.js` hinzugefügt. Er wird ausgelöst, wenn die App zum ersten Mal geladen wird, und dann bei allen Hash-Änderungen in der App. Sie verwendet eine bereinigte Version des Hash als Ansichtsnamen und „Home“, wenn der Hash leer ist. Beachten Sie, dass der Code zur Identifizierung der SPA in der URL nach dem Text „react/&quot; sucht, der höchstwahrscheinlich auf Ihrer Site aktualisiert werden muss. Beachten Sie außerdem, dass es für Ihre SPA angemessener sein kann, `triggerView()` von benutzerdefinierten Ereignissen auszulösen oder den Code direkt in Ihre App einzubetten.

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
* [Verwenden des Visual Experience Composer von Adobe Target für Einzelseitenanwendungen (SPA VEC)](../experiences/use-the-visual-experience-composer-for-single-page-applications.md)
