---
title: internal (Riferimenti per C#)
ms.date: 07/20/2015
f1_keywords:
- internal_CSharpKeyword
- internal
helpviewer_keywords:
- internal keyword [C#]
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
ms.openlocfilehash: 54ec003683953b53dedf8885a41350daf5338f83
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/04/2018
ms.locfileid: "43523361"
---
# <a name="internal-c-reference"></a>internal (Riferimenti per C#)
La parola chiave `internal` è un [modificatore di accesso](../../../csharp/language-reference/keywords/access-modifiers.md) per tipi e membri dei tipi. 
  
 > Questa pagina illustra l'accesso `internal`. La parola chiave `internal` fa anche parte del modificatore di accesso [`protected internal`](./protected-internal.md).
  
I tipi o membri interni sono accessibili solo all'interno di file nello stesso assembly, come nell'esempio seguente:  
  
```csharp  
public class BaseClass   
{  
    // Only accessible within the same assembly  
    internal static int x = 0;  
}  
```  

 Per un confronto di `internal` con altri modificatori di accesso, vedere [Livelli di accessibilità](../../../csharp/language-reference/keywords/accessibility-levels.md) e [Modificatori di accesso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Per altre informazioni sugli assembly, vedere [Assembly e Global Assembly Cache](../../../csharp/programming-guide/concepts/assemblies-gac/index.md).  
  
 Un uso comune dell'accesso interno è in fase di sviluppo basato su componenti poiché consente a un gruppo di componenti di collaborare in modo privato senza essere esposti al resto del codice dell'applicazione. Ad esempio, un framework per la creazione di interfacce utente grafiche potrebbe indicare le classi `Control` e `Form` che interagiscono usando membri con accesso interno. Poiché questi membri sono interni, non sono esposti al codice che usa il framework.  
  
 Non è corretto fare riferimento a un tipo o a un membro con accesso interno all'esterno dell'assembly in cui è stato definito.  
  
## <a name="example"></a>Esempio  
 Questo esempio contiene due file, `Assembly1.cs` e `Assembly1_a.cs`. Il primo file contiene una classe di base interna, `BaseClass`. Nel secondo file, un tentativo di creare un'istanza di `BaseClass` genererà un errore.  
  
```csharp  
// Assembly1.cs  
// Compile with: /target:library  
internal class BaseClass   
{  
   public static int intM = 0;  
}  
```  
  
```csharp  
// Assembly1_a.cs  
// Compile with: /reference:Assembly1.dll  
class TestAccess   
{  
   static void Main()   
   {  
      BaseClass myBase = new BaseClass();   // CS0122  
   }  
}  
```  
  
## <a name="example"></a>Esempio  
 In questo esempio, usare gli stessi file dell'esempio 1 e modificare il livello di accessibilità di `BaseClass` in `public`. Modificare anche il livello di accessibilità del membro `IntM` in `internal`. In questo caso, è possibile creare un'istanza della classe, ma non è possibile accedere al membro interno.  
  
```csharp  
// Assembly2.cs  
// Compile with: /target:library  
public class BaseClass   
{  
   internal static int intM = 0;  
}  
```  
  
```csharp  
// Assembly2_a.cs  
// Compile with: /reference:Assembly2.dll  
public class TestAccess   
{  
   static void Main()   
   {  
      BaseClass myBase = new BaseClass();   // Ok.  
      BaseClass.intM = 444;    // CS0117  
   }  
}  
```  
  
## <a name="c-language-specification"></a>Specifiche del linguaggio C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Riferimenti per C#](../../../csharp/language-reference/index.md)  
- [Guida per programmatori C#](../../../csharp/programming-guide/index.md)  
- [Parole chiave di C#](../../../csharp/language-reference/keywords/index.md)  
- [Modificatori di accesso](../../../csharp/language-reference/keywords/access-modifiers.md)  
- [Livelli di accessibilità](../../../csharp/language-reference/keywords/accessibility-levels.md)  
- [Modificatori](../../../csharp/language-reference/keywords/modifiers.md)  
- [public](../../../csharp/language-reference/keywords/public.md)  
- [private](../../../csharp/language-reference/keywords/private.md)  
- [protected](../../../csharp/language-reference/keywords/protected.md)
