---
title: Riferimento all'assembly Friend &lt;riferimento&gt; non è valido
ms.date: 07/20/2015
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
ms.openlocfilehash: c47fae9c60dc04ee02b1ff015d3dde87b8920c02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="friend-assembly-reference-ltreferencegt-is-invalid"></a>Riferimento all'assembly Friend &lt;riferimento&gt; non è valido
Riferimento all'assembly Friend \<riferimento > non è valido. Gli assembly firmati con nome sicuro devono specificare una chiave pubblica nelle relative dichiarazioni InternalsVisibleTo.  
  
 Il nome dell'assembly passato per il <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> costruttore di attributo identifica un assembly con nome sicuro, ma non include un `PublicKey` attributo.  
  
 **ID errore:** BC31535  
  
## <a name="to-correct-this-error"></a>Per correggere l'errore  
  
1.  Determinare la chiave pubblica dell'assembly friend con nome sicuro. Includere la chiave pubblica come parte del nome dell'assembly passato al <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> costruttore di attributo tramite il `PublicKey` attributo.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Reflection.AssemblyName>  
 [Assembly Friend](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 

