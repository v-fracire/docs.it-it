---
title: -win32icon
ms.date: 03/13/2018
helpviewer_keywords:
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 045e621f0104c4c958d77d2443c1524b33410b7a
ms.sourcegitcommit: f6343b070f3c66877338a05c8bfb0be9985255e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/24/2018
ms.locfileid: "39221023"
---
# <a name="-win32icon"></a>-win32icon
Inserisce un file con estensione ICO nel file di output. Il file ICO rappresenta il file di output in **Esplora File**.  
  
## <a name="syntax"></a>Sintassi  
  
```  
-win32icon:filename  
```  
  
## <a name="arguments"></a>Argomenti  
  
|Termine|Definizione|  
|---|---|  
|`filename`|Il file con estensione ico da aggiungere al file di output. Racchiudere il nome file racchiuso tra virgolette ("") se contiene uno spazio.|  
  
## <a name="remarks"></a>Note  
 È possibile creare un file con estensione ico con il compilatore di risorse (RC) di Microsoft Windows. Il compilatore di risorse viene richiamato quando si compila un programma in Visual C++. il file RC viene creato un file con estensione ico. Il `-win32icon` e `-win32resource` opzioni si escludono a vicenda.  
  
 Visualizzare [- linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) per fare riferimento a un [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] file di risorse, o [-risorse (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) collegare un [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] file di risorse. Visualizzare [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) per importare un file con estensione res.  
  
|Per impostare - win32icon nell'IDE di Visual Studio|  
|---|  
|1.  Selezionare un progetto in **Esplora soluzioni**. Scegliere **Proprietà** dal menu **Progetto**. <br />2.  Fare clic sulla scheda **Applicazione** .<br />3.  Modificare il valore di **icona** casella.|  
  
## <a name="example"></a>Esempio  
 Il codice seguente Compila `In.vb` e associa un file con estensione ico, `Rf.ico`.  
  
```console
vbc -win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Compilatore della riga di comando di Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Esempi di righe di comando di compilazione](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
