---
title: Eventi e callback
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- events [.NET Framework], extensibility
- methods [.NET Framework], callback
- callback methods
- callbacks
ms.assetid: 48b55c60-495f-4089-9396-97f9122bba7c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 390c12af7107bb78fc261c55ea15390cf9eaa5b7
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2018
ms.locfileid: "43862949"
---
# <a name="events-and-callbacks"></a>Eventi e callback
I callback sono punti di estendibilità che consentono un framework di eseguire il callback nel codice utente attraverso un delegato. Questi delegati vengono in genere passati al framework tramite un parametro di un metodo.  
  
 Gli eventi sono un caso speciale di callback che supporta la sintassi semplice e uniforme per fornire il delegato (un gestore eventi). Inoltre, il completamento delle istruzioni e le finestre di progettazione di Visual Studio forniscono informazioni sull'uso di API basate su eventi. (Vedere [progettazione di eventi](../../../docs/standard/design-guidelines/event.md).)  
  
 **✓ CONSIDER** utilizzando i callback per permettere agli utenti di fornire codice personalizzato deve essere eseguita dal framework.  
  
 **✓ CONSIDER** mediante gli eventi per consentire agli utenti di personalizzare il comportamento di un framework senza la necessità di informazioni sulla progettazione orientata agli oggetti.  
  
 **✓ DO** preferire eventi semplici callback, perché sono più familiari a una gamma più ampia di sviluppatori e integrati con il completamento delle istruzioni di Visual Studio.  
  
 **X AVOID** usare callback nelle API sensibili alle prestazioni.  
  
 **✓ DO** usare il nuovo `Func<...>`, `Action<...>`, o `Expression<...>` tipi anziché delegati personalizzati, quando si definiscono le API con callback.  
  
 `Func<...>` e `Action<...>` rappresentano i delegati generici. `Expression<...>` rappresenta le definizioni di funzione che possono essere compilate e successivamente richiamate in fase di esecuzione ma può anche essere serializzate e passate a processi remoti.  
  
 **✓ DO** misurare e comprendere le implicazioni sulle prestazioni dell'uso `Expression<...>`, anziché utilizzare `Func<...>` e `Action<...>` delegati.  
  
 `Expression<...>` i tipi sono logicamente equivalente alla maggior parte dei casi `Func<...>` e `Action<...>` delegati. La differenza principale tra di esse è che i delegati sono destinati a essere usato in scenari del processo locale. le espressioni sono concepite per casi in cui risulta vantaggioso e consente di valutare l'espressione in una macchina o il processo remoto.  
  
 **✓ DO** comprendere che la chiamata a un delegato, si eseguono codice arbitrario e che potrebbe avere ripercussioni sicurezza, la correttezza e compatibilità.  
  
 *Parti protette da copyright © 2005, 2009 Microsoft Corporation. Tutti i diritti riservati.*  
  
 *Ristampato con l'autorizzazione di Pearson Education, Inc. da [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2a edizione](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) di Krzysztof Cwalina and Brad Abrams, pubblicato il 22 ottobre 2008 da Addison-Wesley Professional nella collana Microsoft Windows Development Series.*  
  
## <a name="see-also"></a>Vedere anche

- [Progettazione finalizzata all'estensibilità](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
- [Linee guida per la progettazione di Framework](../../../docs/standard/design-guidelines/index.md)
