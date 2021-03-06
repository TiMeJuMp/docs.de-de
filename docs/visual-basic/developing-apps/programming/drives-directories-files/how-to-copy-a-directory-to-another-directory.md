---
title: 'Gewusst wie: Kopieren eines Verzeichnisses in ein anderes Verzeichnis in Visual Basic'
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- I/O [Visual Basic], copying directories
- I/O [Visual Basic], copying folders
- folders [Visual Basic], copying
- directories [Visual Basic], copying
ms.assetid: 2a370bd7-10ba-4219-afc4-4519d031eb6c
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 7bcc7f924d26247b0d0ab30a9ea0fc6d6333b652
ms.contentlocale: de-de
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-copy-a-directory-to-another-directory-in-visual-basic"></a>Gewusst wie: Kopieren eines Verzeichnisses in ein anderes Verzeichnis in Visual Basic
Verwenden Sie die <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A>-Methode zum Kopieren eines Verzeichnisses in ein anderes Verzeichnis. Diese Methode kopiert den Inhalt des Verzeichnisses sowie das Verzeichnis selbst. Wenn das Zielverzeichnis nicht vorhanden ist, wird es erstellt. Wenn ein Verzeichnis mit dem gleichen Namen am Zielspeicherort vorhanden ist und `overwrite` auf `False` festgelegt ist, werden die Inhalte der beiden Verzeichnisse zusammengeführt. Sie können während des Vorgangs einen neuen Namen für das Verzeichnis angeben.  
  
 Beim Kopieren von Dateien innerhalb eines Verzeichnisses können Ausnahmen ausgelöst werden, die durch eine bestimmte Datei verursacht werden. Dies kann zum Beispiel eine Datei sein, die während einer Zusammenführung vorhanden ist, wenn `overwrite` auf `False` festgelegt ist. Wenn solche Ausnahmen ausgelöst werden, werden sie zu einer einzigen Ausnahme konsolidiert, deren `Data`-Eigenschaft Einträge enthält, in denen der Datei- oder Verzeichnispfad der Schlüssel ist und die spezifische Ausnahmemeldung im entsprechenden Wert enthalten ist.  
  
### <a name="to-copy-a-directory-to-another-directory"></a>Kopieren eines Verzeichnisses in ein anderes Verzeichnis  
  
-   Verwenden Sie die `CopyDirectory`-Methode, um Verzeichnisnamen von Quelle und Ziel anzugeben. Im folgenden Beispiel wird das Verzeichnis mit dem Namen `TestDirectory1` in `TestDirectory2` kopiert, wobei vorhandene Dateien überschrieben werden.  
  
     [!code-vb[VbVbcnMyFileSystem#16](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-a-directory-to-another-directory_1.vb)]  
  
     Dieses Codebeispiel ist auch als IntelliSense-Codeausschnitt verfügbar. In der Codeausschnittauswahl befindet es sich unter **Dateisystem – Verarbeiten von Laufwerken, Ordnern und Dateien**. Weitere Informationen finden Sie unter [Codeausschnitte](/visualstudio/ide/code-snippets).  
  
## <a name="robust-programming"></a>Stabile Programmierung  
 Die folgenden Bedingungen können einen Ausnahmefehler verursachen:  
  
-   Der neue Name, der für das Verzeichnis angegeben wird, enthält einen Doppelpunkt (:) oder einen Schrägstrich (\ oder /) (<xref:System.ArgumentException>).  
  
-   Der Pfad ist aus einem der folgenden Gründe ungültig: Er ist eine Zeichenfolge der Länge 0, er enthält nur Leerzeichen, er enthält ungültige Zeichen, oder er ist ein Gerätepfad (beginnt mit \\\\.\\) (<xref:System.ArgumentException>).  
  
-   Der Pfad ist ungültig, da er `Nothing` ist (<xref:System.ArgumentNullException>).  
  
-   `destinationDirectoryName` ist `Nothing` oder eine leere Zeichenfolge (<xref:System.ArgumentNullException>).  
  
-   Das Quellverzeichnis ist nicht vorhanden (<xref:System.IO.DirectoryNotFoundException>).  
  
-   Das Quellverzeichnis ist ein Stammverzeichnis (<xref:System.IO.IOException>).  
  
-   Der kombinierte Pfad verweist auf eine vorhandene Datei (<xref:System.IO.IOException>).  
  
-   Der Quellpfad und der Zielpfad sind identisch (<xref:System.IO.IOException>).  
  
-   `ShowUI` ist auf `UIOption.AllDialogs` festgelegt, und der Benutzer bricht den Vorgang ab, oder eine oder mehrere Dateien im Verzeichnis können nicht kopiert werden (<xref:System.OperationCanceledException>).  
  
-   Der Vorgang ist zyklisch (<xref:System.InvalidOperationException>).  
  
-   Der Pfad enthält einen Doppelpunkt (:) (<xref:System.NotSupportedException>).  
  
-   Der Pfad überschreitet die im System definierte maximale Länge (<xref:System.IO.PathTooLongException>).  
  
-   Der Pfad eines Datei- oder Ordnernamens enthält einen Doppelpunkt (:) oder weist ein ungültiges Format auf (<xref:System.NotSupportedException>).  
  
-   Dem Benutzer fehlen die erforderlichen Berechtigungen zum Anzeigen des Pfades (<xref:System.Security.SecurityException>).  
  
-   Eine Zieldatei ist vorhanden, aber nicht zugänglich (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A>   
 [Gewusst wie: Suchen nach Unterverzeichnissen mit einem bestimmten Muster](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)   
 [Gewusst wie: Abrufen einer Sammlung von Dateien in einem Verzeichnis](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)

