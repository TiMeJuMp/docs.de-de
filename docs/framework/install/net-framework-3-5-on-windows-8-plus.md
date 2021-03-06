---
title: Installieren von .NET Framework 3.5 auf Windows 8, Windows 8.1 und Windows 10
ms.date: 05/26/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
helpviewer_keywords:
- .NET Framework 3.5, installing on Windows 8
- Windows 8, installing .NET Framework 3.5
ms.assetid: 3eab3eb4-4573-42ac-98f8-36fb2c22c7d5
caps.latest.revision: 69
author: mairaw
ms.author: mairaw
ms.translationtype: HT
ms.sourcegitcommit: 93f77dd5c3ca61935ae98ddef15f9c5cf7644bbb
ms.openlocfilehash: e9c8dcfacff689761d9ec891db8a1a4756acece0
ms.contentlocale: de-de
ms.lasthandoff: 08/22/2017

---

# <a name="install-the-net-framework-35-on-windows-8-windows-81-and-windows-10"></a>Installieren von .NET Framework 3.5 auf Windows 8, Windows 8.1 und Windows 10

.NET Framework ist integraler Bestandteil vieler Apps unter Windows und stellt allgemeine Funktionen für diese Apps bereit. Für Entwickler bietet .NET Framework ein konsistentes Programmiermodell zum Erstellen von Apps. Wenn Sie Windows als Betriebssystem verwenden, ist .NET Framework möglicherweise bereits auf dem Computer installiert. So ist [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] in [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] in [!INCLUDE[win81](../../../includes/win81-md.md)] und [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] in Windows 10 enthalten.  
  
.NET Framework 3.5 wird jedoch nicht automatisch mit [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)] oder Windows 10 installiert und muss separat aktiviert werden, um Apps auszuführen, die davon abhängen. Dies muss über die Windows Update vorgenommen werden, diese Option kann mithilfe der folgenden drei Möglichkeiten aufgerufen werden. Dazu ist eine Internetverbindung erforderlich:  
  
- [Installieren von .NET Framework 3.5 bei Bedarf](#OnDemand)  
  
- [Aktivieren von .NET Framework 3.5 in der Systemsteuerung](#ControlPanel)  
  
- [Herunterladen des Installationsprogramms von .NET Framework 3.5](http://www.microsoft.com/en-us/download/details.aspx?id=21) (Hinweis: Hiermit wird .NET Framework nicht direkt heruntergeladen, sondern es wird ein Installationsprogramm heruntergeladen, das Windows Update aufruft.)  
  
Während der Installation tritt möglicherweise der Fehler 0x800f0906, 0x800f0907 oder 0x800f081f auf. In diesem Fall finden Sie weitere Informationen unter [.NET Framework 3.5-Installationsfehler: 0x800f0906, 0x800f0907 oder 0x800f081f](https://support.microsoft.com/help/2734782/net-framework-3-5-installation-error-0x800f0906--0x800f081f--0x800f09). Beachten Sie, dass diese Fehler möglicherweise durch die Installation des [Sicherheitsupdates 3005628](https://support.microsoft.com/kb/3005628)behoben werden können.  
  
Wenn bei den oben genannten Methoden ein Fehler auftritt, oder Sie nicht über eine Internetverbindung verfügen, müssen Sie das Windows-Installationsmedium verwenden. Weitere Informationen finden Sie unter Methode 3 für Fehler 0x800f0906 im Artikel [.NET Framework 3.5-Installationsfehler](https://support.microsoft.com/en-us/kb/2734782). Wenn keine Installationsmedien vorhanden sind, lesen Sie [Create Installation media for Windows 8.1 (Erstellen eines Installationsmediums für Windows 8.1)](http://windows.microsoft.com/en-US/windows-8/create-reset-refresh-media?woldogcb=0).  
  
**Wichtige Hinweise:**
  
- Deinstallieren Sie im Allgemeinen keine Version von .NET Framework von Ihrem Computer. Verschiedene Apps benötigen unterschiedliche Versionen von Framework, und mehrere Versionen von .NET Framework können gleichzeitig auf einen einzelnen Computer bestehen.  
  
- .NET Framework 3.5 wird auch von Apps verwendet, die für die Versionen 2.0 und 3.0 erstellt wurden.  
  
- Wenn ein Language Pack von Windows vor der Installation von .NET Framework 3.5 installiert wird, kann bei der Installation von .NET Framework 3.5 ein Fehler auftreten. Installieren Sie .NET Framework 3.5 bevor Sie die Language Packs von Windows installieren.  
  
- Windows CardSpace steht in .NET Framework 3.5 unter [!INCLUDE[win8](../../../includes/win8-md.md)]nicht zur Verfügung.  
  
- Aufgrund der Schwierigkeiten bei der Art und Weise, wie .NET Framework 3.5 installiert werden muss, ist es leider nicht möglich, ein separates, eigenständiges Installationsprogramm bereitzustellen, das unabhängig von Windows Update ausgeführt werden kann. Wenn alle anderen Methoden zu Fehlern führen, müssen Sie wie zuvor beschrieben das Installationsmedium verwenden.  
  
<a name="OnDemand"></a>   
## <a name="install-the-net-framework-35-on-demand"></a>Installieren von .NET Framework 3.5 bei Bedarf

Wenn eine App .NET Framework 3.5 erfordert, diese Version jedoch auf dem Computer nicht aktiviert ist, wird entweder während der Installation oder beim ersten Ausführen der App das folgende Meldungsfeld angezeigt. Wählen Sie im Meldungsfeld **Feature installieren** aus, um .NET Framework 3.5 zu aktivieren. Für diese Option ist eine Internetverbindung erforderlich.  
  
![Dialogfeld für die Installation von 3.5 auf Windows 8](../../../docs/framework/deployment/media/installdialog.png "installdialog")  
  
<a name="ControlPanel"></a>   
## <a name="enable-the-net-framework-35-in-control-panel"></a>Aktivieren von .NET Framework 3.5 in der Systemsteuerung

Sie können .NET Framework 3.5 auch über die Systemsteuerung aktivieren. Für diese Option ist eine Internetverbindung erforderlich.  
  
1. Drücken Sie die Windows-Taste ![Windows-Logo](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") auf der Tastatur. Geben Sie „Windows Features“ ein und drücken Sie die EINGABETASTE. Daraufhin wird das Dialogfeld **Windows-Features aktivieren oder deaktivieren** angezeigt. Alternativ können Sie die Systemsteuerung öffnen, auf die **Programm**elemente klicken und anschließend unter **Programme und Funktionen** auf **Windows-Funktionen ein- oder ausschalten** klicken.  
  
2. Aktivieren Sie das Kontrollkästchen **.NET Framework 3.5 (umfasst .NET 2.0 und 3.0)**, klicken Sie auf **OK**, und starten Sie den Computer neu, wenn Sie dazu aufgefordert werden.  
  
Sie müssen nicht die untergeordneten Elemente für die **HTTP-Aktivierung von Windows Communication Foundation (WCF)** auswählen, es sei denn, Sie sind ein Entwickler und benötigen die WCF-Funktion für Skript- und Handlerzuordnung.
  
## <a name="see-also"></a>Siehe auch

[Installationshandbuch](../../../docs/framework/get-started/index.md)

