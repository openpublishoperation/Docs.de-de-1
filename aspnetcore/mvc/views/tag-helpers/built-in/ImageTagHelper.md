---
title: Bild-Tag-Hilfsprogramm | Microsoft Docs
author: pkellner
description: Veranschaulicht das Arbeiten mit Images Tag Helper
keywords: ASP.NET Core, Tag-Hilfsprogramm
ms.author: riande
manager: wpickett
ms.date: 02/14/2017
ms.topic: article
ms.assetid: c045d485-d1dc-4cea-a675-46be83b7a013
ms.technology: aspnet
ms.prod: aspnet-core
uid: mvc/views/tag-helpers/builtin-th/ImageTagHelper
ms.openlocfilehash: 67537674154d885fc6f69accd2cc7f01c9104d71
ms.sourcegitcommit: 0b6c8e6d81d2b3c161cd375036eecbace46a9707
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/11/2017
---
# <a name="imagetaghelper"></a>ImageTagHelper

Durch [Peter Kellner](http://peterkellner.net) 

Das Image-Tag-Hilfsobjekt verbessert die `img` (`<img>`) Tag. Erfordert eine `src` Tag als auch die `boolean` Attribut `asp-append-version`.

Wenn die Bildquelle (`src`) ist eine statische Datei auf dem Host-Webserver, ein eindeutiger Cache Abwehrprogramm Zeichenfolge als Abfrageparameter an die Bildquelle angefügt ist. Dadurch wird sichergestellt, dass wenn die Datei auf dem Webserver des Hosts geändert wird, eine eindeutige Anforderungs-URL generiert wird, die die aktualisierte Anforderungsparameter enthält. Der Cache Abwehrprogramm Zeichenfolge ist ein eindeutiger Wert, der den Hash der Datei statisches Bild darstellt.

Wenn die Bildquelle (`src`) ist, eine statische Datei (z. B. eine remote-URL oder die Datei existiert nicht auf dem Server), die `<img>` des Tags `src` Attribut ohne Cache Abwehrprogramm Abfragezeichenfolgen-Parameters generiert wird.

## <a name="image-tag-helper-attributes"></a>Bildattributen Tag-Hilfsprogramm


### <a name="asp-append-version"></a>ASP-Anhängen-version

Wenn zusammen mit angegebenen ein `src` -Attribut, das Image-Tag-Hilfsprogramm wird aufgerufen.

Ein Beispiel einer gültigen `img` Tag Helper ist:

```cshtml
<img src="~/images/asplogo.png" 
    asp-append-version="true"  />
```

Eine statische Datei im Verzeichnis vorhanden *... wwwroot/Images/asplogo.PNG* die generierte HTML-Code ist ähnlich der folgenden (der Hash wird abweichen):

```html
<img 
    src="/images/asplogo.png?v=Kl_dqr9NVtnMdsM2MUg4qthUnWZm5T1fCEimBPWDNgM"/>
```

Der Wert, der dem Parameter zugewiesen `v` wird der Hashwert der Datei auf dem Datenträger. Ist der Webserver konnte nicht abgerufen werden Lesezugriff auf die statische Datei auf die verwiesen wird, keine `v` Parameter hinzugefügt wird die `src` Attribut.

- - -

### <a name="src"></a>src

Um das Image-Tag-Hilfsprogramm zu aktivieren, muss das Src-Attribut auf die `<img>` Element. 

> [!NOTE]
> Das Image-Tag-Hilfsprogramm verwendet die `Cache` Anbieter auf dem lokalen Webserver zum Speichern der berechneten `Sha512` einer angegebenen Datei. Wenn die Datei erneut angefordert wird die `Sha512` muss nicht neu berechnet werden. Der Cache wird durch einen Dateimonitor für die, die an die Datei angehängt ist ungültig Wenn der Datei `Sha512` berechnet wird.

## <a name="additional-resources"></a>Zusätzliche Ressourcen

* <xref:performance/caching/memory>