---
title: "Reduzieren von Paketabhängigkeiten mit „project.json“"
description: "Reduzieren Sie beim Erstellen von Bibliotheken, die auf project.json basieren, die Paketabhängigkeiten."
keywords: .NET, .NET Core
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 916251e3-87f9-4eee-81ec-94076215e6fa
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 23d83f0402e35bc4bed31ef59a6fff0e28e01d35
ms.contentlocale: de-de
ms.lasthandoff: 07/28/2017

---

# <a name="reducing-package-dependencies-with-projectjson"></a>Reduzieren von Paketabhängigkeiten mit „project.json“

Dieser Artikel beschreibt, was Sie über das Reduzieren Ihrer Paketabhängigkeiten beim Erstellen von `project.json`-Bibliotheken wissen müssen. Am Ende dieses Artikels erfahren Sie, wie Ihre Bibliothek so zusammengesetzt wird, dass sie nur die Abhängigkeiten verwendet, die sie benötigt. 

## <a name="why-its-important"></a>Warum dies wichtig ist

.NET Core ist ein Produkt, das aus NuGet-Paketen besteht.  Ein wichtiges Paket ist das [.NETStandard.Library metapackage (.NETStandard.Library-Metapaket)](https://www.nuget.org/packages/NETStandard.Library), wobei es sich um ein NuGet-Paket handelt, das aus anderen Paketen besteht.  Es stellt die Reihe von Paketen bereit, bei denen gewährleistet wird, dass sie auf mehreren .NET-Implementierungen wie z.B. .NET Framework, .NET Core und Xamarin/Mono funktionieren.

Jedoch ist die Wahrscheinlichkeit hoch, dass Ihre Bibliothek nicht jedes einzelne Paket verwenden wird, das enthalten ist.  Beim Erstellen einer Bibliothek und Verteilen dieser Bibliothek über NuGet ist eine empfohlene Vorgehensweise das „Beschränken“ Ihrer Abhängigkeiten auf nur die Pakete, die Sie tatsächlich verwenden.  Dies führt zu einem kleineren allgemeinen Speicherbedarf für NuGet-Pakete.

## <a name="how-to-do-it"></a>So gehen Sie vor

Derzeit gibt es keinen offiziellen `dotnet`-Befehl, der Paketverweise beschränkt.  Stattdessen müssen Sie dies manuell tun.  Der allgemeine Prozess sieht folgendermaßen aus:

1. Verweisen Sie auf `NETStandard.Library` Version `1.6.0` in einem `dependencies`-Abschnitt Ihrer `project.json`.
2. Stellen Sie Pakete mit `dotnet restore` aus der Befehlszeile wieder her.
3. Prüfen Sie die Datei `project.lock.json`, und suchen Sie den Abschnitt `NETSTandard.Library`.  Er befindet sich nahe dem Anfang der Datei.
4. Kopieren Sie alle unter `dependencies` aufgeführten Pakete.
5. Entfernen Sie den `.NETStandard.Library`-Verweis, und ersetzen Sie ihn durch die kopierten Pakete.
6. Entfernen Sie Verweise auf Pakete, die Sie nicht benötigen.

Auf eine der folgenden Weisen können Sie herausfinden, welche Pakete Sie nicht benötigen:

1. Ausprobieren:  Bei dieser Methode entfernen Sie ein Paket, stellen es wieder her, nehmen zur Kenntnis, ob Ihre Bibliothek immer noch kompiliert, und wiederholen diesen Prozess.
2. Verwenden eines Tools zum Ansehen von Verweisen wie z.B. [ILSpy](http://ilspy.net) oder [.NET Reflector](http://www.red-gate.com/products/dotnet-development/reflector), um zu sehen, was Ihr Code tatsächlich verwendet.  Anschließend können Sie Pakete entfernen, die nicht den Typen entsprechen, die Sie verwenden.

## <a name="example"></a>Beispiel 

Stellen Sie sich vor, dass Sie eine Bibliothek geschrieben haben, die zusätzliche Funktionen für generische Sammlungstypen bereitstellt.  Eine solche Bibliothek müsste von Paketen wie z.B. `System.Collections` abhängen, hängt möglicherweise aber überhaupt nicht von Paketen wie z.B. `System.Net.Http` ab.  Daher wäre es gut, Paketabhängigkeiten auf nur das zu beschränken, was die Bibliothek tatsächlich benötigt.

Um diese Bibliothek zu beschränken, beginnen Sie mit der `project.json`-Datei, und fügen Sie einen Verweis zu `NETStandard.Library` Version `1.6.0` hinzu.

```json
{
    "version":"1.0.0",
    "dependencies":{
        "NETStandard.Library":"1.6.0"
    },
    "frameworks": {
        "netstandard1.0": {}
     }
}
```

Als Nächstes stellen Sie Pakete mit `dotnet restore` wieder her, prüfen die Datei `project.lock.json` und suchen alle für `NETSTandard.Library` wiederhergestellten Pakete.

So sieht der entsprechende Abschnitt in der Datei `project.lock.json` aus, wenn auf `netstandard1.0` abgezielt wird:

```json
"NETStandard.Library/1.6.0":{
    "type": "package",
    "dependencies": {
        "Microsoft.NETCore.Platforms": "1.0.1",
        "Microsoft.NETCore.Runtime": "1.0.2",
        "System.Collections": "4.0.11",
        "System.Diagnostics.Debug": "4.0.11",
        "System.Diagnostics.Tools": "4.0.1",
        "System.Globalization": "4.0.11",
        "System.IO": "4.1.0",
        "System.Linq": "4.1.0",
        "System.Net.Primitives": "4.0.11",
        "System.ObjectModel": "4.0.12",
        "System.Reflection": "4.1.0",
        "System.Reflection.Extensions": "4.0.1",
        "System.Reflection.Primitives": "4.0.1",
        "System.Resources.ResourceManager": "4.0.1",
        "System.Runtime": "4.1.0",
        "System.Runtime.Extensions": "4.1.0",
        "System.Text.Encoding": "4.0.11",
        "System.Text.Encoding.Extensions": "4.0.11",
        "System.Text.RegularExpressions": "4.1.0",
        "System.Threading": "4.0.11",
        "System.Threading.Tasks": "4.0.11",
        "System.Xml.ReaderWriter": "4.0.11",
        "System.Xml.XDocument": "4.0.11"
    }
}
```

Kopieren Sie als Nächstes die Paketverweise in den `dependencies`-Abschnitt der `project.json`-Datei der Bibliothek, und ersetzen Sie den `NETStandard.Library`-Verweis:

```json
{
    "version":"1.0.0",
    "dependencies":{
        "Microsoft.NETCore.Platforms": "1.0.1",
        "Microsoft.NETCore.Runtime": "1.0.2",
        "System.Collections": "4.0.11",
        "System.Diagnostics.Debug": "4.0.11",
        "System.Diagnostics.Tools": "4.0.1",
        "System.Globalization": "4.0.11",
        "System.IO": "4.1.0",
        "System.Linq": "4.1.0",
        "System.Net.Primitives": "4.0.11",
        "System.ObjectModel": "4.0.12",
        "System.Reflection": "4.1.0",
        "System.Reflection.Extensions": "4.0.1",
        "System.Reflection.Primitives": "4.0.1",
        "System.Resources.ResourceManager": "4.0.1",
        "System.Runtime": "4.1.0",
        "System.Runtime.Extensions": "4.1.0",
        "System.Text.Encoding": "4.0.11",
        "System.Text.Encoding.Extensions": "4.0.11",
        "System.Text.RegularExpressions": "4.1.0",
        "System.Threading": "4.0.11",
        "System.Threading.Tasks": "4.0.11",
        "System.Xml.ReaderWriter": "4.0.11",
        "System.Xml.XDocument": "4.0.11"
    },
    "frameworks":{
        "netstandard1.0": {}
    }
}
```

Das sind ziemlich viele Pakete, die sicherlich nicht zum Erweitern von Sammlungstypen benötigt werden.  Sie können Pakete entweder manuell entfernen oder ein Tool wie z.B. [ILSpy](http://ilspy.net) oder [.NET Reflector](http://www.red-gate.com/products/dotnet-development/reflector) verwenden, um zu bestimmen, welche Pakete Ihr Code tatsächlich verwendet.

So könnte ein eingeschränktes Paket aussehen:

```json
{
    "dependencies":{
        "Microsoft.NETCore.Platforms": "1.0.1",
        "Microsoft.NETCore.Runtime": "1.0.2",
        "System.Collections": "4.0.11",
        "System.Linq": "4.1.0",
        "System.Runtime": "4.1.0",
        "System.Runtime.Extensions": "4.1.0",
        "System.Runtime.Handles": "4.0.1",
        "System.Runtime.InteropServices": "4.1.0",
        "System.Runtime.InteropServices.RuntimeInformation": "4.0.0",
        "System.Threading.Tasks": "4.0.11"
    },
    "frameworks":{
        "netstandard1.0": {}
     }
}
```

Nun hat es einen geringeren Speicherbedarf als wenn es vom `NETStandard.Library`-Metapaket abhängen würde.

