---
title: "Zuordnungssatzende | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fe4bf1d3-047a-4a37-98c5-a66e70811346
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Zuordnungssatzende
Ein *Zuordnungssatzende* identifiziert den [Entitätstyp](../../../../docs/framework/data/adonet/entity-type.md) und die [Entitätenmenge](../../../../docs/framework/data/adonet/entity-set.md) am Ende eines [Zuordnungssatzes](../../../../docs/framework/data/adonet/association-set.md).  Zuordnungssatzenden werden als Teil eines Zuordnungssatzes definiert. Ein Zuordnungssatz muss genau zwei Zuordnungssatzenden aufweisen.  
  
 Die Definition eines Zuordnungssatzendes enthält die folgenden Informationen:  
  
-   Einen der Entitätstypen des Zuordnungssatzes.  \(erforderlich\)  
  
-   Die Entitätenmenge für den Entitätstyp im Zuordnungssatz.  \(erforderlich\)  
  
## Beispiel  
 Die unten stehende Abbildung zeigt ein konzeptionelles Modell mit zwei Zuordnungen: `WrittenBy` und `PublishedBy`.  
  
 ![Beispielmodell](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 Die folgende Abbildung zeigt einen Zuordnungssatz \(`PublishedBy`\) sowie zwei Entitätenmengen \(`Books` und `Publishers`\) auf Grundlage des oben gezeigten konzeptionellen Modells.  Die Zuordnungssatzenden sind die Entitätenmengen `Books` und `Publishers`.  Bi in der Entitätenmenge `Books` stellt eine Instanz des Entitätstyps `Book` zur Laufzeit dar.  Ebenso stellt Pj eine `Publisher`\-Instanz in der Entitätenmenge `Publishers` dar.  BiPj stellt eine Instanz der `PublishedBy`\-Zuordnung im `PublishedBy`\-Zuordnungssatz dar.  
  
 ![Festlegungsbeispiel](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")  
  
 Das [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) verwendet eine domänenspezifische Sprache \(DSL\) mit der Bezeichnung konzeptionelle Schemadefinitionssprache \([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)\), um konzeptionelle Modelle zu definieren.  Die folgende CSDL definiert einen Entitätscontainer mit einem Zuordnungssatz für jede Zuordnung in der oben gezeigten Abbildung.  Beachten Sie, dass Zuordnungssatzenden als Teil jeder Zuordnungssatzdefinition definiert werden.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## Siehe auch  
 [Schlüsselkonzepte im Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)   
 [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)