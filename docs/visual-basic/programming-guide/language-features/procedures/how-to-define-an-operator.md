---
title: 'Procedura: definire un operatore (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- operator procedures [Visual Basic], about operator procedures
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: d4b0e253-092a-4e6e-9fe2-01f562140a29
ms.openlocfilehash: 1f5a020a710cecdfd8722a9fca0a8b329697eced
ms.sourcegitcommit: fc70fcb9c789b6a4aefcdace46f3643fd076450f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/06/2018
ms.locfileid: "34805399"
---
# <a name="how-to-define-an-operator-visual-basic"></a>Procedura: definire un operatore (Visual Basic)
Se è stato definito una classe o struttura, è possibile definire il comportamento di un operatore (ad esempio `*`, `<>`, o `And`) quando uno o entrambi gli operandi sono del tipo di classe o struttura.  
  
 Definire l'operatore standard come una routine di operatore all'interno della classe o struttura. Tutte le routine di operatore devono essere `Public` `Shared`.  
  
 La definizione di un operatore in una classe o struttura viene definita anche *overload* l'operatore.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente definisce il `+` chiamato operatore per una struttura `height`. La struttura utilizza altezze misurate in metri e centimetri. Un *pollici* è 2,54 centimetri e uno *piede* 12 pollici. Per garantire valori normalizzati (pollici < 12.0), il costruttore esegue *modulo* aritmetico 12. Il `+` operatore viene utilizzato il costruttore per generare valori normalizzati.  
  
 [!code-vb[VbVbcnProcedures#25](./codesnippet/VisualBasic/how-to-define-an-operator_1.vb)]  
  
 È possibile testare la struttura `height` con il codice seguente.  
  
 [!code-vb[VbVbcnProcedures#26](./codesnippet/VisualBasic/how-to-define-an-operator_2.vb)]  
  
 Per altre informazioni ed esempi, vedere [Overload di operatori in Visual Basic 2005](https://msdn.microsoft.com/library/ms379613(v=vs.80).aspx).  
  
## <a name="see-also"></a>Vedere anche  
 [Routine di operatore](./operator-procedures.md)  
 [Procedura: Definire un operatore di conversione](./how-to-define-a-conversion-operator.md)  
 [Procedura: Chiamare una routine di operatore](./how-to-call-an-operator-procedure.md)  
 [Procedura: Usare una classe che definisce gli operatori](./how-to-use-a-class-that-defines-operators.md)  
 [Istruzione Operator](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Istruzione Structure](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Procedura: Dichiarare una struttura](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [Operatore Mod](../../../../visual-basic/language-reference/operators/mod-operator.md)
