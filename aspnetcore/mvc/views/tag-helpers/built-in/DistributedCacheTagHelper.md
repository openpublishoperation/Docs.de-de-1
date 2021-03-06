---
title: Verteilte Cache Tag Helper | Microsoft Docs
author: pkellner
description: Zeigt die zum Arbeiten mit Cache-Tag-Hilfsprogramm
keywords: ASP.NET Core, Tag-Hilfsprogramm
ms.author: riande
manager: wpickett
ms.date: 02/14/2017
ms.topic: article
ms.assetid: c045d485-d1dc-4cea-a675-46be83b7a022
ms.technology: aspnet
ms.prod: aspnet-core
uid: mvc/views/tag-helpers/builtin-th/DistributedCacheTagHelper
ms.openlocfilehash: 2b260624fb2d85ab1a2625511397bcb4a85b6e77
ms.sourcegitcommit: d022d4b96795ee473fa3847a1d8a8c7430423a86
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/13/2017
---
# <a name="distributed-cache-tag-helper"></a>Verteilter Cache-Tag-Hilfsprogramm

Durch [Peter Kellner](http://peterkellner.net) 


Das verteilte Cache-Tag-Hilfsprogramm bietet die Möglichkeit, die Leistung Ihrer App ASP.NET Core erheblich zu verbessern, indem Sie dessen Inhalt an eine Quelle verteilter Cache caching.

Das verteilte Cache-Tag-Hilfsobjekt erbt von der gleichen Basisklasse als die Cache-Tag-Hilfsprogramm.  Alle Attribute, die dem Cache Tag Hilfsprogramm zugeordnete funktioniert auch auf das Tag-Hilfsobjekt verteilt.


Das verteilte Cache-Tag-Hilfsobjekt folgt die **expliziten Abhängigkeiten Prinzip** genannt **Konstruktoreinfügung**.  Insbesondere die `IDistributedCache` Schnittstelle Container an den verteilten Cache Tag Helfer-Konstruktor übergeben wird.  Wenn keine bestimmte konkrete Implementierung der `IDistributedCache` erstellt wurde, `ConfigureServices`, in der Regel in startup.cs gefunden und dann das verteilte Cache-Tag-Hilfsobjekt wird die gleiche in-Memory-Anbieter zum Speichern von zwischengespeicherten Daten als die grundlegende Cache-Tag-Hilfsprogramm verwenden.

## <a name="distributed-cache-tag-helper-attributes"></a>Verteilte Cache Tagattribute-Hilfsprogramm

- - -

### <a name="enabled-expires-on-expires-after-expires-sliding-vary-by-header-vary-by-query-vary-by-route-vary-by-cookie-vary-by-user-vary-by-priority"></a>läuft ab am läuft ab nach Ablauf-gleitende aktiviert variieren-by-Header durch eine Abfrage variieren variieren von Route variieren von Cookie variieren von Benutzer variieren-nach Priorität

Definitionen finden Sie in der Cache-Tag-Hilfsprogramm. Verteilte Cache Tag Helper erbt von derselben Klasse wie Cache-Tag-Hilfsprogramm, damit alle diese Attribute aus dem Cache Tag Helper gemeinsam verwendet werden.

- - -

### <a name="name-required"></a>Name (erforderlich)

| Attributtyp    | Beispielwert     |
|----------------   |----------------   |
| string    | "my-distributed-cache-unique-key-101"     |

Die erforderliche `name` Attribut als Schlüssel für diesen Cache gespeichert, die für jede Instanz eines verteilten Cache-Tag-Hilfsprogramms verwendet wird.  Im Gegensatz zu den grundlegenden Cache Tag-Hilfsprogramm, das einen Schlüssel jeder Cache Tag-Hilfsinstanz basierend auf den Namen der Razor-Seite und den Speicherort der Hilfsprogramm-Tag in der Seite "Razor" zuweist, beruht die verteilten Cache Tag Helper nur sie dessen Schlüssel für das Attribut`name`

Verwendungsbeispiel:

```cshtml
<distributed-cache name="my-distributed-cache-unique-key-101">
    Time Inside Cache Tag Helper: @DateTime.Now
</distributed-cache>
```

## <a name="distributed-cache-tag-helper-idistributedcache-implementations"></a>Verteilte Cache Tag Helper IDistributedCache Implementierungen

Es gibt zwei Implementierungen von `IDistributedCache` in ASP.NET Core integriert.  Eine basiert auf **Sql Server** und die andere basiert auf **Redis**. Details zu dieser Implementierung finden Sie unter der Ressource, die nachstehenden benannte "Arbeiten mit einem verteilten Cache". Beide Implementierungen umfassen Festlegen einer Instanz des `IDistributedCache` in ASP.NET Core des **startup.cs**.

Stehen keine Tagattribute explizit verknüpft sind mit einer bestimmten Implementierung des `IDistributedCache`.



- - -



## <a name="additional-resources"></a>Zusätzliche Ressourcen

* <xref:mvc/views/tag-helpers/builtin-th/CacheTagHelper>
* <xref:fundamentals/dependency-injection#service-lifetimes-and-registration-options>
* <xref:performance/caching/distributed>
* <xref:performance/caching/memory>
* <xref:security/authentication/identity>
