---
title: Classi base per l'implementazione di astrazioni
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- abstractions [.NET Framework]
- base classes, abstractions
ms.assetid: 37a2d9a4-9721-482a-a40f-eee2c1d97875
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f326ee895251678c7a23ea84a11e83951edf2cc
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2018
ms.locfileid: "45677071"
---
# <a name="base-classes-for-implementing-abstractions"></a>Classi base per l'implementazione di astrazioni
In teoria, una classe diventa una classe di base quando un'altra classe viene derivata da essa. Ai fini di questa sezione, tuttavia, una classe di base è una classe progettata principalmente per fornire un'astrazione comune o per altre classi di riutilizzare alcuni implementazione tuttavia l'ereditarietà predefinita. Le classi di base si trovano in genere al centro le gerarchie di ereditarietà, tra diverse implementazioni personalizzate nella parte inferiore e un'astrazione a livello di radice di una gerarchia.  
  
 Vengono usati come gli helper di implementazione per l'implementazione di astrazioni. Ad esempio, una delle astrazioni del Framework per le raccolte ordinate di elementi è il <xref:System.Collections.Generic.IList%601> interfaccia. Implementazione <xref:System.Collections.Generic.IList%601> non è semplice, e pertanto il Framework fornisce diverse classi di base, ad esempio <xref:System.Collections.ObjectModel.Collection%601> e <xref:System.Collections.ObjectModel.KeyedCollection%602>, che fungono da helper per l'implementazione di raccolte personalizzate.  
  
 Le classi di base in genere non sono adatte per essere utilizzato come astrazioni di per sé, perché tendono a contenere una quantità eccessiva di implementazione. Ad esempio, il `Collection<T>` classe di base contiene un numero elevato di implementazione correlato al fatto che implementa il metodo non generico `IList` interfaccia (per l'integrazione migliore con le raccolte non generiche) e del fatto che è una raccolta di elementi archiviati in memoria in uno dei relativi campi.  
  
 Come indicato in precedenza, le classi di base possono fornire Guida in linea preziosissima per gli utenti che devono implementare le astrazioni, ma allo stesso tempo può essere un ostacolo significativo. Aggiungono superficie di attacco e aumentare la profondità delle gerarchie di ereditarietà e quindi concettualmente complicare il framework. Di conseguenza, le classi di base devono essere utilizzate solo se offrono un valore significativo per gli utenti del framework. È preferibile evitarli se offrono valore solo per gli implementatori di framework, in cui deve essere fortemente considerata case delega a un'implementazione interna invece dell'ereditarietà da una classe base.  
  
 **✓ CONSIDER** astratta le classi di base che anche se non contengono alcun membro astratto. Ciò comunica agli utenti che la classe è progettata esclusivamente per essere ereditata da.  
  
 **✓ CONSIDER** posizionando le classi di base in uno spazio dei nomi separato dai tipi di scenario principale. Per definizione, le classi di base sono destinate agli scenari di estendibilità avanzata e pertanto non sono utili per la maggior parte degli utenti.  
  
 **X AVOID** denominazione delle classi di base con un suffisso "Base" se la classe è destinata all'utilizzo nelle API pubbliche.  
  
 *Parti protette da copyright © 2005, 2009 Microsoft Corporation. Tutti i diritti riservati.*  
  
 *Ristampato con l'autorizzazione di Pearson Education, Inc. da [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2a edizione](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) di Krzysztof Cwalina and Brad Abrams, pubblicato il 22 ottobre 2008 da Addison-Wesley Professional nella collana Microsoft Windows Development Series.*  
  
## <a name="see-also"></a>Vedere anche

- [Linee guida per la progettazione di Framework](../../../docs/standard/design-guidelines/index.md)  
- [Progettazione finalizzata all'estensibilità](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
