---
title: 'Operatore :: (Riferimenti per C#)'
ms.date: 07/20/2015
f1_keywords:
- ::_CSharpKeyword
helpviewer_keywords:
- ':: operator [C#]'
- 'namespaces [C#], :: operator'
- namespace alias qualifier operator (::) [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
ms.openlocfilehash: 077d5835b372897cbe797385271effc5d00bf6e3
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/04/2018
ms.locfileid: "43525656"
---
# <a name="-operator-c-reference"></a>Operatore :: (Riferimenti per C#)
Il qualificatore di alias dello spazio dei nomi (`::`) viene usato per cercare gli identificatori. Viene sempre posizionato tra due identificatori, come nell'esempio seguente:  
  
 [!code-csharp[csRefOperators#27](../../../csharp/language-reference/operators/codesnippet/CSharp/namespace-alias-qualifer_1.cs)]  

L'operatore `::` può anche essere usato con una *direttiva using alias*:

```csharp
// using Col=System.Collections.Generic;
var numbers = new Col::List<int> { 1, 2, 3 };
```

## <a name="remarks"></a>Note  
 Il qualificatore di alias dello spazio dei nomi può essere `global`. In questo modo viene richiamata una ricerca nello spazio dei nomi globale anziché in uno spazio dei nomi con alias.  
  
## <a name="for-more-information"></a>Ulteriori informazioni  
 Per un esempio di utilizzo dell'operatore `::`, vedere la seguente sezione:  
  
-   [Procedura: Usare l'alias dello spazio dei nomi globale](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## <a name="c-language-specification"></a>Specifiche del linguaggio C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Riferimenti per C#](../../../csharp/language-reference/index.md)  
- [Guida per programmatori C#](../../../csharp/programming-guide/index.md)  
- [Operatori C#](../../../csharp/language-reference/operators/index.md)  
- [Parole chiave per gli spazi dei nomi](../../../csharp/language-reference/keywords/namespace-keywords.md)  
- [. (operatore)](../../../csharp/language-reference/operators/member-access-operator.md)  
- [alias extern](../../../csharp/language-reference/keywords/extern-alias.md)
