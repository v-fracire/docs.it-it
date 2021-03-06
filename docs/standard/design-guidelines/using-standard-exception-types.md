---
title: Utilizzo di tipi di eccezioni standard
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- throwing exceptions, standard types
- catching exceptions
- exceptions, catching
- exceptions, throwing
ms.assetid: ab22ce03-78f9-4dca-8824-c7ed3bdccc27
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9ea4a61be3a76c30c564cbf98ba3318fc6c3e7d4
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/26/2018
ms.locfileid: "47216095"
---
# <a name="using-standard-exception-types"></a>Utilizzo di tipi di eccezioni standard
In questa sezione descrive le eccezioni standard fornite dal Framework e i dettagli del loro utilizzo. L'elenco è in alcun modo esaustivo. Consultare la documentazione di riferimento di .NET Framework per l'utilizzo di altri Framework dei tipi di eccezione.  
  
## <a name="exception-and-systemexception"></a>Eccezione e SystemException  
 **X DO NOT** throw <xref:System.Exception?displayProperty=nameWithType> o <xref:System.SystemException?displayProperty=nameWithType>.  
  
 **X DO NOT** catch `System.Exception` o `System.SystemException` nel codice del framework, a meno che non si intende generare di nuovo.  
  
 **X AVOID** intercettazione `System.Exception` o `System.SystemException`, ad eccezione dei gestori di eccezioni di livello superiore.  
  
## <a name="applicationexception"></a>ApplicationException  
 **X DO NOT** generare o derivare da <xref:System.ApplicationException>.  
  
## <a name="invalidoperationexception"></a>InvalidOperationException  
 **✓ DO** generano un <xref:System.InvalidOperationException> se l'oggetto è in uno stato non appropriato.  
  
## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a>ArgumentException ArgumentNullException e dell'eccezione ArgumentOutOfRangeException  
 **✓ DO** throw <xref:System.ArgumentException> o uno dei sottotipi se a un membro vengono passati argomenti non validi. Preferisce il tipo più derivato di eccezione, se applicabile.  
  
 **✓ DO** impostare il `ParamName` proprietà durante la generazione di una delle sottoclassi di `ArgumentException`.  
  
 Questa proprietà rappresenta il nome del parametro che ha causato l'eccezione viene generata. Si noti che la proprietà può essere impostata usando uno degli overload del costruttore.  
  
 **✓ DO** utilizzare `value` per il nome del parametro del valore implicito dell'impostazione delle proprietà.  
  
## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a>NullReferenceException e IndexOutOfRangeException AccessViolationException  
 **X DO NOT** consentire pubblicamente disponibile per la chiamata API generare in modo esplicito o implicito <xref:System.NullReferenceException>, <xref:System.AccessViolationException>, o <xref:System.IndexOutOfRangeException>. Queste eccezioni sono riservate e generate dal motore di esecuzione e nella che maggior parte dei casi indica un bug.  
  
 Eseguire un controllo per evitare la generazione di queste eccezioni di argomento. Generazione di queste eccezioni espone i dettagli di implementazione del metodo che possono cambiare nel tempo.  
  
## <a name="stackoverflowexception"></a>StackOverflowException  
 **X DO NOT** generare in modo esplicito <xref:System.StackOverflowException>. L'eccezione deve essere generato in modo esplicito solo da CLR.  
  
 **X DO NOT** catch `StackOverflowException`.  
  
 È quasi impossibile scrivere il codice gestito che rimane consistente in presenza di un overflow dello stack arbitrario. Le parti non gestite di Common Language Runtime rimangano coerente per l'uso di probe per spostare gli overflow dello stack a posizioni ben definiti anziché per il backup da un overflow dello stack arbitrario.  
  
## <a name="outofmemoryexception"></a>OutOfMemoryException  
 **X DO NOT** generare in modo esplicito <xref:System.OutOfMemoryException>. Questa eccezione viene generata solo dall'infrastruttura di CLR.  
  
## <a name="comexception-sehexception-and-executionengineexception"></a>ComException SEHException ed ExecutionEngineException  
 **X DO NOT** generare in modo esplicito <xref:System.Runtime.InteropServices.COMException>, <xref:System.ExecutionEngineException>, e <xref:System.Runtime.InteropServices.SEHException>. Queste eccezioni devono essere generate solo dall'infrastruttura di CLR.  
  
 *Parti protette da copyright © 2005, 2009 Microsoft Corporation. Tutti i diritti riservati.*  
  
 *Ristampato con l'autorizzazione di Pearson Education, Inc. da [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2a edizione](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) di Krzysztof Cwalina and Brad Abrams, pubblicato il 22 ottobre 2008 da Addison-Wesley Professional nella collana Microsoft Windows Development Series.*  
  
## <a name="see-also"></a>Vedere anche

- [Linee guida per la progettazione di Framework](../../../docs/standard/design-guidelines/index.md)  
- [Linee guida di progettazione delle eccezioni](../../../docs/standard/design-guidelines/exceptions.md)
