---
title: 'Procedura: definire un parametro per una routine (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure parameters [Visual Basic], defining data types for
- procedures [Visual Basic], parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters [Visual Basic], defining
ms.assetid: 7962808d-407e-4e84-984e-43e9857c53c9
ms.openlocfilehash: b058f593b8672da449dac250947563c75c8386bf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651113"
---
# <a name="how-to-define-a-parameter-for-a-procedure-visual-basic"></a>Procedura: definire un parametro per una routine (Visual Basic)
Oggetto *parametro* consente di passare un valore per la procedura quando esegue la chiamata al codice chiamante. Dichiarare ogni parametro per una procedura esattamente come si dichiara una variabile, che specifica il nome e tipo di dati. Specificare inoltre il meccanismo di passaggio e se il parametro è facoltativo.  
  
 Per ulteriori informazioni, vedere [parametri di stored Procedure e argomenti](./procedure-parameters-and-arguments.md).  
  
### <a name="to-define-a-procedure-parameter"></a>Per definire un parametro di routine  
  
1.  Nella dichiarazione di routine, aggiungere il nome del parametro all'elenco di parametri della stored procedure, separandolo dalle altri parametri da virgole.  
  
2.  Decidere il tipo di dati del parametro.  
  
3.  Seguire il nome del parametro con un `As` clausola per specificare il tipo di dati.  
  
4.  Decidere il meccanismo di passaggio desiderato per il parametro. In genere si passa un parametro per valore, a meno che non si desidera essere in grado di modificare il valore nel codice chiamante alla routine.  
  
5.  Anteporre al nome di parametro [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) o [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) per specificare il meccanismo di passaggio. Per ulteriori informazioni, vedere [le differenze tra il passaggio di un argomento per valore e per riferimento](./differences-between-passing-an-argument-by-value-and-by-reference.md).  
  
6.  Se il parametro è facoltativo, anteporre il meccanismo di passaggio [facoltativo](../../../../visual-basic/language-reference/modifiers/optional.md) e seguire il tipo di dati del parametro con un segno di uguale (`=`) e un valore predefinito.  
  
     Nell'esempio seguente viene definita la struttura di un `Sub` routine con tre parametri. Le prime due sono necessari e il terzo è facoltativo. Nell'elenco di parametri, le dichiarazioni dei parametri sono separati da virgole.  
  
     [!code-vb[VbVbcnProcedures#33](./codesnippet/VisualBasic/how-to-define-a-parameter-for-a-procedure_1.vb)]  
  
     Il primo parametro accetta un `customer` oggetto, e `updateCustomer` può aggiornare direttamente la variabile passata a `c` perché l'argomento è passato [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md). La procedura non è possibile modificare i valori degli ultimi due argomenti in quanto vengono passati [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).  
  
     Se il codice chiamante non fornisce un valore per il `level` parametro, Visual Basic lo imposta sul valore predefinito pari a 0.  
  
     Se il controllo dei tipi passa ([istruzione Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) è `Off`, `As` clausola è facoltativa quando si definisce un parametro. Tuttavia, se un qualsiasi parametro utilizza un `As` clausola, tutti gli elementi deve essere utilizzata. Se il tipo di opzione di controllo è `On`, `As` clausola è obbligatoria per ogni definizione di parametro.  
  
     Specifica di tipi di dati per tutti gli elementi di programmazione è noto come *tipizzazione forte*. Quando si imposta `Option Strict On`, Visual Basic applica la tipizzazione forte. Ciò è particolarmente consigliata per i motivi seguenti:  
  
    -   Consente il supporto IntelliSense per le variabili e parametri. In questo modo è possibile visualizzare le relative proprietà e gli altri membri durante la digitazione nel codice.  
  
    -   Consente al compilatore di eseguire il controllo dei tipi. Ciò consente di intercettare istruzioni possono avere esito negativo in fase di esecuzione a causa di errori, ad esempio l'overflow. Vengono inoltre rilevate le chiamate ai metodi su oggetti che non li supportano.  
  
    -   Comporta tempi di esecuzione del codice. Un motivo è che se non si specifica un tipo di dati per un elemento di programmazione, il compilatore Visual Basic assegna il `Object` tipo. Il codice compilato potrebbe essere necessario convertire avanti e indietro tra `Object` e altri tipi di dati, riducendo le prestazioni.  
  
## <a name="see-also"></a>Vedere anche

 [Routine](./index.md)  
 [Routine Sub](./sub-procedures.md)  
 [Routine Function](./function-procedures.md)  
 [Procedura: Passare argomenti a una routine](./how-to-pass-arguments-to-a-procedure.md)  
 [Passaggio di argomenti per valore e per riferimento](./passing-arguments-by-value-and-by-reference.md)  
 [Routine ricorsive](./recursive-procedures.md)  
 [Overload della routine](./procedure-overloading.md)  
 [Oggetti e classi](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [Programmazione orientata a oggetti (Visual Basic)](../../concepts/object-oriented-programming.md)  
