---
title: "UI Automation Control Patterns Overview | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "control patterns"
  - "UI Automation, control patterns"
ms.assetid: cc229b33-234b-469b-ad60-f0254f32d45d
caps.latest.revision: 34
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 33
---
# UI Automation Control Patterns Overview
> [!NOTE]
>  Diese Dokumentation ist für .NET Framework\-Entwickler vorgesehen, die die verwalteten [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]\-Klassen verwenden möchten, die im <xref:System.Windows.Automation>\-Namespace definiert sind. Aktuelle Informationen zur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] finden Sie auf der Seite zur [Windows\-Automatisierungs\-API: UI\-Automatisierung](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 In dieser Übersicht werden [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]\-Steuerelementmuster vorgestellt. Steuerelementmuster bieten eine Möglichkeit zum Kategorisieren und Verfügbarmachen der Funktionalität eines Steuerelements, unabhängig vom Typ des Steuerelements oder vom Erscheinungsbild des Steuerelements.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] verwendet Steuerelementmuster, um allgemeine Verhaltensweisen von Steuerelementen abzubilden. Beispielsweise verwenden Sie das Aufruf\-Steuerelementmuster für Steuerelemente, die aufgerufen werden können \(etwa Schaltflächen\), und das Scroll\-Steuerelementmuster für Steuerelemente, die Scrollleisten haben \(z. B. Listenfelder, Listenansichten oder Kombinationsfelder\). Da mit jedem Steuerelementmuster eine separate Funktionalität abgebildet wird, können diese kombiniert werden, um den gesamten Funktionsumfang zu beschreiben, der von einem bestimmten Steuerelement unterstützt wird.  
  
> [!NOTE]
>  Zusammengesetzte Steuerelemente – Steuerelemente, die mit untergeordneten Steuerelementen erstellt wurden, die die [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] für Funktionalität bereitstellen, die vom übergeordneten Steuerelement verfügbar gemacht wird – sollten alle Steuerelementmuster implementieren, die normalerweise den untergeordneten Steuerelementen zugewiesen sind. Dagegen ist es nicht erforderlich, dass diese selben Steuerelementmuster durch die untergeordneten Steuerelemente implementiert werden.  
  
<a name="uiautomation_control_pattern_includes"></a>   
## Komponenten der Steuerelementmuster für Benutzeroberflächenautomatisierung  
 Steuerelementmuster unterstützen die Methoden, Eigenschaften, Ereignisse und Beziehungen, die dazu erforderlich sind, eine bestimmte Funktionalität zu definieren, die in einem Steuerelement verfügbar ist.  
  
-   Die Beziehungen zwischen einem Benutzeroberflächenautomatisierungs\-Element und dessen übergeordnetem Element sowie dessen unter\- und gleichgeordneten Elementen beschreibt die Struktur des Elements innerhalb der [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]\-Struktur.  
  
-   Die Methoden ermöglichen es Benutzeroberflächenautomatisierungs\-Clients, das Steuerelement zu bearbeiten.  
  
