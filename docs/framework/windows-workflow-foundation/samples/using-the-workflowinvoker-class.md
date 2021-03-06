---
title: Utilizzo della classe WorkflowInvoker
ms.date: 03/30/2017
ms.assetid: 0a966164-3990-4e78-8aa2-c6797ebbee94
ms.openlocfilehash: d6525dbbd30aae95be4c4ee1de267736e557a541
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/05/2018
ms.locfileid: "43748707"
---
# <a name="using-the-workflowinvoker-class"></a>Utilizzo della classe WorkflowInvoker
In questo esempio viene illustrato come usare la classe <xref:System.Activities.WorkflowInvoker> per richiamare un'attività come se fosse un metodo.  
  
## <a name="sample-details"></a>Dettagli dell'esempio  
 L'uso della classe <xref:System.Activities.WorkflowInvoker> è il modo più semplice per eseguire un'attività. È progettata per eseguire direttamente un'attività come una chiamata al metodo. Questa API ad alte prestazioni, leggera e semplice da usare in scenari in cui l'esecuzione di un'attività non richiede l'infrastruttura di controllo fornita da altre varianti di hosting.  
  
 L'esempio Usa un'attività personalizzata che deriva da <xref:System.Activities.CodeActivity%601>< Int32\> denominate `Add` che aggiunge due <xref:System.Activities.InArgument%601>, `X` e `Y`e restituisce un `Result` <xref:System.Activities.OutArgument%601>. (<xref:System.Activities.CodeActivity%601>\<T > deriva da <xref:System.Activities.Activity%601>< T\>, che dispone di un <xref:System.Activities.OutArgument%601> \<T > denominato `Result`.) Oggetto `Dictionary` \<stringa, oggetto > viene usato per passare argomenti in un'attività richiamata tramite <xref:System.Activities.WorkflowInvoker>. La chiave del dizionario corrisponde al nome di un argomento nell'attività richiamata. Il valore associato a una particolare chiave viene associato all'argomento identificato dalla chiave.  
  
 Nell'esempio viene chiamato <xref:System.Activities.WorkflowInvoker.Invoke%2A> e viene passato un dizionario che contiene valori per `X` e `Y`. La classe <xref:System.Activities.WorkflowInvoker> associa questi valori agli argomenti dell'attività `Add`, esegue l'attività e restituisce il risultato.  
  
#### <a name="to-use-this-sample"></a>Per usare questo esempio  
  
1.  Tramite [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] aprire il file della soluzione Invoker.sln.  
  
2.  Per compilare la soluzione, premere CTRL+MAIUSC+B.  
  
3.  Per eseguire la soluzione, premere F5.  
  
> [!IMPORTANT]
>  È possibile che gli esempi siano già installati nel computer. Verificare la directory seguente (impostazione predefinita) prima di continuare.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se questa directory non esiste, andare al [Windows Communication Foundation (WCF) e gli esempi di Windows Workflow Foundation (WF) per .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) per scaricare tutti i Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] esempi. Questo esempio si trova nella directory seguente.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\WorkflowInvoker`