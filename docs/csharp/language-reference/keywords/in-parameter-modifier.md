---
title: Modificatore del parametro in (Riferimenti per C#)
ms.date: 03/06/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- parameters [C#], in
- in parameters [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 035aac3e6b902f607e533b709713eb1d07c9774a
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2018
---
# <a name="in-parameter-modifier-c-reference"></a>Modificatore del parametro in (Riferimenti per C#)

La parola chiave `in` fa sì che gli argomenti vengono passati per riferimento. È simile alle parole chiave [ref](ref.md) o [out](out-parameter-modifier.md), tranne per il fatto che gli argomenti `in` non possono essere modificati dal metodo chiamato, mentre possono essere modificati gli argomenti `ref`; gli argomenti `out` devono essere modificati dal chiamante e tali modifiche possono essere osservate nel contesto di chiamata.

[!code-csharp-interactive[cs-in-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/InParameterModifier.cs#1)]  

L'esempio precedente dimostra che il modificatore `in` non è necessario nel sito di chiamata. Viene richiesto soltanto nella dichiarazione di metodo.

> [!NOTE] 
> La parola chiave `in` può essere usata anche con un parametro di tipo generico per specificare che il parametro è di tipo controvariante, quale parte di un'istruzione `foreach` o parte di una clausola `join` in una query LINQ. Per altre informazioni sull'uso della parola chiave `in` in questi contesti, vedere [in](in.md), che fornisce collegamenti a tutti gli utilizzi.
  
 Le variabili passate come argomenti `in` devono essere inizializzate prima di essere passate in una chiamata al metodo. Tuttavia, il metodo chiamato non può assegnare un valore o modificare l'argomento.  
  
 Nonostante le parole chiave `in`, `ref` e `out` determinino un comportamento differente in fase di esecuzione, non sono considerate parte della firma del metodo in fase di compilazione. Non è quindi possibile eseguirne l'overload se l'unica differenza è che un metodo accetta un argomento `ref` o `in` e l'altro un argomento `out`. Il codice seguente, ad esempio, non verrà compilato:  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on in, ref and out".
    public void SampleMethod(in int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
L'overload in base alla presenza di `in` è consentito, ma genera un avviso del compilatore:  
  
```csharp
class InOverloads
{
    // Discouraged. Calling SampleMethod(value) is ambiguous.
    public void SampleMethod(in int i) { }
    public void SampleMethod(int i) { }
}
```

Le proprietà o costanti possono essere passate come parametri `in`, perché il metodo di chiamata non può modificare i relativi valori.
  
Non è possibile usare le parole chiave `in`, `ref` e `out` per i seguenti tipi di metodi:  
  
- Metodi asincroni definiti usando il modificatore [async](../../../csharp/language-reference/keywords/async.md).  
  
- Metodi iteratori che includono un'istruzione [yield return](../../../csharp/language-reference/keywords/yield.md) o `yield break`.  

In genere si dichiarano argomenti `in` per evitare le operazioni di copia necessarie per il passaggio di argomenti per valore. Ciò è particolarmente utile quando gli argomenti sono strutture o matrici di strutture.

## <a name="c-language-specification"></a>Specifiche del linguaggio C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti per C#](../../../csharp/language-reference/index.md)  
 [Guida per programmatori C#](../../../csharp/programming-guide/index.md)  
 [Parole chiave di C#](../../../csharp/language-reference/keywords/index.md)  
 [Parametri dei metodi](../../../csharp/language-reference/keywords/method-parameters.md)