-   Die Eigenschaften und Ereignisse stellen Informationen zur Funktionalität des Steuerelementmusters sowie zum Status des Steuerelements zur Verfügung.  
  
 Steuerelementmuster beziehen sich so auf [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], wie sich Schnittstellen auf [!INCLUDE[TLA#tla_com](../../../includes/tlasharptla-com-md.md)]\-Objekte beziehen. In [!INCLUDE[TLA2#tla_com](../../../includes/tla2sharptla-com-md.md)] können Sie ein Objekt daraufhin abfragen, welche Schnittstellen es unterstützt, und dann diese Schnittstellen verwenden, um auf die Funktionalität zuzugreifen. In [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] kann ein Benutzeroberflächenautomatisierungs\-Client ein Steuerelement daraufhin abfragen, welche Steuerelementmuster es unterstützt, und anschließend über die Eigenschaften, Methoden, Ereignisse und Strukturen, die von den unterstützten Steuerelementmustern verfügbar gemacht werden, auf das Steuerelement zugreifen. Beispielsweise implementiert ein Benutzeroberflächenautomatisierungs\-Anbieter für ein mehrzeiliges Bearbeitungsfeld eine <xref:System.Windows.Automation.Provider.IScrollProvider>\-Schnittstelle. Wenn ein Client weiß, dass ein <xref:System.Windows.Automation.AutomationElement> das <xref:System.Windows.Automation.ScrollPattern>\-Steuerelementmuster unterstützt, kann er die Eigenschaften, Methoden und Ereignisse, die von diesem Steuerelementmuster verfügbar gemacht werden, dazu verwenden, auf das Steuerelement oder auf Informationen über das Steuerelement zuzugreifen.  
  
<a name="uiautomation_control_pattern_client_provider"></a>   
## Benutzeroberflächenautomatisierungs\-Anbieter und \-Clients  
 Benutzeroberflächenautomatisierungs\-Anbieter implementieren Steuerelementmuster, um das entsprechende Verhalten für eine bestimmte Funktionalität verfügbar zu machen, die vom Steuerelement unterstützt wird.  
  
 Benutzeroberflächenautomatisierungs\-Clients verwenden Methoden und Eigenschaften von [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]\-Steuerelement\-Musterklassen, um Informationen über die [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] abzurufen oder Änderungen an der [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] vorzunehmen. Diese Steuerelement\-Musterklassen befinden sich im <xref:System.Windows.Automation>\-Namespace \(z. B. <xref:System.Windows.Automation.InvokePattern> und <xref:System.Windows.Automation.SelectionPattern>\).  
  
 Clients verwenden <xref:System.Windows.Automation.AutomationElement>\-Methoden \(etwa <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=fullName> oder <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=fullName>\) oder die [!INCLUDE[TLA#tla_clr](../../../includes/tlasharptla-clr-md.md)]\-Accessoren, um auf die [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]\-Eigenschaften für ein Muster zuzugreifen. Jede Steuerelementmusterklasse hat einen Feldmember \(z. B. <xref:System.Windows.Automation.InvokePattern.Pattern?displayProperty=fullName>`` oder <xref:System.Windows.Automation.SelectionPattern.Pattern?displayProperty=fullName>\), der das Steuerelementmuster kennzeichnet und als Parameter an <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> oder <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> übergeben werden kann, um dieses Muster für ein <xref:System.Windows.Automation.AutomationElement> abzurufen.  
  
<a name="uiautomation_control_patterns_dynamic"></a>   
## Dynamische Steuerelementmuster  
 Einige Steuerelemente unterstützen nicht immer denselben Satz von Steuerelementmustern. Steuerelementmuster gelten als unterstützt, wenn sie für einen Benutzeroberflächenautomatisierungs\-Client verfügbar sind. Beispielsweise ermöglicht ein mehrzeiliges Bearbeitungsfeld nur dann vertikales Scrollen, wenn es mehr Textzeilen enthält, als in seinem Anzeigebereich angezeigt werden können. Scrollen wird deaktiviert, wenn so viel Text entfernt wurde, dass kein Scrollen mehr erforderlich ist. In diesem Beispiel wird das ScrollPattern\-Steuerelementmuster dynamisch je nach aktuellem Zustand des Steuerelements unterstützt \(wie viel Text befindet sich im Bearbeitungsfeld\).  
  
<a name="Control_Pattern_Classes_and_Interfaces"></a>   
## Steuerelement\-Musterklassen und \-Schnittstellen  
 In der folgenden Tabelle werden die [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]\-Steuerelementmuster beschrieben. Außerdem werden in dieser Tabelle folgende Elemente aufgeführt: die Klassen, die von Benutzeroberflächenautomatisierungs\-Clients für den Zugriff auf die Steuerelementmuster verwendet werden, und die Schnittstellen, die von Benutzeroberflächenautomatisierungs\-Anbietern zum Implementieren der Steuerelementmuster verwendet werden.  
  
|Steuerelementmusterklasse|Anbieterschnittstelle|Beschreibung|  
|-------------------------------|---------------------------|------------------|  
|<xref:System.Windows.Automation.DockPattern>|<xref:System.Windows.Automation.Provider.IDockProvider>|Wird für Steuerelemente verwendet, die in einem Dockingcontainer angedockt werden können. Beispielsweise Symbolleisten oder Toolpaletten.|  
|<xref:System.Windows.Automation.ExpandCollapsePattern>|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Wird für Steuerelemente verwendet, die erweitert oder reduziert werden können. Beispielsweise Menüelemente in einer Anwendung, etwa das Menü **Datei**.|  
|<xref:System.Windows.Automation.GridPattern>|<xref:System.Windows.Automation.Provider.IGridProvider>|Wird für Steuerelemente verwendet, die Rasterfunktionen wie z. B. Größenanpassung und Verschieben in eine bestimmte Zelle unterstützen. Beispielsweise die große Symbolansicht in Windows\-Explorer oder einfache Tabellen ohne Überschriften in [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)].|  
|<xref:System.Windows.Automation.GridItemPattern>|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Wird für Steuerelemente verwendet, die Zellen innerhalb von Rastern haben. Die einzelnen Zellen müssen das GridItem\-Muster unterstützen. Beispielsweise jede Zelle in der [!INCLUDE[TLA#tla_winexpl](../../../includes/tlasharptla-winexpl-md.md)]\-Detailansicht.|  
|<xref:System.Windows.Automation.InvokePattern>|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Wird für Steuerelemente verwendet, die aufgerufen werden können, etwa Schaltflächen.|  
|<xref:System.Windows.Automation.MultipleViewPattern>|<xref:System.Windows.Automation.Provider.IMultipleViewProvider>|Wird für Steuerelemente verwendet, die zwischen mehreren Darstellungen derselben Informationen, Daten oder untergeordneten Elemente wechseln können. Beispielsweise ein Listenansicht\-Steuerelement, in dem Daten in einer Miniatur\-, Kachel\-, Symbol\-, Listen\- oder Detailansicht verfügbar sind.|  
|<xref:System.Windows.Automation.RangeValuePattern>|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Wird für Steuerelemente verwendet, die einen Bereich von Werten haben, die auf das Steuerelement angewendet werden können. Beispielsweise kann ein Drehfeld\-Steuerelement, das Jahreswerte enthält, einen Bereich von 1900 bis 2010 haben, während ein anderes Drehfeld\-Steuerelement, in dem Monate angezeigt werden, den Bereich von 1 bis 12 hat.|  
|<xref:System.Windows.Automation.ScrollPattern>|<xref:System.Windows.Automation.Provider.IScrollProvider>|Wird für Steuerelemente verwendet, in denen gescrollt werden kann. Beispielsweise ein Steuerelement, das Scrollleisten hat, die nur aktiv sind, wenn mehr Informationen vorhanden sind, als im Anzeigebereich des Steuerelements angezeigt werden können.|  
|<xref:System.Windows.Automation.ScrollItemPattern>|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Wird für Steuerelemente verwendet, die einzelne Elemente in einer Liste haben, die gescrollt werden kann. Beispielsweise ein Listensteuerelement, das einzelne Elementen in der Scrollliste hat, etwa ein Kombinationsfeld\-Steuerelement.|  
|<xref:System.Windows.Automation.SelectionPattern>|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Wird für Auswahlcontainer\-Steuerelemente verwendet. Beispielsweise Listen\- und Kombinationsfelder.|  
|<xref:System.Windows.Automation.SelectionItemPattern>|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Wird für einzelne Elemente in Auswahlcontainer\-Steuerelementen verwendet, z. B. Listen\- und Kombinationsfelder.|  
|<xref:System.Windows.Automation.TablePattern>|<xref:System.Windows.Automation.Provider.ITableProvider>|Wird für Steuerelemente verwendet, die sowohl ein Raster als auch Überschrifteninformationen haben. Beispielsweise [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)]\-Arbeitsblätter.|  
|<xref:System.Windows.Automation.TableItemPattern>|<xref:System.Windows.Automation.Provider.ITableItemProvider>|Wird für Elemente in einer Tabelle verwendet.|  
|<xref:System.Windows.Automation.TextPattern>|<xref:System.Windows.Automation.Provider.ITextProvider>|Wird für Bearbeitungssteuerelemente und Dokumente verwendet, die Textinformationen verfügbar machen.|  
|<xref:System.Windows.Automation.TogglePattern>|<xref:System.Windows.Automation.Provider.IToggleProvider>|Wird für Steuerelemente verwendet, deren Zustand umgeschaltet werden kann. Beispielsweise Kontrollkästchen und aktivierbare Menüeinträge.|  
|<xref:System.Windows.Automation.TransformPattern>|<xref:System.Windows.Automation.Provider.ITransformProvider>|Wird für Steuerelemente verwendet, die in der Größe geändert, verschoben und gedreht werden können. Typische Einsatzfälle für das Transform\-Steuerelementmuster sind Designer, Formulare, Grafik\-Editoren und Zeichnungsanwendung.|  
|<xref:System.Windows.Automation.ValuePattern>|<xref:System.Windows.Automation.Provider.IValueProvider>|Ermöglicht Clients das Abrufen oder Festlegen eines Werts für ein Steuerelement, das keinen Wertebereich unterstützt. Beispielsweise eine Datums\-\/Zeitauswahl.|  
|<xref:System.Windows.Automation.WindowPattern>|<xref:System.Windows.Automation.Provider.IWindowProvider>|Macht fensterspezifische Informationen verfügbar. Dies ist ein grundlegendes Konzept für [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)]. Zu den Beispielen für Steuerelemente, die Fenster sind, gehören Anwendungsfenster der obersten Ebene \([!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)], [!INCLUDE[TLA#tla_winexpl](../../../includes/tlasharptla-winexpl-md.md)] usw.\), untergeordnete [!INCLUDE[TLA#tla_mdi](../../../includes/tlasharptla-mdi-md.md)]\-Fenster und Dialogfelder.|  
  
## Siehe auch  
 [UI Automation Control Patterns for Clients](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)   
 [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)   
 [UI Automation Overview](../../../docs/framework/ui-automation/ui-automation-overview.md)   
 [UI Automation Properties for Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)   
 [UI Automation Events for Clients](../../../docs/framework/ui-automation/ui-automation-events-for-clients.md)