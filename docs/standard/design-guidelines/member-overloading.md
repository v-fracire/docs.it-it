---
title: Overload dei membri
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- default arguments
- members [.NET Framework], overloaded
- member design guidelines [.NET Framework], overloading
- overloaded members
- signatures, members
ms.assetid: 964ba19e-8b94-4b5b-b1e3-5a0b531a0bb1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2127497d294cbfd4e1bb24d033f432378627ff13
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/17/2018
ms.locfileid: "45964202"
---
# <a name="member-overloading"></a>Overload dei membri
Overload dei membri prevede la creazione di due o più membri sullo stesso tipo che si differenziano solo per il numero o il tipo dei parametri, ma hanno lo stesso nome. Ad esempio, in quanto segue, il `WriteLine` è l'overload di metodo:  
  
```  
public static class Console {  
    public void WriteLine();  
    public void WriteLine(string value);  
    public void WriteLine(bool value);  
    ...  
}  
```  
  
 Poiché solo metodi, costruttori e proprietà indicizzate possono avere parametri, solo i membri possono essere sottoposti a overload.  
  
 L'overload è una delle tecniche più importanti per migliorare l'usabilità, la produttività e migliorare la leggibilità delle librerie riutilizzabili. L'overload per il numero di parametri rende possibile fornire versioni semplificate di costruttori e metodi. L'overload del tipo di parametro rende possibile usare lo stesso nome di membro per i membri identici operazioni su un set selezionato di tipi diversi.  
  
 **✓ DO** tenta di utilizzare nomi di parametro descrittivi per indicare il valore predefinito utilizzato dagli overload più breve.  
  
 **X AVOID** arbitrariamente i nomi dei parametri in overload. Se un parametro in uno degli overload rappresenta lo stesso input di un parametro in un altro overload, tali parametri devono avere lo stesso nome.  
  
 **X AVOID** incoerente nell'ordine dei parametri in membri di overload. I parametri con lo stesso nome verrà visualizzato nella stessa posizione in tutti gli overload.  
  
 **✓ DO** rendere virtuale solo l'overload più lunga (se estendibilità è obbligatoria). Overload più breve deve semplicemente eseguire chiamate a un overload più lungo.  
  
 **X DO NOT** usare `ref` o `out` modificatori per eseguire l'overload di membri.  
  
 Alcuni linguaggi non possono risolvere le chiamate agli overload simile al seguente. Inoltre, tali overload in genere hanno una semantica completamente diversa e probabilmente non deve essere overload, ma due metodi distinti invece.  
  
 **X DO NOT** dispongono di overload con parametri nella stessa posizione e tipi simili ma con una semantica diversa.  
  
 **✓ DO** consentire `null` da passare per gli argomenti facoltativi.  
  
 **✓ DO** utilizzare l'overload dei membri anziché definire membri con argomenti predefiniti.  
  
 Gli argomenti predefiniti non sono conformi a CLS.  
  
 *Parti protette da copyright © 2005, 2009 Microsoft Corporation. Tutti i diritti riservati.*  
  
 *Ristampato con l'autorizzazione di Pearson Education, Inc. da [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2a edizione](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) di Krzysztof Cwalina and Brad Abrams, pubblicato il 22 ottobre 2008 da Addison-Wesley Professional nella collana Microsoft Windows Development Series.*  
  
## <a name="see-also"></a>Vedere anche

- [Linee guida di progettazione dei membri](../../../docs/standard/design-guidelines/member.md)  
- [Linee guida per la progettazione di Framework](../../../docs/standard/design-guidelines/index.md)
