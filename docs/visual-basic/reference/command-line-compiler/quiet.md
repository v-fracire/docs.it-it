---
title: -quiet
ms.date: 07/20/2015
f1_keywords:
- -quiet
- quiet
helpviewer_keywords:
- -quiet compiler option [Visual Basic]
- /quiet compiler option [Visual Basic]
- quiet compiler option [Visual Basic]
ms.assetid: 5d77fa23-4c50-4708-8535-649912b098e8
ms.openlocfilehash: e67fe05507c8cb3edd7f46cad19211ba11e3b054
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652396"
---
# <a name="-quiet"></a>-quiet
Impedisce al compilatore di visualizzare codice per avvisi ed errori relativi alla sintassi.  
  
## <a name="syntax"></a>Sintassi  
  
```  
-quiet  
```  
  
## <a name="remarks"></a>Note  
 Per impostazione predefinita, l'opzione `-quiet` non è attiva. Quando il compilatore segnala un errore di sintassi o di un avviso, viene visualizzata anche la riga del codice sorgente. Per le applicazioni che analizzano l'output del compilatore, potrebbe essere più utile per il compilatore di generare solo il testo della diagnostica.  
  
 Nell'esempio seguente, `Module1` genera un errore che include il codice sorgente quando viene compilato senza `-quiet`.  
  
```vb  
Module Module1  
    Sub Main()  
        x()  
    End Sub  
End Module  
```  
  
 Output:  
 
```console
C:\projects\vb2.vb(3) : error BC30451: 'x' is not declared. It may be inaccessible due to its protection level.

        x()
        ~
``` 
 Compilato con `-quiet`, il compilatore restituisce solo le operazioni seguenti:  
  
 `E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.`  
  
> [!NOTE]
>  Il `-quiet` opzione non è disponibile all'interno dell'ambiente di sviluppo di Visual Studio; è disponibile solo durante la compilazione dalla riga di comando.  
  
## <a name="example"></a>Esempio  
 Il codice seguente Compila `T2.vb` non visualizzare il codice per la diagnostica del compilatore relativi alla sintassi:  
  
```  
vbc -quiet t2.vb  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Compilatore della riga di comando di Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Esempi di righe di comando di compilazione](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
