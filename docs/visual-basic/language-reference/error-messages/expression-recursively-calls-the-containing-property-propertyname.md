---
title: Espressione in modo ricorsivo chiama la proprietà che contiene &#39; &lt;propertyname&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc42026
- BC42026
helpviewer_keywords:
- BC42026
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
ms.openlocfilehash: f14e2645772b22a8f6ff2385dcd316a42d1d5cf0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588843"
---
# <a name="expression-recursively-calls-the-containing-property-39ltpropertynamegt39"></a>Espressione in modo ricorsivo chiama la proprietà che contiene &#39; &lt;propertyname&gt;&#39;
Un'istruzione all'interno di `Set` routine di una definizione di proprietà memorizza un valore nel nome della proprietà.  
  
 L'approccio consigliato per contenere il valore di una proprietà consiste nel definire un `Private` variabile nel contenitore della proprietà e utilizzarlo in entrambe le `Get` e `Set` procedure. Il `Set` routine deve archiviare, quindi il valore in ingresso in questa `Private` variabile.  
  
 Il `Get` routine si comporta come un `Function` procedure, in modo è possibile assegnare un valore per il nome della proprietà e restituire il controllo in corrispondenza di `End Get` istruzione. L'approccio consigliato, tuttavia, consiste nell'includere il `Private` variabile come valore in un [istruzione Return](../../../visual-basic/language-reference/statements/return-statement.md).  
  
 Il `Set` routine si comporta come un `Sub` routine, che non restituisce un valore. Pertanto, il nome della routine o proprietà hanno alcun significato speciale all'interno di un `Set` ed è possibile archiviare un valore al suo interno.  
  
 Nell'esempio seguente viene illustrato l'approccio che può causare questo errore, aggiungendo l'approccio consigliato.  
  
```  
Public Class illustrateProperties  
' The code in the following property causes this error.  
    Public Property badProp() As Char  
        Get  
            Dim charValue As Char  
            ' Insert code to update charValue.  
            badProp = charValue  
        End Get  
        Set(ByVal Value As Char)  
            ' The following statement causes this error.  
            badProp = Value  
            ' The value stored in the local variable badProp  
            ' is not used by the Get procedure in this property.  
        End Set  
    End Property  
' The following code uses the recommended approach.  
    Private propValue As Char  
    Public Property goodProp() As Char  
        Get  
            ' Insert code to update propValue.  
            Return propValue  
        End Get  
        Set(ByVal Value As Char)  
            propValue = Value  
        End Set  
    End Property  
End Class  
```  
  
 Per impostazione predefinita, si tratta di un messaggio di avviso. Per ulteriori informazioni su come nascondere gli avvisi o considerarli come errori, vedere [configurazione degli avvisi in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID errore:** BC42026  
  
## <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Riscrivere la definizione di proprietà per utilizzare l'approccio consigliato, come illustrato nell'esempio precedente.  
  
## <a name="see-also"></a>Vedere anche  
 [Routine Property](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)  
 [Istruzione Property](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Istruzione Set](../../../visual-basic/language-reference/statements/set-statement.md)
